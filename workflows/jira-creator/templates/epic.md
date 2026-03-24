# Epic Template

An **Epic** represents a deliverable body of work that can be completed within a release cycle. Epics contain Stories, Bugs, Tasks, and Spikes.

## JIRA Details

- **Issue Type**: Epic (ID: 10000)
- **Hierarchy Level**: 1
- **Available Fields**: 82 (most of any type)
- **Unique Fields**: Epic Name (`customfield_10011`), OpenShift Planning Ack (`customfield_10761`)

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Deliverable scope statement. Be specific about what will be built/changed. |
| Epic Name | `customfield_10011` | Short unique identifier (appears in Epic Link dropdowns). Keep it concise. |
| Description | `description` | Scope, goals, technical approach, and definition of done |
| Components | `components` | Primary ACM component(s) — see reference for valid values |
| Target Version | `customfield_10855` | Target ACM/MCE release version |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Parent Link | `customfield_10018` | Link to parent Feature |
| Acceptance Criteria | `customfield_10718` | Testable conditions that define "done" |
| Activity Type | `customfield_10464` | Categorize the work type |
| Architect | `customfield_10467` | Technical architect |
| Technical Lead | `customfield_10675` | Engineering lead |
| Story Points | `customfield_10028` | Estimated effort |
| Size | `customfield_10795` | XL, L, M, S, XS |
| Release Type | `customfield_10851` | GA, Tech Preview, Dev Preview |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Target start | `customfield_10022` | Planned start date |
| Target end | `customfield_10023` | Planned delivery date |
| Documentation Type | `customfield_10659` | Type of docs needed |
| OpenShift Planning Ack | `customfield_10761` | QE/Doc/PX acknowledgments |
| Contributors | `customfield_10466` | Key contributors |
| Manager | `customfield_10677` | Engineering manager |
| Product Manager | `customfield_10469` | PM contact |
| Color Status | `customfield_10712` | Tracking: Green, Yellow, Red |
| Release Blocker | `customfield_10847` | Blocker status if applicable |

## Example

**Summary**: Implement compliance dashboard backend API and data aggregation pipeline

**Epic Name**: Compliance Dashboard Backend

**Description**:
## Goal
Build the backend services that power the compliance dashboard feature. This includes a data aggregation pipeline that collects policy violation data from managed clusters and an API layer that serves dashboard queries.

## Scope
- Policy violation data aggregation from managed clusters via ManagedClusterInfo
- REST API endpoints for dashboard queries (violations by cluster, by policy, by time range)
- WebSocket endpoint for real-time violation streaming
- Data retention and cleanup for violation history (configurable, default 90 days)

## Out of Scope
- Frontend UI (separate Epic)
- Alerting/notification system (separate Epic)
- Custom policy authoring

## Technical Approach
Extend the existing search-collector to index policy violation events. Add a new compliance-aggregator component that processes violations and maintains materialized views for dashboard queries.

**Acceptance Criteria**:
- API returns compliance status for all managed clusters within 2 seconds
- Real-time violations appear via WebSocket within 60 seconds of occurrence
- Data aggregation handles 500+ managed clusters at scale
- API supports pagination, filtering, and sorting
- Violation history retained for configurable duration
- Unit and integration test coverage > 80%
