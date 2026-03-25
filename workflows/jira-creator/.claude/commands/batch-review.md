---
description: Review all children of a JIRA issue for hygiene and completeness
displayName: batch-review
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty). The user should provide a parent issue key (e.g., "batch-review ACM-12345"). They may also specify filters (e.g., "batch-review ACM-12345 stories only").

## Purpose

Review all child issues of an Epic or Feature at once, producing a summary table of hygiene scores and a consolidated report of common issues. Much faster than running `/review` on each child individually.

## Process

1. **Fetch Parent Issue**: Use `getJiraIssue` MCP tool to retrieve the parent. If no key provided, ask the user.

2. **Fetch Children**: Use `searchJiraIssuesUsingJql` MCP tool to find all child issues:
   - For Epics: `parent = {EPIC-KEY} ORDER BY type, priority`
   - For Features: `parent = {FEATURE-KEY} ORDER BY type, priority`
   - Apply type filter if user specified one (e.g., "stories only" → `AND issuetype = Story`)

3. **Display Scope**: Show what will be reviewed:
   ```
   Reviewing children of ACM-12345 [Epic] Search performance improvements
   Found: 3 Stories, 1 Task, 1 Spike (5 total)
   ```

   If more than 20 children, warn the user and ask to confirm or filter.

4. **Review Each Child**: For each child issue, use `@hygiene-reviewer` agent to assess:
   - Completeness (fields populated vs template expectations)
   - Summary quality — including length check (flag if > 80 chars, suggest shortening if > 100)
   - Description quality
   - Acceptance Criteria presence
   - Consistency with parent (Components, Target Version match)

   Show progress: "Reviewing 3/5: ACM-12348..."

5. **Summary Table**: Present results as a scored table:
   ```
   Children of ACM-12345 [Epic] Search performance improvements

   Key       | Type  | Summary                           | Chars | Score | Issues
   ----------|-------|-----------------------------------|-------|-------|------------------
   ACM-12346 | Story | Add query result caching layer    | 34    | 9/10  | —
   ACM-12347 | Story | Optimize indexer batch size        | 30    | 6/10  | No AC, no points
   ACM-12348 | Task  | Benchmark search latency          | 26    | 7/10  | No AC
   ACM-12349 | Spike | Evaluate switching to OpenSearch   | 35    | 8/10  | No assignee
   ACM-12350 | Story | Add search query suggestions       | 31    | 3/10  | No desc, no AC

   Average score: 6.6/10
   ```

6. **Common Issues**: Identify patterns across children:
   ```
   Common issues across 5 children:
   - 3/5 missing Acceptance Criteria
   - 2/5 have no Story Points
   - 1/5 has Components mismatched with parent (ACM-12350: Console ≠ Search)
   - 1/5 has empty Description
   - N/5 summaries exceed 80 chars (flag with suggested shortenings)
   ```

7. **Consistency Check**: Flag children that don't match the parent:
   - Components differ from parent
   - Target Version differs from parent
   - Activity Type differs from parent

8. **Recommendations**: Prioritized action list:
   ```
   Recommended actions (highest impact first):
   1. ACM-12350: Add Description and Acceptance Criteria (score: 3/10)
   2. ACM-12347: Add Acceptance Criteria and Story Points (score: 6/10)
   3. ACM-12348: Add Acceptance Criteria (score: 7/10)
   4. ACM-12350: Fix Components (Console → Search) to match parent
   ```

9. **Bulk Fix Option**: Ask if the user wants to apply fixes:
   - **Fix all consistency issues** — update Components/Target Version to match parent
   - **Fix specific issues** — choose which recommendations to apply
   - **Skip** — just keep the report

   For approved fixes, use `editJiraIssue` MCP tool and report each change.

10. **Write Report**: Save to `artifacts/jira-creator/reviews/{parent-key}-batch-review.md`

## Output

- Batch review report written to `artifacts/jira-creator/reviews/{parent-key}-batch-review.md`
