# Task Template

A **Task** represents technical or operational work that is not directly user-facing. Tasks cover infrastructure, CI/CD, refactoring, and other engineering activities.

## JIRA Details

- **Issue Type**: Task (ID: 10014)
- **Hierarchy Level**: 0
- **Available Fields**: 71

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Clear action statement: "Update...", "Configure...", "Migrate..." |
| Description | `description` | What needs to be done, why, and any context or constraints |
| Components | `components` | ACM component(s) this task relates to |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Assignee | `assignee` | Person responsible for this task |
| Story Points | `customfield_10028` | Estimated effort |
| Activity Type | `customfield_10464` | Categorize: Product Work, Quality, Security, etc. |
| Parent | `parent` | Link to parent Epic if part of a larger effort |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Sprint | `customfield_10020` | Sprint assignment |
| Target Version | `customfield_10855` | Target release (if release-bound) |
| Acceptance Criteria | `customfield_10718` | Definition of done |
| Documentation Type | `customfield_10659` | Docs impact |
| Due date | `duedate` | Hard deadline if applicable |

## Example

**Summary**: Upgrade Go dependencies to address CVE-2024-XXXXX in net/http

**Description**:
## Background
A critical CVE has been published affecting Go's `net/http` package. All ACM backend services built with Go < 1.22.2 are potentially affected.

## Task
- Identify all ACM repositories using affected Go versions
- Update `go.mod` to Go 1.22.2+ in each repository
- Run full test suites to verify no regressions
- Submit PRs to each affected repository

## Affected Repositories
- search-collector
- search-indexer
- search-api
- governance-policy-propagator
- multicloud-operators-subscription

## Constraints
- Must be completed before the next z-stream release
- Each PR needs security team approval
