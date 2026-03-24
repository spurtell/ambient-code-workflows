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

4. **Gather Required Fields** ("Always ask" group):
   - Walk through each field, explaining its purpose
   - For option fields (Priority, Severity, Components, Target Version, etc.), present the allowed values
   - Use `@field-expert` agent to validate selections

5. **Gather Recommended Fields**:
   - Present each recommended field with its purpose
   - Allow user to skip any with Enter/blank
   - For parent linking, offer to look up existing issues

6. **Gather Optional Fields**:
   - Ask "Would you like to set any optional fields?" and list them
   - Only gather values for fields the user wants to set

7. **Review Summary**:
   - Present a formatted summary of all fields that will be set
   - Highlight any potential issues (missing recommended fields, etc.)
   - Ask for confirmation

8. **Create Issue**:
   - Use `createJiraIssue` MCP tool with the gathered fields
   - For Outcome/Initiative types, create as Feature and add the appropriate label
   - Report the created issue key and link
   - Append to `artifacts/jira-creator/created-issues.md`

9. **Follow-up**:
   - Ask if user wants to create child issues (e.g., Epics under a Feature, Stories under an Epic)
   - Offer to create related issues

## Agent Collaboration

- Use `@field-expert` agent to validate all option field values before submission
- If creating a Bug, emphasize Steps to Reproduce and Severity
- If creating an Epic, ensure Epic Name is unique and descriptive

## Output

- Created issue logged to `artifacts/jira-creator/created-issues.md`
