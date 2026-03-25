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

3. **Gather Minimal Fields** (matches "Always Ask" in each template):
   - **All types**: Summary, Description, Components, Priority
   - **Outcome**: + Size, Release Type
   - **Initiative**: + Size, Release Type
   - **Feature**: + Size, Release Type
   - **Epic**: + Epic Name, Target Version
   - **Story**: + Target Version
   - **Bug**: + Target Version, Severity, Steps to Reproduce
   - **Task**: (no additional fields)
   - **Spike**: (no additional fields)

4. **Smart Defaults** (applied automatically, skip asking):
   - Priority: default to `Normal` (10003) unless specified
   - Reporter: current user (auto-detected)
   - Project: always `ACM`
   - Outcome: Activity Type → Product / Portfolio Work (10610), Labels → `outcome`
   - Initiative: Activity Type → Product / Portfolio Work (10610), Labels → `initiative`
   - Feature: Activity Type → Product / Portfolio Work (10610)
   - Story: Activity Type → Product / Portfolio Work (10610)

5. **Parent Inheritance**: If the user provides a parent issue key, fetch it and pre-fill:
   - Components (from parent)
   - Target Version (from parent)
   - Activity Type (from parent, if not already a smart default)

6. **Summary Validation**: After gathering the Summary, check its length:
   - **<= 80 chars**: Good — proceed
   - **81-100 chars**: Show warning with char count, offer to shorten
   - **> 100 chars**: Strongly recommend shortening; offer auto-shorten option
   Apply auto-shortening rules (strip boilerplate, condense phrases, extract core action). Preserve full text in Description.

7. **Pre-Creation Review**:

   Use `@field-expert` agent to validate Components and any option fields, then show a compact preview:

   ```
   [TYPE] Summary text here (N chars)
   Components: Console | Priority: Normal | Severity: Important
   Target Ver: ACM 2.16.0 | Parent: (none)
   ⚠ No Acceptance Criteria set
   ```

   Flag missing recommended fields as warnings (single line each). Flag summary length if > 80 chars. Show a quick hygiene score (e.g., "Quality: 6/10").

   Ask: **Create**, **Edit**, or **Cancel**?

8. **Create Issue**: Use `createJiraIssue` MCP tool. Report key and link.

9. **Log**: Append to `artifacts/jira-creator/created-issues.md`

## Output

- Created issue logged to `artifacts/jira-creator/created-issues.md`
