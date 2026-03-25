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

## Summary Best Practices

All JIRA summaries must be concise noun phrases, not full sentences. Length targets:

| Rating | Length | Action |
|--------|--------|--------|
| Ideal | 40-80 chars | No action needed |
| Acceptable | 80-100 chars | Suggest shortening |
| Too long | 100-120 chars | Warn and offer auto-shorten |
| Critical | 120+ chars | Strongly recommend shortening; will truncate in most JIRA views |

### Summary Rules

- Lead with the **what** (action/deliverable), not the **why**
- Use noun phrases or imperative statements, never full sentences
- Remove user story boilerplate ("As a...", "so that...") — move to Description
- Remove explanatory clauses ("to ensure...", "in order to...", "that allows...")
- Condense verbose phrases ("documentation and JIRA tracking" -> "docs & JIRA")
- Always expand "Red Hat Advanced Cluster Management" to just "ACM"
- Preserve full context in the Description field when shortening

### Auto-Shortening Patterns

When a summary exceeds 80 characters, apply these transformations in order:

1. Strip user story boilerplate: `As a [role], I want to [X] so that [Y]` -> extract `[X]`
2. Strip trailing purpose clauses: `to ensure...`, `in order to...`, `so that...`
3. Condense common phrases: "process documentation" -> "process docs", "component ownership map" -> "component ownership"
4. Replace full product names with abbreviations: "Red Hat Advanced Cluster Management" -> "ACM"
5. If still > 80 chars, extract core action + key scope into a compact noun phrase

### Type-Specific Length Guidance

- **Stories/Tasks**: 50-70 chars (more specific scope)
- **Epics/Features**: 40-60 chars (broader scope, needs to fit in Epic panels)
- **Bugs**: 60-80 chars (need enough detail to identify the defect)

## Common Patterns

- When user provides a parent issue key, fetch it first to inherit Components and Target Version
- When creating child issues, suggest inheriting parent's Component and Target Version
- For Bugs, always ask about Severity and Steps to Reproduce
- For Epics, always ask for Epic Name (it's a required unique field)
- For Features, always ask about Release Type and Size
