# Feature Template

A **Feature** represents a product capability or market requirement that delivers distinct customer value. Features contain Epics and are the primary unit of product planning.

## JIRA Details

- **Issue Type**: Feature (ID: 10142)
- **Hierarchy Level**: 2
- **Available Fields**: 77

## Smart Defaults

These fields are set automatically unless the user overrides them:

| Field | Key | Default | ID |
|-------|-----|---------|----|
| Activity Type | `customfield_10464` | Product / Portfolio Work | 10610 |

## Summary Guidelines

**Length:** 40-60 characters (max 100)
**Format:** Noun phrase describing the product capability
**Include:** Market need + product capability
**Exclude:** Full sentences, target personas, explanatory clauses

| Example | Chars | Rating |
|---------|-------|--------|
| "Real-Time Compliance Dashboard with Policy Alerts" | 51 | Good |
| "Multi-Cloud Cluster Lifecycle Management" | 41 | Good |
| "Cluster compliance dashboard with real-time policy violation alerts for platform engineers managing 50+ clusters" | 115 | Bad — too long |

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Concise market-facing capability statement (40-60 chars ideal, max 100). Use a noun phrase, not a full sentence. Avoid explanatory clauses. |
| Description | `description` | Use this structure: **Problem** (what's broken/missing), **Target Persona** (who benefits), **Business Value** (measurable impact), **Solution Approach** (high-level how) |
| Components | `components` | Common: Console (33685), Cluster Lifecycle (33696), GRC (33694), Observability (33700), HyperShift (33695), Search (33705), Application Lifecycle (33686), Business Continuity (33687), Global Hub (33693), Edge (33729). See `reference/acm-jira-allowed-values.md` for full list. |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |
| Release Type | `customfield_10851` | GA (19299), Tech Preview (19300), Conditional Tech Preview (19301), Dev Preview (19302) |
| Size | `customfield_10795` | XL (19206), L (19207), M (19208), S (19209), XS (19210) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Parent | `parent` | Link to parent Initiative or Outcome (if applicable) |
| Acceptance Criteria | `customfield_10718` | Testable conditions that define "done" — separate from Description |
| Target Version | `customfield_10855` | Target ACM/MCE release. Leave blank if not yet planned. |
| Product Manager | `customfield_10469` | PM responsible for this feature |
| Architect | `customfield_10467` | Technical architect |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Target start | `customfield_10022` | Planned start date |
| Target end | `customfield_10023` | Planned delivery date |
| Contributors | `customfield_10466` | Key contributors |
| Doc Contact | `customfield_10473` | Documentation writer |
| QA Contact | `customfield_10470` | QA engineer |
| Technical Lead | `customfield_10675` | Engineering lead |
| Manager | `customfield_10677` | Engineering manager |
| Organization Sponsor | `customfield_10558` | Sponsoring org |
| Product Sponsor | `customfield_10612` | Sponsoring product |
| Color Status | `customfield_10712` | Tracking status: Green (11103), Yellow (11104), Red (11105) |
| Release Blocker | `customfield_10847` | Approved (16772), Proposed (16773), Rejected (16774) |

## Example

**Summary**: Real-Time Compliance Dashboard with Policy Alerts

**Components**: Console, GRC

**Priority**: Major

**Release Type**: GA

**Size**: L

**Description**:

**Problem**: Platform engineers managing 50+ clusters lack a centralized view of compliance status. Current workflow requires checking each cluster individually, leading to delayed response to policy violations and audit findings.

**Target Persona**: Platform Engineer, Security Operations

**Business Value**: Reduces mean-time-to-detect compliance violations from hours to minutes. Addresses top customer request (35 support cases in Q3) and competitive gap vs. Rancher.

**Solution Approach**: Add a compliance dashboard to the ACM Console that aggregates policy violations across all managed clusters with configurable alerting thresholds.

**Acceptance Criteria** (separate field — `customfield_10718`):

- Dashboard displays real-time compliance status for all managed clusters
- Policy violations are surfaced within 60 seconds of detection
- Configurable alert thresholds for violation count and severity
- Dashboard supports filtering by cluster, policy, and namespace
- Export compliance report in CSV and PDF formats
