# /discover - Search and Inventory

## Purpose

Run targeted keyword searches against a shared Google Drive to find process documentation. Build a deduplicated raw inventory for classification.

## Prerequisites

- Google Workspace MCP server is connected and authenticated
- User provides the shared drive ID or name

## Process

1. **Get the drive scope**
   - Ask the user for the shared drive ID or name
   - Confirm the drive with the user before proceeding
   - Ask for the organization name and key product terms to build search queries (e.g., "ACM", "RHACM", "stolostron")

2. **Build the search query list**
   - Organize queries into 4 tiers (see below)
   - If taxonomy files are available locally, load component names for Tier 3 queries
   - Otherwise, ask the user for key component/team names

3. **Execute searches tier by tier**

   **Tier 1 — Direct process terms** (6 queries, highest signal):
   - `"[org] SOP"`
   - `"[org] runbook"`
   - `"[org] process" document`
   - `"[org] procedure"`
   - `"[product] SOP"`
   - `"[product] process"`

   **Tier 2 — Document type + product terms** (7 queries):
   - `"[org]" "how-to"`
   - `"[org]" onboarding guide`
   - `"[org]" "getting started"`
   - `[upstream-project] SOP OR runbook OR process`
   - `"[org]" DDR OR "design decision"`
   - `"[org]" "architecture review"`
   - `"[org]" playbook`

   **Tier 3 — Component-specific** (1 query per major component):
   - `"[component-name]" process OR SOP OR runbook OR guide`
   - Scope with org name to reduce noise
   - Skip components that are unlikely to have standalone docs

   **Tier 4 — Broad sweeps** (3 queries):
   - `"[org]" template`
   - `"[org]" guide`
   - `"[org]" checklist`

4. **For each search pass**
   - Execute the search via Google Workspace MCP
   - For each result, capture: file ID, title, MIME type, last modified date, owner, parent folder path
   - Check file ID against the dedup set (`seenFileIds` in search-state.json)
   - New files: add to discovery log and dedup set
   - Already-seen files: record the additional keyword match but don't duplicate
   - Report progress: "Pass 3/25: '[org] runbook' — 12 results, 8 new. Cumulative: 67 unique docs."

5. **Tier checkpoints**
   - After each tier completes, summarize: total unique docs found, docs per tier, signal quality
   - Ask user: "Continue to Tier N?" or "Add custom queries?" or "Done discovering?"

6. **Save state**
   - Write discovery log to `artifacts/drive-catalog/discovery-log.md`
   - Write machine-readable state to `artifacts/drive-catalog/search-state.json`

## Output

- `artifacts/drive-catalog/discovery-log.md` — Raw search results with metadata
- `artifacts/drive-catalog/search-state.json` — Checkpoint for pause/resume

## Success Criteria

- [ ] All tier 1 and 2 queries executed
- [ ] Results deduplicated by file ID
- [ ] Discovery log written with full metadata
- [ ] Search state saved for resume capability
- [ ] User informed of cumulative totals and signal quality

## Next Steps

Run `/classify` to review discovered docs in batches and assign component, type, and relevance.
