---
description: Review an existing JIRA issue for hygiene, completeness, and quality
displayName: review
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty). The user should provide a JIRA issue key (e.g., "ACM-12345").

## Purpose

Analyze an existing ACM JIRA issue and produce actionable recommendations for improving its quality, completeness, and consistency with team standards.

## Process

1. **Fetch Issue**: Use `getJiraIssue` MCP tool to retrieve the full issue data. If no key provided, ask the user.

2. **Identify Type**: Determine the issue type from the fetched data.

3. **Load Standards**: Read the corresponding template from `templates/{type}.md` to understand expected fields.

4. **Invoke Hygiene Reviewer**: Use `@hygiene-reviewer` agent to perform a comprehensive assessment covering:

   ### Completeness Check
   - Are all "Always ask" fields populated?
   - Are recommended fields populated?
   - Is the Description substantive (not just a title restatement)?
   - For Bugs: Are Steps to Reproduce present and clear?
   - For Epics: Is Epic Name set?
   - For Features: Are Size and Release Type set?

   ### Quality Check
   - **Summary length**: Check character count against thresholds (ideal: 40-80, acceptable: 80-100, too long: 100+). If > 80 chars, suggest a shortened version using auto-shortening rules (strip boilerplate, condense phrases, extract core action). Show before/after with char counts.
   - **Summary content**: Is it concise, specific, and actionable? Flag if it contains user story boilerplate ("As a..."), explanatory clauses ("to ensure...", "in order to..."), or vague terms ("improvement", "enhancement" without specifics).
   - **Description**: Is it detailed enough for someone unfamiliar to understand?
   - **Acceptance Criteria**: Are they testable and specific?
   - **Components**: Are they appropriate for the work described?
   - **Priority/Severity**: Do they align with the issue's actual impact?

   ### Hierarchy Check
   - Does the issue have a parent link where expected?
   - Is the parent type appropriate (Story→Epic, Epic→Feature)?
   - Are Components and Target Version consistent with parent?

   ### Metadata Check
   - Is Target Version set and current (not EOL)?
   - Is Activity Type set?
   - Are Labels meaningful and consistent?
   - Is Assignee set for in-progress work?

5. **Generate Report**: Write a structured review to `artifacts/jira-creator/reviews/{issue-key}-review.md`:

   ```markdown
   # Hygiene Review: {ISSUE-KEY}
   ## Summary: {issue summary}
   ## Type: {issue type}
   ## Overall Score: {X}/10

   ### Findings
   #### Critical (must fix)
   - ...

   #### Recommended (should fix)
   - ...

   #### Suggestions (nice to have)
   - ...

   ### Recommended Field Updates
   | Field | Current | Recommended | Reason |
   |-------|---------|-------------|--------|
   ```

6. **Offer Fixes**: Ask the user if they want to apply any of the recommended changes. Use `editJiraIssue` MCP tool for approved changes.

## Output

- Review report written to `artifacts/jira-creator/reviews/{issue-key}-review.md`
