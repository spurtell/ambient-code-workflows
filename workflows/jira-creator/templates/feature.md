# Feature Template

A **Feature** represents a product capability or market requirement that delivers distinct customer value. Features contain Epics and are the primary unit of product planning.

## JIRA Details

- **Issue Type**: Feature (ID: 10142)
- **Hierarchy Level**: 2
- **Available Fields**: 77

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Market-facing capability statement. Focus on the customer problem being solved. |
| Description | `description` | Problem statement, target persona, business value, and high-level solution approach |
| Components | `components` | Primary ACM component(s) — see reference for valid values |
| Target Version | `customfield_10855` | Target ACM/MCE release version |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Parent | `parent` | Link to parent Initiative or Outcome (if applicable) |
| Acceptance Criteria | `customfield_10718` | Testable conditions that define "done" for this feature |
| Release Type | `customfield_10851` | GA (19299), Tech Preview (19300), Dev Preview (19302) |
| Size | `customfield_10795` | XL (19206), L (19207), M (19208), S (19209), XS (19210) |
| Activity Type | `customfield_10464` | Usually "Product / Portfolio Work" (10610) |
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

**Summary**: Cluster compliance dashboard with real-time policy violation alerts

**Description**:
**Problem**: Platform engineers managing 50+ clusters lack a centralized view of compliance status. Current workflow requires checking each cluster individually, leading to delayed response to policy violations and audit findings.

**Target Persona**: Platform Engineer, Security Operations

**Business Value**: Reduces mean-time-to-detect compliance violations from hours to minutes. Addresses top customer request (35 support cases in Q3) and competitive gap vs. Rancher.

**Solution Approach**: Add a compliance dashboard to the ACM Console that aggregates policy violations across all managed clusters with configurable alerting thresholds.

**Acceptance Criteria**:
- Dashboard displays real-time compliance status for all managed clusters
- Policy violations are surfaced within 60 seconds of detection
- Configurable alert thresholds for violation count and severity
- Dashboard supports filtering by cluster, policy, and namespace
- Export compliance report in CSV and PDF formats
