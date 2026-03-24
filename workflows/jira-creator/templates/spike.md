# Spike Template

A **Spike** is a time-boxed research or investigation task. Spikes produce knowledge (not code) and have a defined timebox and set of questions to answer.

## JIRA Details

- **Issue Type**: Spike (ID: 10104)
- **Hierarchy Level**: 0
- **Available Fields**: 57 (leanest type)

## Always Ask

| Field | Key | Guidance |
|-------|-----|----------|
| Summary | `summary` | "Spike: [topic] — [key question]". Always prefix with "Spike:" for clarity. |
| Description | `description` | Research questions, scope, timebox, and expected deliverables |
| Components | `components` | ACM component(s) this investigation relates to |
| Priority | `priority` | Blocker (10000), Critical (10001), Major (10002), Normal (10003), Minor (10004) |

## Recommended

| Field | Key | Guidance |
|-------|-----|----------|
| Assignee | `assignee` | Researcher/investigator |
| Story Points | `customfield_10028` | Timebox in points (e.g., 3 = ~3 days) |
| Acceptance Criteria | `customfield_10718` | What questions must be answered? What artifact produced? |
| Parent | `parent` | Link to parent Epic if part of a larger effort |

## Optional

| Field | Key | Guidance |
|-------|-----|----------|
| Labels | `labels` | Categorization labels |
| Sprint | `customfield_10020` | Sprint assignment |
| Target Version | `customfield_10855` | Target release context |
| Due date | `duedate` | End of timebox |

## Example

**Summary**: Spike: Evaluate Argo CD vs Flux for GitOps addon replacement

**Description**:
## Research Questions
1. How do Argo CD and Flux compare for multi-cluster GitOps at scale (500+ clusters)?
2. What is the migration effort from the current GitOps addon to each option?
3. What are the resource footprint differences on the hub cluster?
4. How does each handle large ApplicationSet deployments (1000+ applications)?
5. What is the upstream community health and release cadence for each?

## Timebox
3 story points (~3 days of focused research)

## Deliverables
- Comparison matrix document covering all research questions
- Proof-of-concept deployment of top candidate with 50 managed clusters
- Recommendation with trade-offs for team review

## Out of Scope
- Full migration plan (that will be a separate Epic if we decide to proceed)
- Performance benchmarking beyond basic resource footprint
