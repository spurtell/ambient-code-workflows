# /scan - Inventory and Assess

## Purpose

Recursively inventory all files and subfolders in a Google Drive folder and identify organizational problems: duplicates, stale files, inconsistent naming, deep nesting, and misplaced items.

## Prerequisites

- Google Workspace MCP server is connected and authenticated
- User provides a Google Drive folder ID

## Process

1. **Get the folder ID**
   - Ask the user for the Google Drive folder ID if not already provided
   - The folder ID is the string after `folders/` in the Drive URL
   - Confirm the folder name with the user before proceeding

2. **List all contents recursively**
   - Use the Google Workspace MCP to list all files and subfolders
   - For each item, capture: name, type (file/folder), MIME type, size, last modified date, parent folder, file ID
   - Track folder depth (nesting level)

3. **Flag organizational problems**
   - **Duplicates**: Files with identical names (note: may be different versions)
   - **Stale files**: Not modified in over 1 year
   - **Deep nesting**: Files more than 3 levels deep
   - **Inconsistent naming**: Mixed conventions (camelCase, snake_case, spaces, etc.)
   - **Root clutter**: Files sitting in the root that likely belong in subfolders
   - **Empty folders**: Folders with no contents
   - **Large files**: Unusually large files that may need attention

4. **Generate the inventory report**
   - Summary statistics: total files, total folders, total size, date range
   - Problem breakdown with counts
   - Full file listing as a table (name, type, size, modified, depth, flags)
   - Write to `artifacts/drive-cleanup/inventory.md`

5. **Present findings**
   - Show the summary to the user
   - Highlight the most significant issues
   - Recommend running `/structure` next to define the target organization

## Output

- `artifacts/drive-cleanup/inventory.md` — Full inventory with flagged issues

## Success Criteria

- [ ] All files and folders in the target folder are inventoried
- [ ] Duplicates, stale files, and naming issues are flagged
- [ ] Summary statistics are accurate
- [ ] Inventory artifact is written

## Next Steps

Run `/structure` to propose or define the target folder organization.
