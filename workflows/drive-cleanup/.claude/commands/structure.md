# /structure - Propose Target Organization

## Purpose

Define the target folder structure that all files will be organized into. This can be agent-proposed based on the inventory, user-provided, or a collaborative refinement of both.

## Prerequisites

- `/scan` has been run and `artifacts/drive-cleanup/inventory.md` exists
- The user has reviewed the inventory findings

## Process

1. **Review the inventory**
   - Read `artifacts/drive-cleanup/inventory.md`
   - Identify natural groupings from existing folder names and file types
   - Note the domain/context (product management, engineering, personal, etc.)

2. **Propose a folder structure**
   - Use numbered prefixes for ordering: `00_`, `01_`, `02_`, etc.
   - Include an `_Archive/` folder for old/deprecated items
   - Include a `_Templates/` folder if template files were found
   - Present the structure as a tree diagram
   - Explain the reasoning behind each top-level folder

3. **Gather user preferences**
   - **Naming convention**: snake_case, kebab-case, Title_Case, or Spaces?
   - **Archive strategy**: Move old files to `_Archive/`, tag them, or leave in place?
   - **Duplicate handling**: Keep newest? Keep largest? Prompt per-duplicate? Move to `_Duplicates/`?
   - **Depth limit**: How many levels of nesting are acceptable?
   - **Special handling**: Any file types or patterns that need custom rules?

4. **Refine and confirm**
   - Incorporate user feedback into the structure
   - Present the final version for explicit approval
   - Do NOT proceed until the user confirms the structure

5. **Write the target structure**
   - Document the agreed structure with descriptions for each folder
   - Include the agreed naming convention, archive strategy, and duplicate handling rules
   - Write to `artifacts/drive-cleanup/target-structure.md`

## Output

- `artifacts/drive-cleanup/target-structure.md` — Agreed folder structure and organizational rules

## Success Criteria

- [ ] Target structure is based on actual inventory contents
- [ ] User has explicitly approved the structure
- [ ] Naming convention, archive strategy, and duplicate handling are documented
- [ ] Structure artifact is written

## Next Steps

Run `/categorize` to map every file from the inventory to the target structure.
