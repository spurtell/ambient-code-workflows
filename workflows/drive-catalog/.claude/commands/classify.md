# /classify - Batch Classification

## Purpose

Present discovered documents in batches of 20-30 for human-approved classification against the organizational taxonomy.

## Prerequisites

- `/discover` has been run and `discovery-log.md` exists
- Taxonomy data is available (local files or user-provided)

## Process

1. **Load taxonomy data**
   - Search for taxonomy files locally (e.g., `**/acm-team-component-registry.md`, `**/sop-ownership-mapping.md`)
   - If found, read them to get: component list, triads, existing SOPs, stale SOPs, gaps
   - If not found, ask the user to paste or upload the taxonomy data
   - Confirm the component list with the user before proceeding

2. **Load discovery state**
   - Read `artifacts/drive-catalog/discovery-log.md` for the full document list
   - Read `artifacts/drive-catalog/classification-plan.md` if it exists (resume from last batch)
   - Identify unclassified documents

3. **For each batch (20-30 documents)**

   a. **Content peek**: For each document in the batch, use the Google Workspace MCP to read the first ~500 words of content. This provides the signal needed for classification.

   b. **Propose classification**: For each document, propose:
   - **Component**: Best match from the taxonomy. Use title, folder path, content peek, and owner as signals. If the doc references old/renamed components (e.g., "GRC" instead of "Governance"), map to the current name.
   - **Doc Type**: SOP, Runbook, DDR, Onboarding Guide, Reference, How-To, Process Guide, Template, Presentation, Meeting Notes, or Other.
   - **Relevance**: One of:
     - "Fills gap: [gap name]" — matches a known missing SOP
     - "Overlaps SOP #N" — covers the same ground as an existing SOP
     - "Overlaps stale SOP #N" — may be an updated version of a stale SOP
     - "New" — process doc not in the existing index
     - "Duplicate of [other doc]" — duplicate of another discovered doc
     - "Not relevant" — matched keywords but is not a process doc
   - **Staleness**: Current (<6 months), Aging (6-12 months), Stale (>12 months)
   - **Owner Match**: Yes/No — whether the doc owner matches the component's triad

   c. **Present the batch** as a table:
   ```
   | # | Title | Component | Type | Relevance | Staleness | Owner Match |
   ```

   d. **Ask for approval**:
   - "Approve all" — record all classifications as proposed
   - "Approve all except [N, M]" — user corrects specific rows
   - "Reject all" — re-examine the batch
   - "Skip batch" — defer to a later session

4. **Record approved classifications**
   - Append to `artifacts/drive-catalog/classification-plan.md`
   - Update progress count: "Classified 45/120 documents"

5. **Handle edge cases**
   - Documents that can't be read (permissions, format): flag as "Unreadable" with the error
   - Documents matching multiple components: pick the strongest match, note alternatives
   - Documents with no clear component: classify as "Cross-cutting" or "Unknown"

## Output

- `artifacts/drive-catalog/classification-plan.md` — All classified documents with batch history

## Success Criteria

- [ ] All discovered documents classified or explicitly skipped
- [ ] Every classification approved by the user
- [ ] Taxonomy data loaded and applied consistently
- [ ] Classification plan written with batch audit trail

## Next Steps

Run `/catalog` to compile all classified docs into a structured inventory.
