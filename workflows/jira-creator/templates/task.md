# Task Template

A **Task** represents technical or operational work that is not directly user-facing. Tasks cover infrastructure, CI/CD, refactoring, and other engineering activities.

## JIRA Details

- **Issue Type**: Task (ID: 10014)
- **Hierarchy Level**: 0
- **Available Fields**: 71

## Summary Guidelines

**Length:** 50-70 characters (max 100)
**Format:** Imperative action statement: "Update...", "Configure...", "Migrate..."
**Include:** Action verb + target + key context
**Exclude:** Full sentences, rationale — put those in Description

| Example | Chars | Rating |
|---------|-------|--------|
| "Upgrade Go dependencies for CVE-2024-XXXXX" | 44 | Good |
| "Configure CI pipeline for multi-arch builds" | 44 | Good |
| "Update all Go dependencies across ACM repositories to address critical CVE in net/http package" | 96 | Bad — too long |

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | Clear action statement (50-70 chars ideal, max 100): "Update...", "Configure...", "Migrate...". Use imperative noun phrase, not a full sentence. |
| Description | `description` | Use this structure: **Background** (why this task is needed), **Task** (specific actions to take), **Constraints** (deadlines, dependencies, approvals needed) |
| Components | `components` | Common: Console (33685), Cluster Lifecycle (33696), GRC (33694), Observability (33700), HyperShift (33695), Search (33705), Application Lifecycle (33686), Business Continuity (33687), Global Hub (33693), Edge (33729). See `reference/acm-jira-allowed-values.md` for full list. |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Assignee | `assignee` | Person responsible for this task |
| Story Points | `customfield_10028` | Estimated effort |
| Activity Type | `customfield_10464` | Categorize: Product / Portfolio Work (10610), Quality / Stability / Reliability (10608), Security & Compliance (10609), Incidents & Support (10607), Future Sustainability (10606) |
| Parent | `parent` | Link to parent Epic if part of a larger effort |
| Acceptance Criteria | `customfield_10718` | Definition of done — separate from Description |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Sprint | `customfield_10020` | Sprint assignment |
| Target Version | `customfield_10855` | Target release (if release-bound) |
| Documentation Type | `customfield_10659` | Docs impact |
| Due date | `duedate` | Hard deadline if applicable |

## Example

**Summary**: Upgrade Go deps for CVE-2024-XXXXX in net/http

**Components**: Secure Engineering

**Priority**: Critical

**Description**:

**Background**: A critical CVE has been published affecting Go's `net/http` package. All ACM backend services built with Go < 1.22.2 are potentially affected.

**Task**:
- Identify all ACM repositories using affected Go versions
- Update `go.mod` to Go 1.22.2+ in each repository
- Run full test suites to verify no regressions
- Submit PRs to each affected repository

Affected repositories: search-collector, search-indexer, search-api, governance-policy-propagator, multicloud-operators-subscription.

**Constraints**:
- Must be completed before the next z-stream release
- Each PR needs security team approval

**Acceptance Criteria** (separate field — `customfield_10718`):

- All affected repositories updated to Go 1.22.2+
- Full test suites pass in each repository
- PRs approved by security team and merged
- No regressions in CI pipelines
