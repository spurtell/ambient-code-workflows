---
description: Detailed interactive JIRA issue creation with full field guidance
displayName: create
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty). If the user specifies an issue type (e.g., "create bug", "create epic"), skip the type selection step.

## Purpose

Create a well-formed ACM JIRA issue through an interactive, guided process. This is the **detailed** mode — walk the user through all recommended fields with explanations.

## Process

1. **Select Issue Type**: If not provided in arguments, ask the user to choose:
   - Outcome, Initiative, Feature, Epic, Story, Bug, Task, or Spike

2. **Load Template**: Read the corresponding template from `templates/{type}.md`. This contains the field groups and guidance for that type.

3. **Load Reference**: Read `reference/acm-jira-guide.md` for field keys and allowed values.

4. **Apply Smart Defaults**: Check the template for a "Smart Defaults" section. Apply those values automatically and inform the user (e.g., "Activity Type set to Product / Portfolio Work. Override? [Enter to keep]").

5. **Parent Inheritance**: If the user provides a parent issue key (or one is given in arguments):
   - Fetch the parent issue via `getJiraIssue` MCP tool
   - Pre-fill from parent: Components, Target Version, Activity Type
   - Show inherited values: "Inherited from {PARENT-KEY}: Components=Console, Target Version=ACM 2.16.0"
   - User can override any inherited value during field gathering

6. **Gather Required Fields** ("Always ask" group):
   - Walk through each field, explaining its purpose
   - For fields already set via Smart Defaults or Parent Inheritance, show the current value and ask to confirm or change
   - For option fields (Priority, Severity, Components, Target Version, etc.), present the allowed values
   - Use `@field-expert` agent to validate selections

7. **Gather Recommended Fields**:
   - Present each recommended field with its purpose
   - Allow user to skip any with Enter/blank
   - For parent linking (if not already set), offer to look up existing issues

8. **Gather Optional Fields**:
   - Ask "Would you like to set any optional fields?" and list them
   - Only gather values for fields the user wants to set

9. **Pre-Creation Review**:

   Before creating, run a thorough review of the draft issue:

   a. **Validate fields**: Use `@field-expert` agent to verify all Components, Target Version, and option field values resolve to valid IDs.

   b. **Present JIRA-style preview**: Format the draft to mirror how it will appear in JIRA:
      ```
      ┌─────────────────────────────────────────────────┐
      │ [TYPE] Summary text here                        │
      ├─────────────────────────────────────────────────┤
      │ Project:    ACM                                 │
      │ Type:       Feature          Priority: Major    │
      │ Components: Console, GRC     Size:     L        │
      │ Target Ver: (not set)        Release:  GA       │
      │ Parent:     ACM-12345        Assignee: (none)   │
      ├─────────────────────────────────────────────────┤
      │ Description:                                    │
      │ (first 3-5 lines of description)                │
      ├─────────────────────────────────────────────────┤
      │ Acceptance Criteria:                            │
      │ - criterion 1                                   │
      │ - criterion 2                                   │
      └─────────────────────────────────────────────────┘
      ```

   c. **Hygiene warnings**: Flag issues but do NOT block creation:
      - **Missing recommended fields** — list which ones are unset (e.g., "Acceptance Criteria: not set")
      - **Summary quality** — warn if too vague, too long (>120 chars), or missing component context
      - **Description quality** — warn if it doesn't follow the structured format for this type
      - **Hierarchy gap** — warn if no parent is set where one is expected (Story without Epic, Epic without Feature)

   d. **Score**: Show a quick hygiene score (e.g., "Quality: 8/10 — missing Acceptance Criteria")

   e. **Ask for confirmation**: Present three options:
      - **Create** — proceed as-is
      - **Edit** — go back and change specific fields
      - **Cancel** — abort

10. **Create Issue**:
   - Use `createJiraIssue` MCP tool with the gathered fields
   - For Outcome/Initiative types, create as Feature and add the appropriate label
   - Report the created issue key and link
   - Append to `artifacts/jira-creator/created-issues.md`

11. **Follow-up**:
   - Ask if user wants to create child issues (e.g., Epics under a Feature, Stories under an Epic)
   - Offer to create related issues

## Agent Collaboration

- Use `@field-expert` agent to validate all option field values before submission
- If creating a Bug, emphasize Steps to Reproduce and Severity
- If creating an Epic, ensure Epic Name is unique and descriptive

## Output

- Created issue logged to `artifacts/jira-creator/created-issues.md`
