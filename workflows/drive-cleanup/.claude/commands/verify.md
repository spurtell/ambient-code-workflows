# /verify - Verify and Report

## Purpose

Re-scan the Drive folder to confirm the new structure matches the plan, identify any missed or failed items, and produce a final summary report.

## Prerequisites

- `/execute` has been run and `artifacts/drive-cleanup/execution-log.md` exists
- At least one group of changes has been executed

## Process

1. **Re-scan the folder**
   - Use the Google Workspace MCP to list all files and folders in the target Drive folder recursively
   - Build a current-state inventory

2. **Compare against the plan**
   - Read `artifacts/drive-cleanup/target-structure.md` for the intended structure
   - Read `artifacts/drive-cleanup/categorization-plan.md` for the intended file locations
   - Read `artifacts/drive-cleanup/execution-log.md` for what was actually done
   - Identify discrepancies:
     - Files that were planned to move but didn't
     - Files that ended up in unexpected locations
     - Destination folders that are empty (planned items didn't arrive)
     - Files still in the root or original locations

3. **Produce before/after comparison**
   - Show the original folder structure (from inventory) alongside the new structure
   - Summary stats: files moved, files archived, files renamed, files skipped, errors

4. **List remaining items**
   - Files that were skipped or deferred
   - Uncategorized items that still need decisions
   - Failed moves that need manual attention
   - Any new files that appeared during the cleanup process

5. **Write the final report**
   - Executive summary: what was accomplished
   - Before/after tree diagrams
   - Statistics table
   - Remaining action items
   - Write to `artifacts/drive-cleanup/final-report.md`

6. **Present to user**
   - Show the summary
   - If there are remaining items, ask if the user wants to run another `/categorize` + `/execute` cycle for them
   - If everything is clean, congratulate the user

## Output

- `artifacts/drive-cleanup/final-report.md` — Before/after comparison and remaining action items

## Success Criteria

- [ ] Current folder state has been re-scanned
- [ ] Discrepancies between plan and reality are identified
- [ ] Before/after comparison is clear and accurate
- [ ] Remaining action items are listed
- [ ] Final report artifact is written

## Notes

- This phase is read-only. No files are moved or modified.
- If significant discrepancies are found, the user can re-run `/categorize` and `/execute` for the remaining items.
