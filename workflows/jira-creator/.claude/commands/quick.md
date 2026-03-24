---
description: Quick JIRA issue creation with minimal fields
displayName: quick
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty). The user may provide type and summary inline, e.g., "quick bug Console crashes on cluster import".

## Purpose

Fast-path issue creation for experienced users. Only asks for the essential fields — skips recommended and optional fields entirely.

## Process

1. **Parse Input**: Extract issue type and summary from arguments if provided. If not, ask for:
   - Issue type (one word: outcome, initiative, feature, epic, story, bug, task, spike)
   - Summary (one line)

2. **Load Template**: Read `templates/{type}.md` to identify the "Always ask" fields only.

3. **Gather Minimal Fields**:
   - **All types**: Summary, Components, Priority
   - **Feature**: + Target Version, Description
   - **Epic**: + Target Version, Epic Name, Description
   - **Story**: + Target Version, Description
   - **Bug**: + Target Version, Severity, Steps to Reproduce, Description
   - **Task**: + Description
   - **Spike**: + Description
   - **Outcome/Initiative**: + Description

4. **Smart Defaults**:
   - Priority: default to `Normal` (10003) unless specified
   - Reporter: current user (auto-detected)
   - Project: always `ACM`

5. **Pre-Creation Review**:

   Use `@field-expert` agent to validate Components and any option fields, then show a compact preview:

   ```
   [TYPE] Summary text here
   Components: Console | Priority: Normal | Severity: Important
   Target Ver: ACM 2.16.0 | Parent: (none)
   ⚠ No Acceptance Criteria set
   ```

   Flag missing recommended fields as warnings (single line each). Show a quick hygiene score (e.g., "Quality: 6/10").

   Ask: **Create**, **Edit**, or **Cancel**?

6. **Create Issue**: Use `createJiraIssue` MCP tool. Report key and link.

7. **Log**: Append to `artifacts/jira-creator/created-issues.md`

## Output

- Created issue logged to `artifacts/jira-creator/created-issues.md`
