# /report - Gap Analysis and Recommendations

## Purpose

Cross-reference the catalog against the taxonomy's existing SOPs, stale SOPs, and gaps. Produce actionable recommendations for documentation migration, SOP updates, and process improvements.

## Prerequisites

- `/catalog` has been run and `catalog.md` exists

## Process

1. **Load data**
   - Read `artifacts/drive-catalog/catalog.md`
   - Load taxonomy data (component registry + SOP mapping) if not already in context

2. **Analyze gaps resolved**
   - For each known SOP gap, check if any Drive doc fills it
   - Assess quality: is the Drive doc complete enough to serve as the SOP, or does it need work?
   - Recommend action: migrate as-is, migrate with updates, use as starting point for new SOP

3. **Analyze gaps still open**
   - List gaps with no Drive docs found
   - For each, note the component owner and recommend next steps

4. **Analyze stale SOP replacements**
   - For each stale SOP, check if any Drive doc provides an updated version
   - Recommend action: replace stale SOP, merge content, or flag for manual review

5. **Identify new process docs**
   - Drive docs classified as process-relevant but not matching any existing SOP or gap
   - Recommend: add to process index, migrate to Confluence, or archive

6. **Generate component coverage summary**
   - For each component: doc count, gap coverage percentage, staleness distribution
   - Highlight components with no documentation and components with all-stale docs
   - Suggest priority order for documentation migration

7. **Write recommendations**
   - Prioritized action list:
     1. Migrate docs that fill known gaps (highest priority)
     2. Migrate current SOPs/runbooks not yet indexed
     3. Update stale SOPs with Drive replacements
     4. Archive stale docs with no replacement
     5. Assign owners to unclassifiable docs
   - Include effort estimates where possible (small/medium/large)

8. **Write the report**
   - Write to `artifacts/drive-catalog/gap-report.md`
   - Present executive summary to the user

## Output

- `artifacts/drive-catalog/gap-report.md` — Gap analysis with prioritized recommendations

## Success Criteria

- [ ] All known gaps assessed against Drive findings
- [ ] All stale SOPs assessed for replacements
- [ ] New process docs identified and triaged
- [ ] Component coverage summary complete
- [ ] Prioritized recommendations written
- [ ] Report artifact written

## Next Steps

Use the gap report to drive documentation migration work (e.g., Confluence migration, SOP creation tasks in Jira).
