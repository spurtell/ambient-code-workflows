# CLAUDE.md — ACM JIRA Creator Workflow

## Behavioral Guidelines

- Always load the appropriate template from `templates/` before starting issue creation
- Use the `@field-expert` agent to validate Components, Target Version, and other option fields against known allowed values
- Use the `@hygiene-reviewer` agent when reviewing existing issues
- Never guess field IDs — always reference `reference/acm-jira-guide.md` for field keys and allowed values
- When creating issues via MCP, always include the 4 required fields: Summary, Project, Issue Type, Reporter
- For Outcome and Initiative types, create as Feature with appropriate label (`outcome` or `initiative`)
- Present a confirmation summary before creating any issue
- Log all created issues to `artifacts/jira-creator/created-issues.md`

## Agent Usage Rules

- `@field-expert`: Invoke when validating field values, looking up component IDs, version IDs, or any option field values. This agent has deep knowledge of all ACM JIRA field metadata.
- `@hygiene-reviewer`: Invoke when reviewing existing issues. This agent knows the quality standards and completeness criteria for each issue type.

## Quick vs Detailed Creation

**Quick** (`/quick`): Only ask for fields marked "Always ask" in the template. Skip recommendations and optional fields. Get to creation fast.

**Detailed** (`/create`): Walk through "Always ask" fields first, then "Recommended" fields, then offer "Optional" fields. Explain each field's purpose briefly. Produce a thorough, high-quality issue.

## Common Patterns

- When user provides a parent issue key, fetch it first to inherit Components and Target Version
- When creating child issues, suggest inheriting parent's Component and Target Version
- For Bugs, always ask about Severity and Steps to Reproduce
- For Epics, always ask for Epic Name (it's a required unique field)
- For Features, always ask about Release Type and Size
