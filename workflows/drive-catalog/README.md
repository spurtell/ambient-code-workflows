# Drive Catalog

Search-first discovery and classification of process documentation scattered across a shared Google Drive.

## What It Does

Systematically searches a Google Drive using targeted keyword queries, presents discovered documents for human-approved classification against a team/component taxonomy, and produces a structured inventory with gap analysis.

This is a **read-only** workflow — nothing in Drive gets moved, renamed, or deleted.

## Prerequisites

- **Google Workspace MCP server** connected and authenticated
- Access to the target shared Google Drive
- (Optional) Local taxonomy files for classification:
  - Component registry (e.g., `acm-team-component-registry.md`)
  - SOP ownership mapping (e.g., `sop-ownership-mapping.md`)
  - If not available locally, you can paste or upload taxonomy data during the workflow

## Commands

| Command | Phase | Purpose |
|---------|-------|---------|
| `/discover` | 1 | Search Drive with tiered keyword queries, deduplicate results |
| `/classify` | 2 | Review docs in batches of 20-30, assign component/type/relevance |
| `/catalog` | 3 | Compile structured inventory grouped by component |
| `/report` | 4 | Cross-reference against SOPs/gaps, produce recommendations |

## Search Strategy

Searches are organized in 4 tiers, from most specific to broadest:

1. **Direct process terms** — `"[org] SOP"`, `"[org] runbook"`, etc.
2. **Doc type + product terms** — `"[org]" onboarding`, `DDR "[org]"`, etc.
3. **Component-specific** — one query per major component
4. **Broad sweeps** — `"[org]" template`, `"[org]" guide`

You can pause after any tier and resume later. Custom queries can be added at any time.

## Artifacts

All outputs are written to `artifacts/drive-catalog/`:

| Artifact | Description |
|----------|-------------|
| `discovery-log.md` | Raw search results with metadata |
| `search-state.json` | Machine-readable checkpoint for pause/resume |
| `classification-plan.md` | Human-reviewed classifications with batch history |
| `catalog.md` | Final structured inventory grouped by component |
| `gap-report.md` | Gap analysis with prioritized recommendations |

## Typical Workflow

```
/discover          → Search the drive, build raw inventory (~25 search passes)
/classify          → Review in batches, classify each doc (~7-10 batches)
/catalog           → Compile the final inventory
/report            → Generate gap analysis and action items
```

Expected scale: 200-400 raw results → 100-200 unique docs → 7-10 classification batches.
