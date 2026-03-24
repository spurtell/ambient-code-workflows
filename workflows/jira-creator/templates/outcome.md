# Outcome Template

An **Outcome** represents a strategic business objective or measurable result the organization wants to achieve. In the ACM JIRA project, Outcomes are created as **Features** with the label `outcome`.

## JIRA Mapping

- **Issue Type**: Feature (ID: 10142)
- **Required Label**: `outcome`
- **Hierarchy**: Above Feature — group Features and Initiatives under Outcomes

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Strategic objective statement. Start with a verb: "Improve...", "Enable...", "Reduce..." |
| Description | `description` | Define the business outcome: what success looks like, why it matters, how it will be measured |
| Components | `components` | Primary ACM component area(s) this outcome impacts |
| Target Version | `customfield_10855` | Target ACM release for achieving this outcome |
| Priority | `priority` | Business priority: Blocker, Critical, Major, Normal, Minor |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Acceptance Criteria | `customfield_10718` | Measurable success criteria — how do we know the outcome is achieved? |
| Activity Type | `customfield_10464` | Usually "Product / Portfolio Work" for outcomes |
| Product Manager | `customfield_10469` | PM responsible for this outcome |
| Architect | `customfield_10467` | Technical architect overseeing the outcome |
| Target start | `customfield_10022` | When work should begin |
| Target end | `customfield_10023` | When outcome should be achieved |
| Size | `customfield_10795` | Estimated scope: XS, S, M, L, XL |
| Release Type | `customfield_10851` | GA, Tech Preview, Dev Preview |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Additional labels beyond `outcome` |
| Contributors | `customfield_10466` | Key contributors across teams |
| Doc Contact | `customfield_10473` | Documentation lead |
| QA Contact | `customfield_10470` | QA lead |

## Example

**Summary**: Enable seamless multi-cloud cluster lifecycle management across AWS, Azure, and GCP

**Description**:
Organizations managing Kubernetes clusters across multiple cloud providers need a unified experience for provisioning, upgrading, and decommissioning clusters. This outcome targets reducing the operational complexity of multi-cloud management by 40% as measured by time-to-provision and support ticket volume.

**Acceptance Criteria**:
- Cluster provisioning workflow is consistent across AWS, Azure, and GCP
- Upgrade operations complete within documented SLA for all 3 providers
- Support ticket volume for multi-cloud operations decreases by 40%
- Customer satisfaction score for multi-cloud management improves by 20%
