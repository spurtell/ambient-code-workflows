# Story Template

A **Story** represents a unit of user-facing functionality that delivers value to a specific persona. Stories are the primary work item for development teams.

## JIRA Details

- **Issue Type**: Story (ID: 10009)
- **Hierarchy Level**: 0
- **Available Fields**: 77

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | User-centric statement. Use "As a [role], [action]" or describe the user-visible behavior. |
| Description | `description` | User story details: who, what, why, and any technical context needed |
| Components | `components` | ACM component(s) this story belongs to |
| Target Version | `customfield_10855` | Target ACM/MCE release |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Parent | `parent` | Link to parent Epic |
| Acceptance Criteria | `customfield_10718` | Testable criteria — what must be true for this story to be "done"? |
| Story Points | `customfield_10028` | Estimated effort (Fibonacci: 1, 2, 3, 5, 8, 13) |
| Activity Type | `customfield_10464` | Categorize the work |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Assignee | `assignee` | Developer who will implement |
| Sprint | `customfield_10020` | Sprint assignment |
| Documentation Type | `customfield_10659` | Docs impact |
| Regression | `customfield_10623` | Yes (16062) / No (16061) |
| Test Coverage | `customfield_10638` | + (15875), - (15876), ? (15877) |
| Customer Impact | `customfield_10689` | Customer escalated/facing/reported |
| Organization Sponsor | `customfield_10558` | Sponsoring org |

## Example

**Summary**: Display policy violation count badges on cluster list page

**Description**:
As a platform engineer, I want to see policy violation counts directly on the cluster list page so that I can quickly identify clusters with compliance issues without navigating to each cluster's detail view.

## Context
This story is part of the Compliance Dashboard epic. It adds violation count badges to the existing cluster list view in the ACM Console.

## Technical Notes
- Query the compliance-aggregator API for violation counts per cluster
- Display badge with count next to cluster name (red for critical, yellow for warning)
- Badge should link to the cluster's compliance detail view
- Use existing PatternFly badge component

**Acceptance Criteria**:
- Violation count badge appears next to each cluster name on the cluster list page
- Badge color reflects highest severity violation (red=critical, yellow=important, green=compliant)
- Clicking the badge navigates to the cluster's compliance detail view
- Badge updates within 60 seconds when new violations are detected
- Clusters with no violations show a green checkmark
- Badge does not appear if user lacks policy view permissions
