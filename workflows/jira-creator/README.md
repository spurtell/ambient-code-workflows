# ACM JIRA Creator Workflow

Create, review, and improve JIRA issues for the Red Hat Advanced Cluster Management (ACM) project.

## Features

- **Quick Create** (`/quick`): Fast-path issue creation with minimal fields for experienced users
- **Detailed Create** (`/create`): Guided interactive creation with field explanations and validation
- **Hygiene Review** (`/review`): Analyze existing issues for completeness, quality, and consistency

## Supported Issue Types

| Type | Hierarchy | Description |
|------|-----------|-------------|
| Outcome | Strategic | Business objective (created as Feature + `outcome` label) |
| Initiative | Program | Cross-team capability grouping (created as Feature + `initiative` label) |
| Feature | Product | Market requirement / product capability |
| Epic | Delivery | Deliverable body of work within a release |
| Story | Work Item | User-facing functionality |
| Bug | Work Item | Defect report |
| Task | Work Item | Technical/operational work |
| Spike | Work Item | Time-boxed research/investigation |

## Commands

### `/create [type]`

Interactive detailed creation. Walks through all field groups:
1. **Always Ask** — required and essential fields
2. **Recommended** — important but skippable fields
3. **Optional** — additional metadata

### `/quick [type] [summary]`

Fast creation with just the essentials. Supports inline arguments:
```
/quick bug Console crashes on cluster import
/quick story Add violation badges to cluster list
```

### `/review [ACM-XXXXX]`

Fetches an existing issue and produces a hygiene report covering:
- Field completeness against type-specific standards
- Summary and description quality
- Acceptance criteria presence and testability
- Hierarchy and linking correctness
- Metadata consistency

## Agents

| Agent | Purpose |
|-------|---------|
| `field-expert` | Validates field values against ACM JIRA allowed values, resolves component/version IDs |
| `hygiene-reviewer` | Assesses issue quality and produces structured improvement recommendations |

## Templates

Each issue type has a template in `templates/` with:
- Field groups (Always Ask, Recommended, Optional) with JIRA field keys
- Guidance for each field
- A worked example showing a well-formed issue

## Reference Data

The `reference/` directory contains ACM JIRA field metadata:
- `acm-jira-guide.md` — Field availability matrix, option values, workflow guidance
- `acm-jira-allowed-values.md` — Components, versions, and products lists

## Prerequisites

- Atlassian MCP server configured with access to `issues.redhat.com`
- User must have permission to create issues in the ACM project
