# Initiative Template

An **Initiative** represents a program-level grouping of related Features that together deliver a significant capability. In the ACM JIRA project, Initiatives are created as **Features** with the label `initiative`.

## JIRA Mapping

- **Issue Type**: Feature (ID: 10142)
- **Required Label**: `initiative`
- **Hierarchy**: Groups related Features; may roll up to an Outcome

## Smart Defaults

These fields are set automatically unless the user overrides them:

| Field | Key | Default | ID |
|-------|-----|---------|----|
| Activity Type | `customfield_10464` | Product / Portfolio Work | 10610 |
| Labels | `labels` | `initiative` | — |

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Program-level capability statement. Be specific about scope and boundary. |
| Description | `description` | Use this structure: **Program Scope** (what this initiative delivers), **Teams Involved** (which areas it spans), **Business Justification** (why this grouping matters), **Child Features** (list of planned features) |
| Components | `components` | Common: Console (33685), Cluster Lifecycle (33696), GRC (33694), Observability (33700), HyperShift (33695), Search (33705), Application Lifecycle (33686), Business Continuity (33687), Global Hub (33693), Edge (33729). See `reference/acm-jira-allowed-values.md` for full list. |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |
| Size | `customfield_10795` | XL (19206), L (19207), M (19208), S (19209), XS (19210) |
| Release Type | `customfield_10851` | GA (19299), Tech Preview (19300), Conditional Tech Preview (19301), Dev Preview (19302) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Parent | `parent` | Link to parent Outcome if applicable |
| Acceptance Criteria | `customfield_10718` | High-level criteria for initiative completion — separate from Description |
| Target Version | `customfield_10855` | Target ACM release. Leave blank if initiative spans multiple releases. |
| Product Manager | `customfield_10469` | PM owning this initiative |
| Architect | `customfield_10467` | Technical architect |
| Technical Lead | `customfield_10675` | Engineering lead |
| Target start | `customfield_10022` | Planned start date |
| Target end | `customfield_10023` | Planned completion date |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Contributors | `customfield_10466` | Cross-team contributors |
| Manager | `customfield_10677` | Engineering manager |
| Organization Sponsor | `customfield_10558` | Sponsoring organization |
| Product Sponsor | `customfield_10612` | Sponsoring product area |

## Example

**Summary**: HyperShift hosted control planes GA readiness for ACM 2.16

**Components**: HyperShift, Console, Cluster Lifecycle, QE

**Priority**: Critical

**Size**: XL

**Release Type**: GA

**Description**:

**Program Scope**: All work required to bring HyperShift hosted control planes to GA quality in ACM 2.16, including feature completion, scale testing, documentation, and supportability improvements.

**Teams Involved**: HyperShift (core engine), Console (UI workflows), Cluster Lifecycle (API integration), QE (test coverage), Documentation (user guides and runbooks).

**Business Justification**: HyperShift is the #1 strategic differentiator for ACM. Moving from Tech Preview to GA unlocks enterprise adoption and addresses 12 active customer POCs waiting on GA support commitment.

**Child Features**:
- HyperShift cluster creation wizard improvements
- NodePool management and auto-scaling
- HyperShift observability and monitoring integration
- HyperShift documentation and support runbooks

**Acceptance Criteria** (separate field — `customfield_10718`):

- All child Features delivered and verified
- Scale testing passes at target cluster count (500 hosted clusters)
- Documentation complete and reviewed by CCS
- Support team trained and runbooks published
