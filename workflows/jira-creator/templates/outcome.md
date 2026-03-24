# Outcome Template

An **Outcome** represents a strategic business objective or measurable result the organization wants to achieve. In the ACM JIRA project, Outcomes are created as **Features** with the label `outcome`.

## JIRA Mapping

- **Issue Type**: Feature (ID: 10142)
- **Required Label**: `outcome`
- **Hierarchy**: Above Feature — group Features and Initiatives under Outcomes

## Smart Defaults

These fields are set automatically unless the user overrides them:

| Field | Key | Default | ID |
|-------|-----|---------|----|
| Activity Type | `customfield_10464` | Product / Portfolio Work | 10610 |
| Labels | `labels` | `outcome` | — |

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Strategic objective statement. Start with a verb: "Improve...", "Enable...", "Reduce..." |
| Description | `description` | Use this structure: **Business Objective** (what we want to achieve), **Why It Matters** (strategic context), **Success Metrics** (how we measure achievement), **Scope** (what areas/teams are involved) |
| Components | `components` | Common: Console (33685), Cluster Lifecycle (33696), GRC (33694), Observability (33700), HyperShift (33695), Search (33705), Application Lifecycle (33686), Business Continuity (33687), Global Hub (33693), Edge (33729). See `reference/acm-jira-allowed-values.md` for full list. |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |
| Size | `customfield_10795` | XL (19206), L (19207), M (19208), S (19209), XS (19210) |
| Release Type | `customfield_10851` | GA (19299), Tech Preview (19300), Conditional Tech Preview (19301), Dev Preview (19302) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Acceptance Criteria | `customfield_10718` | Measurable success criteria — separate from Description. How do we know the outcome is achieved? |
| Target Version | `customfield_10855` | Target ACM release. Leave blank if outcome spans multiple releases. |
| Product Manager | `customfield_10469` | PM responsible for this outcome |
| Architect | `customfield_10467` | Technical architect overseeing the outcome |
| Target start | `customfield_10022` | When work should begin |
| Target end | `customfield_10023` | When outcome should be achieved |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Contributors | `customfield_10466` | Key contributors across teams |
| Doc Contact | `customfield_10473` | Documentation lead |
| QA Contact | `customfield_10470` | QA lead |

## Example

**Summary**: Enable seamless multi-cloud cluster lifecycle management across AWS, Azure, and GCP

**Components**: Cluster Lifecycle, Console

**Priority**: Major

**Size**: XL

**Release Type**: GA

**Description**:

**Business Objective**: Provide a unified experience for provisioning, upgrading, and decommissioning Kubernetes clusters across AWS, Azure, and GCP.

**Why It Matters**: Organizations adopting multi-cloud strategies are blocked by provider-specific workflows in ACM. This is the #1 request from enterprise customers and a competitive gap vs. Rancher and Tanzu.

**Success Metrics**: Reduce operational complexity of multi-cloud management by 40% as measured by time-to-provision and support ticket volume.

**Scope**: Cluster Lifecycle (provisioning APIs), Console (unified wizard), QE (cross-provider test matrix).

**Acceptance Criteria** (separate field — `customfield_10718`):

- Cluster provisioning workflow is consistent across AWS, Azure, and GCP
- Upgrade operations complete within documented SLA for all 3 providers
- Support ticket volume for multi-cloud operations decreases by 40%
- Customer satisfaction score for multi-cloud management improves by 20%
