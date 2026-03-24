# Initiative Template

An **Initiative** represents a program-level grouping of related Features that together deliver a significant capability. In the ACM JIRA project, Initiatives are created as **Features** with the label `initiative`.

## JIRA Mapping

- **Issue Type**: Feature (ID: 10142)
- **Required Label**: `initiative`
- **Hierarchy**: Groups related Features; may roll up to an Outcome

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Program-level capability statement. Be specific about scope and boundary. |
| Description | `description` | What this initiative delivers, which teams/areas it spans, and its business justification |
| Components | `components` | All ACM component areas involved |
| Target Version | `customfield_10855` | Target ACM release |
| Priority | `priority` | Business priority: Blocker, Critical, Major, Normal, Minor |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Parent | `parent` | Link to parent Outcome if applicable |
| Acceptance Criteria | `customfield_10718` | High-level criteria for initiative completion |
| Activity Type | `customfield_10464` | Usually "Product / Portfolio Work" |
| Product Manager | `customfield_10469` | PM owning this initiative |
| Architect | `customfield_10467` | Technical architect |
| Technical Lead | `customfield_10675` | Engineering lead |
| Size | `customfield_10795` | Estimated scope: XS, S, M, L, XL |
| Release Type | `customfield_10851` | GA, Tech Preview, Dev Preview |
| Target start | `customfield_10022` | Planned start date |
| Target end | `customfield_10023` | Planned completion date |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Additional labels beyond `initiative` |
| Contributors | `customfield_10466` | Cross-team contributors |
| Manager | `customfield_10677` | Engineering manager |
| Organization Sponsor | `customfield_10558` | Sponsoring organization |
| Product Sponsor | `customfield_10612` | Sponsoring product area |

## Example

**Summary**: HyperShift hosted control planes GA readiness for ACM 2.16

**Description**:
This initiative encompasses all work required to bring HyperShift hosted control planes to GA quality in ACM 2.16. It spans multiple teams (HyperShift, Console, Cluster Lifecycle, QE) and includes feature completion, scale testing, documentation, and supportability improvements.

Child Features:
- HyperShift cluster creation wizard improvements
- NodePool management and auto-scaling
- HyperShift observability and monitoring integration
- HyperShift documentation and support runbooks

**Acceptance Criteria**:
- All child Features delivered and verified
- Scale testing passes at target cluster count (500 hosted clusters)
- Documentation complete and reviewed by CCS
- Support team trained and runbooks published
