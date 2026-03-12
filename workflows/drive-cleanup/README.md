# Clean Up Google Drive

Systematically organize a messy Google Drive folder through interactive inventory, structure planning, and batch-approved file operations. The workflow uses Google Workspace MCP to interact with Drive while keeping the user in full control of every change.

## How It Works

The workflow follows 5 phases. Nothing moves without your explicit approval.

### 1. Scan (`/scan`)

Provide a Google Drive folder ID. The agent inventories all files and subfolders recursively, flagging duplicates, stale files (1+ year unmodified), inconsistent naming, deep nesting, and root clutter.

### 2. Structure (`/structure`)

The agent proposes a target folder organization using numbered prefixes (`00_Strategy/`, `01_Planning/`, etc.). You refine the structure and set preferences for naming conventions, archive strategy, and duplicate handling.

### 3. Categorize (`/categorize`)

Every file is mapped to its destination in the target structure. Proposed actions are grouped by target folder in batches of 20-30 items. Items that don't fit cleanly are flagged for manual guidance.

### 4. Execute (`/execute`)

Each batch is presented for approval. You can approve all, approve with exceptions, reject, or skip each group. The agent creates missing folders, executes approved moves via MCP, and logs every action with enough detail to reverse it.

### 5. Verify (`/verify`)

The folder is re-scanned and compared against the plan. A final report shows before/after structure, statistics, and any remaining items that need attention.

## Prerequisites

- **Google Workspace MCP server** must be connected and authenticated in your ACP session
- A Google Drive folder ID (the string after `folders/` in the Drive URL)

## Artifacts

All outputs are written to `artifacts/drive-cleanup/`:

| File | Phase | Contents |
|------|-------|----------|
| `inventory.md` | Scan | Full file listing with flagged issues |
| `target-structure.md` | Structure | Agreed folder organization and rules |
| `categorization-plan.md` | Categorize | File-to-folder mapping with proposed actions |
| `execution-log.md` | Execute | Timestamped log of all executed actions |
| `final-report.md` | Verify | Before/after comparison and remaining items |

## Safety

- Files are never moved, renamed, or deleted without explicit approval
- Archiving is preferred over deletion
- Delete operations require a separate confirmation with a warning
- The execution log records original location and file ID for every action, enabling manual reversal
- The workflow supports pause/resume — the categorization plan and execution log serve as checkpoints

## Quick Start

```text
/scan
> Provide folder ID: 1ABCxyz...

/structure
> Review and approve the proposed organization

/categorize
> Review the file-to-folder mapping

/execute
> Approve batches: "Approve all for 00_Strategy"

/verify
> Confirm everything is in place
```
