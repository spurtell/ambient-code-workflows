# Bug Template

A **Bug** is a defect report describing incorrect, unexpected, or broken behavior in the product.

## JIRA Details

- **Issue Type**: Bug (ID: 10016)
- **Hierarchy Level**: 0
- **Available Fields**: 80
- **Unique Fields**: Steps to Reproduce (`customfield_10821`), Special Handling (`customfield_10670`), Escape Impact/Reason, Corrective Measures

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | "[Component] [broken behavior] when [condition]" — be specific and searchable |
| Description | `description` | Use this structure: **Problem** (what's broken and how it manifests), **Impact** (who is affected and how badly), **Environment** (ACM version, OCP version, browser, infrastructure) |
| Steps to Reproduce | `customfield_10821` | Numbered steps to reproduce the issue. Be precise — include exact navigation paths, input values, and expected vs actual results. |
| Components | `components` | Common: Console (33685), Cluster Lifecycle (33696), GRC (33694), Observability (33700), HyperShift (33695), Search (33705), Application Lifecycle (33686), Business Continuity (33687), Global Hub (33693), Edge (33729). See `reference/acm-jira-allowed-values.md` for full list. |
| Target Version | `customfield_10855` | Version to fix in |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |
| Severity | `customfield_10840` | Critical (19917), Important (19918), Moderate (19919), Low (19920), Informational (19921) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Acceptance Criteria | `customfield_10718` | What does "fixed" look like? — separate from Description |
| Assignee | `assignee` | Developer to fix the bug |
| Regression | `customfield_10623` | Yes (16062) / No (16061) — was this working before? |
| Affects versions | `versions` | Version(s) where the bug exists |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Sprint | `customfield_10020` | Sprint assignment |
| Release Blocker | `customfield_10847` | Approved (16772), Proposed (16773), Rejected (16774) |
| Customer Impact | `customfield_10689` | Escalated (16324), Facing (16325), QE Confirmed (16326), Reported (16327) |
| Special Handling | `customfield_10670` | compliance-priority (19864), Major Incident (19867), Minor Incident (19868), security-select (19869) |
| Environment | `environment` | Additional environment details beyond what's in Description |
| Story Points | `customfield_10028` | Estimated fix effort |
| Parent | `parent` | Link to parent Epic if part of a tracked effort |
| Test Coverage | `customfield_10638` | + (15875), - (15876), ? (15877) |

## Example

**Summary**: [Console] Cluster import wizard fails silently when kubeconfig contains special characters

**Components**: Console

**Target Version**: ACM 2.15.1

**Priority**: Major

**Severity**: Important

**Description**:

**Problem**: When importing a cluster using a kubeconfig file that contains special characters (e.g., `@`, `#`, `%`) in the cluster name or context, the import wizard completes without error but the cluster never appears in the managed clusters list.

**Impact**: Users who have non-standard characters in their kubeconfig (common with EKS and custom installations) cannot import clusters via the UI. They must manually edit their kubeconfig first, which is undiscoverable.

**Environment**:
- ACM 2.15.0 on OCP 4.16.2
- Browser: Chrome 131, Firefox 134
- Affected kubeconfig: EKS-generated with `@` in ARN-based context names

**Steps to Reproduce** (separate field — `customfield_10821`):

1. Generate a kubeconfig from EKS (`aws eks update-kubeconfig`)
2. Note the context name contains `arn:aws:eks:...` with `:` and `/` characters
3. Navigate to Infrastructure > Clusters > Import cluster
4. Upload the kubeconfig file
5. Complete the wizard and click "Import"
6. Observe: wizard completes with "success" message
7. Wait 5 minutes — cluster never appears in managed clusters list
8. Check `open-cluster-management-agent` namespace on target cluster — no resources created

**Acceptance Criteria** (separate field — `customfield_10718`):

- Cluster import succeeds with kubeconfig containing special characters in names/contexts
- If special characters genuinely cannot be supported, display a clear error message during validation (before the user clicks Import)
- Add validation feedback in the import wizard for unsupported characters
