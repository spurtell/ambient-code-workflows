# /assess.start - Gather Assessment Inputs

## Purpose

Collect all necessary inputs before running a quick or full feasibility assessment. This ensures the assessment has proper context and scope.

## Process

1. **Identify the RFE**
   - Ask for a JIRA URL/issue key OR a text description of the RFE
   - If JIRA URL provided, use `jira_get_issue` to pull full details (summary, description, comments, priority, assignee, customer)
   - If text description provided, confirm understanding with the user

2. **Extract Key Information**
   From the RFE, identify and present back to the user:
   - **Customer/Requester**: Who wants this?
   - **Business Need**: What problem does it solve?
   - **Current Workaround**: How is this handled today?
   - **Priority**: How urgent is this?
   - **Acceptance Criteria**: What defines "done"?
   - Flag any missing information that could affect the assessment

3. **Identify Target Codebases**
   - Ask which GitHub repositories are relevant (frontend, backend, API, etc.)
   - Confirm repo URLs and branches to analyze
   - Note any repos that need cloning vs. already available locally

4. **Confirm Assessment Mode**
   - Ask whether they want a quick scan (/assess.quick) or full analysis (/assess.full)
   - Confirm output preferences (artifact location, Google Drive export)

5. **Create Context File**
   - Write a context summary to `artifacts/rfe-feasibility/{RFE-ID}-context.md`
   - Include all gathered inputs for reference during assessment

## Output

- `artifacts/rfe-feasibility/{RFE-ID}-context.md` - Collected inputs and context

## Next Steps

After gathering inputs:
- Run `/assess.quick` for a fast feasibility scan
- Run `/assess.full` for a comprehensive technical assessment
