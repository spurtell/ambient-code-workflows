# PRD Creation Workflow

An AI-powered multi-agent workflow for drafting Product Requirements Documents. Five specialist agents contribute to and review each PRD, running in parallel for speed. No external dependencies — runs entirely within the Ambient Code Platform.

## Multi-Agent Approach

| Agent | Contribution Focus | Review Focus |
|-------|-------------------|--------------|
| **Product Manager** | Problem framing, business case, goals, success criteria, prioritization | Strategy, measurability, stakeholder readiness |
| **UX Researcher** | Personas, user stories, use cases, pain points | Persona depth, scenario coverage, research gaps |
| **Staff Engineer** | Architecture, APIs, performance, security, dependencies | Feasibility, completeness, technical risks |
| **UX Designer** | Interaction models, user journeys, CLI/UI/API experience | Flow completeness, consistency, edge cases |
| **Technical Writer** | Template evaluation, structure, terminology, completeness | Clarity, consistency, actionability |

## Workflow Phases

```
1. Discovery       /discover      Interactive Q&A to gather requirements
2. Contributions   /contribute    5 agents contribute in parallel
3. Synthesis       /synthesize    Merge inputs into unified outline
4. Draft           /draft         Generate the full PRD
5. Reviews         /review        5 agents review in parallel
6. Refinement      /refine        Incorporate feedback into final draft
```

Steps 2 and 5 run all five agents simultaneously. Discovery is interactive; all other steps run automatically.

Use `/speedrun` to execute all phases sequentially with minimal interaction.

## Getting Started

1. Load the workflow in ACP
2. Run `/discover` to start the interactive discovery session
3. Answer the specialist's questions about your feature/product
4. Run `/contribute` through `/refine` to complete the PRD (or use `/speedrun`)
5. Find your final PRD at `artifacts/prd-creation/prd-final.md`

## Output Artifacts

All outputs are saved in `artifacts/prd-creation/`:

```
artifacts/prd-creation/
├── discovery.md              # Discovery transcript
├── contributions/            # Specialist contributions
│   ├── pm.md
│   ├── ux_researcher.md
│   ├── engineer.md
│   ├── ux_designer.md
│   └── tech_writer.md
├── outline.md                # Synthesized outline
├── draft.md                  # Full PRD draft
├── reviews/                  # Specialist reviews
│   ├── pm.md
│   ├── ux_researcher.md
│   ├── engineer.md
│   ├── ux_designer.md
│   └── tech_writer.md
└── prd-final.md              # Final refined PRD
```
