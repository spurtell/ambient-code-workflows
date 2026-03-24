---
description: Create multiple related JIRA issues in one pass with automatic linking
displayName: bulk
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty). The user may describe the structure inline (e.g., "bulk epic with 3 stories for search performance improvements").

## Purpose

Create a parent issue and its children in a single workflow. Shared fields are set once on the parent and inherited by all children. Saves time and ensures consistency when setting up a new body of work.

## Supported Patterns

| Pattern | Parent | Children |
|---------|--------|----------|
| Feature breakdown | Feature | Epics |
| Epic breakdown | Epic | Stories, Bugs, Tasks, Spikes |
| Mixed | Epic | Any combination of child types |

## Process

1. **Determine Structure**: If not provided in arguments, ask the user:
   - What is the parent type? (Feature or Epic)
   - How many children? What types?
   - Or: "Describe the work and I'll suggest a breakdown"

   If the user describes work in plain language, propose a structure:
   ```
   Proposed structure:
   [Epic] Search performance improvements
   ├── [Story] Add query result caching layer
   ├── [Story] Optimize search indexer batch size
   ├── [Task] Benchmark current search latency baseline
   └── [Spike] Evaluate switching to OpenSearch

   Create this structure? (Yes / Edit / Cancel)
   ```

2. **Create Parent First**: Use the `/create` flow (steps 1-10) for the parent issue. This establishes:
   - Components
   - Target Version
   - Priority
   - Activity Type
   - All other parent-level fields

3. **Define Shared Fields**: After the parent is created, confirm which fields children will inherit:
   ```
   Children will inherit from {PARENT-KEY}:
   - Components: Search
   - Target Version: ACM 2.16.0
   - Activity Type: Product / Portfolio Work
   - Priority: Major

   Override any of these for all children? (Enter to keep)
   ```

4. **Gather Children**: For each child issue, collect only the fields that differ:
   - **Summary** (required — unique per child)
   - **Type** (if mixed types)
   - **Description** (brief is fine — can be expanded later)
   - **Story Points** (if applicable)
   - **Assignee** (if known)

   Present as a table for efficient input:
   ```
   #  | Type  | Summary                              | Points | Assignee
   1  | Story | Add query result caching layer        | 5      | —
   2  | Story | Optimize search indexer batch size     | 3      | —
   3  | Task  | Benchmark current search latency      | 2      | —
   4  | Spike | Evaluate switching to OpenSearch       | 3      | —
   ```

   The user can provide all children at once or add them one at a time.

5. **Pre-Creation Review**: Show the complete structure before creating anything:
   ```
   ┌─ [Epic] Search performance improvements (ACM-XXXXX — already created)
   │  Components: Search | Target Ver: ACM 2.16.0 | Priority: Major
   │
   ├── [Story] Add query result caching layer (5 pts)
   ├── [Story] Optimize search indexer batch size (3 pts)
   ├── [Task] Benchmark current search latency baseline (2 pts)
   └── [Spike] Evaluate switching to OpenSearch (3 pts)

   Total: 4 children | 13 story points
   All children inherit: Components=Search, Target Ver=ACM 2.16.0

   ⚠ No Acceptance Criteria on any children
   ⚠ No Assignees set
   ```

   Ask: **Create all**, **Edit**, or **Cancel**?

6. **Create Children**: Create each child issue sequentially:
   - Set parent link to the parent issue
   - Apply inherited fields
   - Apply child-specific fields
   - Use `@field-expert` agent to validate each
   - Report progress: "Created 1/4: ACM-12346 — Add query result caching layer"

7. **Summary Report**: After all children are created, show:
   ```
   Bulk creation complete: 4/4 issues created

   Parent: ACM-12345 — Search performance improvements
   ├── ACM-12346 [Story] Add query result caching layer (5 pts)
   ├── ACM-12347 [Story] Optimize search indexer batch size (3 pts)
   ├── ACM-12348 [Task] Benchmark current search latency (2 pts)
   └── ACM-12349 [Spike] Evaluate switching to OpenSearch (3 pts)
   ```

8. **Log**: Append all created issues to `artifacts/jira-creator/created-issues.md` with note: "Bulk: parent {PARENT-KEY}"

## Error Handling

- If a child creation fails, report the error and continue with remaining children
- After all attempts, list successes and failures
- Offer to retry failed children

## Output

- All created issues logged to `artifacts/jira-creator/created-issues.md`
