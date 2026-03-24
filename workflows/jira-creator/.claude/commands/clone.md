---
description: Clone an existing JIRA issue with modifications
displayName: clone
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty). The user should provide a source issue key (e.g., "clone ACM-12345"). They may also specify modifications inline (e.g., "clone ACM-12345 for ACM 2.17.0").

## Purpose

Create a new JIRA issue based on an existing one. Fetches all fields from the source issue, lets the user modify specific fields, then creates a new issue. Useful for:
- Same bug across multiple versions
- Similar stories in different components
- Repeating tasks for a new sprint/release
- Creating a related issue with shared context

## Process

1. **Fetch Source Issue**: Use `getJiraIssue` MCP tool to retrieve the full issue. If no key provided, ask the user.

2. **Display Source Summary**: Show a compact preview of the source issue:
   ```
   Cloning from: ACM-12345
   [Bug] Console crashes on cluster import with special characters
   Components: Console | Priority: Major | Severity: Important
   Target Ver: ACM 2.15.0 | Parent: ACM-11000
   ```

3. **Determine Clone Type**: Ask the user what kind of clone:
   - **Same type** (default) — create the same issue type with same fields
   - **Different type** — change the issue type (e.g., clone a Bug as a Story)

4. **Pre-fill Fields**: Copy all populated fields from the source issue, with these adjustments:
   - **Summary**: Prefix with "Clone: " (user can change)
   - **Reporter**: Set to current user (cached from startup)
   - **Status**: Reset (new issues start in backlog/new)
   - **Assignee**: Clear (user can re-assign)
   - **Sprint**: Clear (don't inherit sprint assignment)
   - **Fix versions**: Clear (user sets for new issue)
   - **Git Pull Request / Git Commit / GitHub Issue**: Clear (these are implementation-specific)
   - **Keep**: Description, Components, Priority, Severity, Target Version, Parent, Labels, Acceptance Criteria, Steps to Reproduce, Activity Type, Story Points

5. **Present Modifications**: Show what will be copied and what was cleared. Ask the user:
   - "What would you like to change?" — let them modify any field
   - Apply any modifications mentioned in the original arguments (e.g., "for ACM 2.17.0" → update Target Version)
   - Common modifications to suggest:
     - Target Version (most common reason to clone)
     - Components (clone to different team)
     - Summary (differentiate from source)
     - Parent (re-parent under different Epic/Feature)

6. **Smart Defaults**: Apply template Smart Defaults for the issue type if the source didn't have those fields set.

7. **Parent Inheritance**: If the user changes the parent, offer to inherit Components and Target Version from the new parent instead of the source.

8. **Pre-Creation Review**:

   Use `@field-expert` agent to validate all option fields, then show a compact preview:

   ```
   Cloning ACM-12345 → New [Bug]
   Summary: Console crashes on cluster import with special characters
   Components: Console | Priority: Major | Severity: Important
   Target Ver: ACM 2.17.0 (changed) | Parent: ACM-11000
   ⚠ No Acceptance Criteria set
   Quality: 7/10
   ```

   Ask: **Create**, **Edit**, or **Cancel**?

9. **Create Issue**: Use `createJiraIssue` MCP tool. Report key and link.

10. **Link Issues**: Ask if the user wants to link the new issue to the source:
    - "relates to" (default for same-type clones)
    - "is cloned by" / "clones" (if available)
    - Skip linking

11. **Log**: Append to `artifacts/jira-creator/created-issues.md` with note: "Cloned from {SOURCE-KEY}"

## Output

- Created issue logged to `artifacts/jira-creator/created-issues.md`
