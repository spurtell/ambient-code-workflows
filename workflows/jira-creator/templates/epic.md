# Epic Template

An **Epic** represents a deliverable body of work that can be completed within a release cycle. Epics contain Stories, Bugs, Tasks, and Spikes.

## JIRA Details

- **Issue Type**: Epic (ID: 10000)
- **Hierarchy Level**: 1
- **Available Fields**: 82 (most of any type)
- **Unique Fields**: Epic Name (`customfield_10011`), OpenShift Planning Ack (`customfield_10761`)

## Summary Guidelines

**Length:** 40-60 characters (max 100)
**Format:** Noun phrase describing the deliverable scope
**Include:** Capability area + deliverable scope
**Exclude:** Full sentences, explanatory clauses ("to ensure...", "in order to...")

| Example | Chars | Rating |
|---------|-------|--------|
| "Compliance Dashboard Backend API" | 34 | Good |
| "Search Performance Optimization" | 32 | Good |
| "Implement compliance dashboard backend API and data aggregation pipeline for real-time monitoring" | 98 | Bad — too long |

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Concise deliverable scope statement (40-60 chars ideal, max 100). Use a noun phrase, not a full sentence. Must fit in Epic panels without truncation. |
| Epic Name | `customfield_10011` | Short unique identifier (appears in Epic Link dropdowns). Keep it concise. |
| Description | `description` | Use this structure: **Goal** (what this epic delivers), **Scope** (what's included), **Out of Scope** (what's excluded), **Technical Approach** (high-level how) |
| Components | `components` | Common: Console (33685), Cluster Lifecycle (33696), GRC (33694), Observability (33700), HyperShift (33695), Search (33705), Application Lifecycle (33686), Business Continuity (33687), Global Hub (33693), Edge (33729). See `reference/acm-jira-allowed-values.md` for full list. |
| Target Version | `customfield_10855` | Target ACM/MCE release version |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Parent Link | `customfield_10018` | Link to parent Feature |
| Acceptance Criteria | `customfield_10718` | Testable conditions that define "done" — separate from Description |
| Activity Type | `customfield_10464` | Categorize: Product / Portfolio Work (10610), Quality / Stability / Reliability (10608), Security & Compliance (10609), etc. |
| Architect | `customfield_10467` | Technical architect |
| Technical Lead | `customfield_10675` | Engineering lead |
| Story Points | `customfield_10028` | Estimated effort |
| Size | `customfield_10795` | XL (19206), L (19207), M (19208), S (19209), XS (19210) |
| Release Type | `customfield_10851` | GA (19299), Tech Preview (19300), Dev Preview (19302) |

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
| Color Status | `customfield_10712` | Tracking: Green (11103), Yellow (11104), Red (11105) |
| Release Blocker | `customfield_10847` | Approved (16772), Proposed (16773), Rejected (16774) |

## Example

**Summary**: Compliance Dashboard Backend API

**Epic Name**: Compliance Dashboard Backend

**Components**: GRC, Search

**Target Version**: ACM 2.16.0

**Priority**: Major

**Description**:

**Goal**: Build the backend services that power the compliance dashboard feature. This includes a data aggregation pipeline that collects policy violation data from managed clusters and an API layer that serves dashboard queries.

**Scope**:
- Policy violation data aggregation from managed clusters via ManagedClusterInfo
- REST API endpoints for dashboard queries (violations by cluster, by policy, by time range)
- WebSocket endpoint for real-time violation streaming
- Data retention and cleanup for violation history (configurable, default 90 days)

**Out of Scope**:
- Frontend UI (separate Epic)
- Alerting/notification system (separate Epic)
- Custom policy authoring

**Technical Approach**: Extend the existing search-collector to index policy violation events. Add a new compliance-aggregator component that processes violations and maintains materialized views for dashboard queries.

**Acceptance Criteria** (separate field — `customfield_10718`):

- API returns compliance status for all managed clusters within 2 seconds
- Real-time violations appear via WebSocket within 60 seconds of occurrence
- Data aggregation handles 500+ managed clusters at scale
- API supports pagination, filtering, and sorting
- Violation history retained for configurable duration
- Unit and integration test coverage > 80%
