# /execute - Execute Approved Changes

## Purpose

Present each group of proposed file actions to the user for approval, then execute approved moves, renames, and archives via the Google Workspace MCP.

## Prerequisites

- `/categorize` has been run and `artifacts/drive-cleanup/categorization-plan.md` exists
- Google Workspace MCP server is connected and authenticated

## Process

1. **Load the categorization plan**
   - Read `artifacts/drive-cleanup/categorization-plan.md`
   - If an execution log already exists, read it to determine which groups have already been processed (supports pause/resume)

2. **Present each group for approval**
   - Show the group name (target top-level folder)
   - Display the action table for that group
   - Show the count: "Group 1 of N: 00_Strategy (23 items)"
   - Ask for one of these responses:
     - **"Approve all for [folder]"** — Execute all moves in this group
     - **"Approve all except [file1, file2]"** — Execute with exceptions; ask for alternative instructions on exceptions
     - **"Reject all for [folder]"** — Ask for alternative instructions for the entire group
     - **"Skip this group"** — Move to the next group, revisit later

3. **Prepare destination folders**
   - Before executing moves, check whether each destination folder exists
   - Create missing folders via MCP if possible
   - If folder creation fails, tell the user which folders need manual creation and wait

4. **Execute approved actions**
   - Process each approved action via MCP (move, rename, or archive)
   - For each action, log:
     - Timestamp
     - File name and ID
     - Action taken
     - Original location (full path)
     - New location (full path)
     - Status: Success or Error (with error message)
   - If an action fails, log the error and continue with remaining items
   - Show progress: "Moved 12/23 items in this group..."

5. **Handle delete requests**
   - If any action is a delete, present a separate confirmation with a clear warning
   - Show: "WARNING: The following N files will be permanently deleted. This cannot be undone."
   - Require explicit "Yes, delete" confirmation
   - Suggest archiving as an alternative

6. **Update the execution log**
   - Append completed group results to `artifacts/drive-cleanup/execution-log.md`
   - Include running totals: items processed, items remaining, items skipped, errors
   - The log contains enough detail to manually reverse any action

7. **Continue or finish**
   - After each group, ask if the user wants to continue to the next group or pause
   - If all groups are processed, summarize results and recommend `/verify`

## Output

- `artifacts/drive-cleanup/execution-log.md` — Timestamped log of all executed actions with original/new locations and file IDs

## Success Criteria

- [ ] Each group is presented for explicit approval before execution
- [ ] No files moved, renamed, or deleted without user approval
- [ ] Missing destination folders are created or flagged
- [ ] Failed actions are logged and don't stop the batch
- [ ] Execution log has enough detail to reverse any action
- [ ] Progress counts are shown during processing

## Notes

- If the user pauses mid-workflow, the execution log tracks what's been done. Running `/execute` again picks up where it left off.
- Delete operations require a separate, explicit confirmation with a warning.

## Next Steps

Run `/verify` to confirm the final folder state matches the plan.
