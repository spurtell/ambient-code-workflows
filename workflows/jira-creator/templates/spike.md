# Spike Template

A **Spike** is a time-boxed research or investigation task. Spikes produce knowledge (not code) and have a defined timebox and set of questions to answer.

## JIRA Details

- **Issue Type**: Spike (ID: 10104)
- **Hierarchy Level**: 0
- **Available Fields**: 57 (leanest type)

## Summary Guidelines

**Length:** 50-70 characters (max 100, including "Spike: " prefix)
**Format:** "Spike: [topic] — [key question]"
**Include:** Research topic + primary question
**Exclude:** Full sentences, detailed scope — put those in Description

| Example | Chars | Rating |
|---------|-------|--------|
| "Spike: Argo CD vs Flux for GitOps addon" | 41 | Good |
| "Spike: OpenSearch feasibility for ACM Search" | 46 | Good |
| "Spike: Evaluate whether Argo CD or Flux would be a better replacement for the current GitOps addon at scale" | 110 | Bad — too long |

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | "Spike: [topic] — [key question]" (50-70 chars ideal, max 100). Always prefix with "Spike:" for clarity. Keep the topic and question concise. |
| Description | `description` | Use this structure: **Research Questions** (numbered list of specific questions to answer), **Timebox** (effort budget in points/days), **Deliverables** (what artifact will be produced), **Out of Scope** (what this spike will NOT cover) |
| Components | `components` | Common: Console (33685), Cluster Lifecycle (33696), GRC (33694), Observability (33700), HyperShift (33695), Search (33705), Application Lifecycle (33686), Business Continuity (33687), Global Hub (33693), Edge (33729). See `reference/acm-jira-allowed-values.md` for full list. |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Assignee | `assignee` | Researcher/investigator |
| Story Points | `customfield_10028` | Timebox in points (e.g., 3 = ~3 days) |
| Acceptance Criteria | `customfield_10718` | What questions must be answered? What artifact produced? — separate from Description |
| Parent | `parent` | Link to parent Epic if part of a larger effort |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Sprint | `customfield_10020` | Sprint assignment |
| Target Version | `customfield_10855` | Target release context |
| Due date | `duedate` | End of timebox |

## Example

**Summary**: Spike: Argo CD vs Flux for GitOps addon

**Components**: Application Lifecycle, GitOps Addon

**Priority**: Major

**Description**:

**Research Questions**:
1. How do Argo CD and Flux compare for multi-cluster GitOps at scale (500+ clusters)?
2. What is the migration effort from the current GitOps addon to each option?
3. What are the resource footprint differences on the hub cluster?
4. How does each handle large ApplicationSet deployments (1000+ applications)?
5. What is the upstream community health and release cadence for each?

**Timebox**: 3 story points (~3 days of focused research)

**Deliverables**:
- Comparison matrix document covering all research questions
- Proof-of-concept deployment of top candidate with 50 managed clusters
- Recommendation with trade-offs for team review

**Out of Scope**:
- Full migration plan (that will be a separate Epic if we decide to proceed)
- Performance benchmarking beyond basic resource footprint

**Acceptance Criteria** (separate field — `customfield_10718`):

- All 5 research questions answered with evidence
- Comparison matrix document published to team wiki
- POC deployed and results documented
- Recommendation presented to team with clear trade-offs
