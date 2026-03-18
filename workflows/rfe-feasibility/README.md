# RFE Feasibility Assessment

Assess the technical feasibility and implementation complexity of RFEs by analyzing requirements, exploring codebases, verifying APIs, and delivering comprehensive assessment documentation.

## Overview

This workflow provides two assessment modes for evaluating RFE feasibility:

### Quick Mode (~15-30 min)

A fast scan that checks RFE completeness, identifies obvious blockers, and provides a rough sizing estimate without deep codebase analysis.

### Full Mode (~2 hours)

A comprehensive technical assessment that includes codebase exploration, API verification, and produces a detailed feasibility document with implementation plans, risk assessment, and design recommendations.

## Commands

| Command | Purpose |
|---------|---------|
| `/assess.start` | Gather inputs (JIRA URL, repos, preferences) |
| `/assess.quick` | Quick feasibility scan with rough sizing |
| `/assess.full` | Comprehensive technical assessment |
| `/assess.export` | Export artifacts to Google Drive |

## Workflow

```text
/assess.start (gather inputs)
    |
    +---> /assess.quick (fast scan)
    |         |
    |         +---> Done, or escalate to /assess.full
    |
    +---> /assess.full (deep analysis)
              |
              +---> /assess.export (share with team)
```

## Assessment Output

Every assessment produces:

- **Feasibility Rating**: HIGH / MEDIUM / LOW
- **Implementation Complexity**: LOW / MEDIUM / HIGH
- **Story Point Estimate**: Range (e.g., 3-5 SP)
- **Risk Level**: LOW / MEDIUM / HIGH
- **Recommendation**: APPROVE / APPROVE WITH CONDITIONS / NEEDS MORE INVESTIGATION / REJECT

## Artifacts

All outputs are written to `artifacts/rfe-feasibility/`:

```text
artifacts/rfe-feasibility/
  {RFE-ID}-context.md                # Gathered inputs
  {RFE-ID}-quick-assessment.md       # Quick scan results
  {RFE-ID}-feasibility-assessment.md # Full assessment
  {RFE-ID}-api-verification.md       # Backend API details
```

## Integrations

- **JIRA** - Read RFE details and related issues
- **Google Drive** - Export deliverables for sharing
- **GitHub** - Clone and analyze source repositories

## Getting Started

1. Load the workflow in ACP
2. Run `/assess.start` to provide your RFE details and target repos
3. Choose `/assess.quick` for a fast scan or `/assess.full` for deep analysis
4. Run `/assess.export` to share results with your team
