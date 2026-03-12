# /categorize - Map Files to Target Structure

## Purpose

Create a detailed plan mapping every inventoried file and folder to its destination in the target structure, grouped by target folder for batch approval.

## Prerequisites

- `/scan` has been run and `artifacts/drive-cleanup/inventory.md` exists
- `/structure` has been run and `artifacts/drive-cleanup/target-structure.md` exists
- User has approved the target folder structure

## Process

1. **Load inventory and target structure**
   - Read `artifacts/drive-cleanup/inventory.md`
   - Read `artifacts/drive-cleanup/target-structure.md`
   - Note the agreed naming convention, archive strategy, and duplicate handling rules

2. **Categorize each item**
   - For every file and folder in the inventory, determine:
     - **Action**: Move, Rename & Move, Archive, or Delete
     - **Destination**: Full target path
     - **Reasoning**: Brief explanation of why this categorization was chosen
   - Apply the agreed duplicate handling strategy
   - Apply the agreed archive strategy for stale files
   - Flag items that don't fit any category

3. **Group by target folder**
   - Organize all proposed actions by their target top-level folder
   - Example: all moves into `00_Strategy/` grouped together, then `01_Planning/`, etc.
   - Keep groups to 20-30 items for manageable review
   - If a group exceeds 30 items, split into sub-batches

4. **Handle edge cases**
   - **Uncategorized Items**: Files that don't clearly belong anywhere — list separately and ask for guidance
   - **Folders for Deeper Review**: Existing subfolders whose contents may need individual triage rather than bulk moves
   - **Conflicts**: Files with the same name targeting the same destination — flag and propose resolution

5. **Write the categorization plan**
   - For each group, produce a table with columns: Original Name, File ID, Action, Target Path, Reasoning
   - Include summary counts per group
   - Include the Uncategorized and Deeper Review sections
   - Write to `artifacts/drive-cleanup/categorization-plan.md`

6. **Present for review**
   - Show the user a summary: X files to move, Y to archive, Z to rename, W uncategorized
   - Recommend running `/execute` to begin batch approvals

## Output

- `artifacts/drive-cleanup/categorization-plan.md` — Complete file-to-folder mapping with proposed actions

## Success Criteria

- [ ] Every inventoried item has a proposed action or is listed as uncategorized
- [ ] Actions are grouped by target folder in batches of 20-30
- [ ] Each action includes file ID, target path, and reasoning
- [ ] Uncategorized items and folders needing deeper review are called out
- [ ] Categorization plan artifact is written

## Notes

- This plan serves as a checkpoint. If the user pauses the workflow, they can resume from this artifact.
- No files are moved during this phase. This is planning only.

## Next Steps

Run `/execute` to begin presenting groups for approval and executing approved changes.
