# /catalog - Compile Structured Inventory

## Purpose

Compile all classified documents into a structured markdown catalog grouped by component, ready for use in documentation migration and gap analysis.

## Prerequisites

- `/classify` has been run and `classification-plan.md` is complete (or substantially complete)

## Process

1. **Load classification data**
   - Read `artifacts/drive-catalog/classification-plan.md`
   - Count documents by status: classified, skipped, not relevant, unreadable

2. **Generate summary statistics**
   - Total docs discovered
   - Classified as process docs (by type)
   - Skipped / not relevant
   - Unclassifiable (need manual review)
   - Known gaps filled
   - Stale SOP overlaps found
   - New docs not in existing index

3. **Build per-component sections**
   - Group classified docs by component
   - For each component, create a table: Title, Type, Staleness, Link (Google Drive URL), Notes
   - Sort components alphabetically
   - List components with no Drive docs found

4. **Build by-document-type breakdown**
   - Table showing each doc type with count and staleness distribution (Current / Aging / Stale)

5. **Build cross-reference tables**
   - Known gaps: gap name, status (Filled / Still missing), Drive doc found, notes
   - Stale SOPs: SOP #, replacement found in Drive, notes

6. **Write the catalog**
   - Write to `artifacts/drive-catalog/catalog.md`
   - Present summary to the user

## Output

- `artifacts/drive-catalog/catalog.md` — Structured inventory grouped by component

## Success Criteria

- [ ] All classified documents included
- [ ] Grouped by component with correct taxonomy names
- [ ] Summary statistics accurate
- [ ] Gap and stale SOP cross-references complete
- [ ] Catalog artifact written

## Next Steps

Run `/report` to generate actionable recommendations from the catalog.
