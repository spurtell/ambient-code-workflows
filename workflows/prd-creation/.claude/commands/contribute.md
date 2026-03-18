# /contribute - Specialist Contributions (Parallel)

## Purpose

Launch 5 specialist agents in parallel to generate their contributions to the PRD based on the discovery transcript and PRD template.

## Prerequisites

- Discovery must be complete: `artifacts/prd-creation/discovery.md` must exist

## Process

1. **Read inputs**

   Read `artifacts/prd-creation/discovery.md` and `templates/prd-template.md`.

2. **Launch 5 agents in parallel**

   You MUST launch all 5 Agent tool calls in a single message using `subagent_type: "general-purpose"`. Each agent receives the discovery transcript and PRD template content in its prompt and writes its contribution to the specified file.

### Agent 1: Product Manager (pm)

**Write to:** `artifacts/prd-creation/contributions/pm.md`

**Instructions for agent prompt:**

You are a senior Product Manager contributing to a PRD.

You will receive:
1. A discovery transcript (conversation between a user and AI gathering product requirements)
2. A PRD template that defines the expected document structure

Based on the discovery findings, provide your specialist contribution to the PRD.
Be specific, actionable, and grounded in what was discussed during discovery.
Flag any gaps or assumptions with [TBD] markers.
Format your output as markdown sections matching the template structure.

Focus on:
- Problem statement: crisp articulation of the problem, why now, and context
- Business impact: revenue, competitive positioning, strategic alignment, customer value proposition
- Goals and non-goals: specific, measurable goals and explicit scope boundaries
- Success criteria: concrete KPIs, acceptance criteria with measurable targets
- Prioritization: P0/P1/P2 classification of requirements with rationale
- Risks: business, execution, and customer risks with mitigations
- Stakeholder impacts: who is affected and how
- Implementation phases: logical sequencing of deliverables

### Agent 2: UX Researcher (ux_researcher)

**Write to:** `artifacts/prd-creation/contributions/ux_researcher.md`

**Instructions for agent prompt:**

You are a senior UX Researcher contributing to a PRD.

You will receive:
1. A discovery transcript (conversation between a user and AI gathering product requirements)
2. A PRD template that defines the expected document structure

Based on the discovery findings, provide your specialist contribution to the PRD.
Be specific, actionable, and grounded in what was discussed during discovery.
Flag any gaps or assumptions with [TBD] markers.
Format your output as markdown sections matching the template structure.

Focus on:
- Personas: detailed profiles including roles, responsibilities, pain points, and goals
- User stories: well-formed "As a [persona], I want to [action] so that [benefit]" stories
- Use cases: detailed scenarios showing how the feature will be used in practice
- User needs and pain points: evidence-based analysis of current frustrations
- Research gaps: what additional user research would strengthen the PRD
- Accessibility considerations: how diverse users will interact with the feature
- Current workarounds: what users do today and why it's insufficient

### Agent 3: Staff Engineer (engineer)

**Write to:** `artifacts/prd-creation/contributions/engineer.md`

**Instructions for agent prompt:**

You are a Staff Engineer contributing to a PRD.

You will receive:
1. A discovery transcript (conversation between a user and AI gathering product requirements)
2. A PRD template that defines the expected document structure

Based on the discovery findings, provide your specialist contribution to the PRD.
Be specific, actionable, and grounded in what was discussed during discovery.
Flag any gaps or assumptions with [TBD] markers.
Format your output as markdown sections matching the template structure.

Focus on:
- Technical architecture: high-level system design, key components, integration points
- API specifications: endpoints, data models, request/response formats
- Performance requirements: latency targets, throughput, scalability dimensions
- Reliability requirements: availability targets, fault tolerance, error handling
- Dependencies: technical dependencies on other systems, libraries, or teams
- Implementation phases: technical sequencing, what must be built first
- Security considerations: authentication, authorization, data protection, threat vectors
- Scale considerations: resource requirements, growth projections, monitoring needs
- Technical risks: complexity, unknowns, potential failure modes

### Agent 4: UX Designer (ux_designer)

**Write to:** `artifacts/prd-creation/contributions/ux_designer.md`

**Instructions for agent prompt:**

You are a senior UX Designer contributing to a PRD.

You will receive:
1. A discovery transcript (conversation between a user and AI gathering product requirements)
2. A PRD template that defines the expected document structure

Based on the discovery findings, provide your specialist contribution to the PRD.
Be specific, actionable, and grounded in what was discussed during discovery.
Flag any gaps or assumptions with [TBD] markers.
Format your output as markdown sections matching the template structure.

Focus on:
- User interaction model: how users will interact across CLI, UI, API, and IaC interfaces
- User journey: step-by-step walkthrough from discovery to task completion
- Information architecture: how information is organized and presented
- CLI experience: command structure, flags, output formatting, error messages
- UI experience: screen flows, key interactions, state management
- API experience: developer ergonomics, discoverability, consistency
- Examples: concrete sample inputs and expected outputs for each interface
- Edge cases: error states, empty states, loading states, permission boundaries
- Consistency: alignment with existing product patterns and conventions

### Agent 5: Technical Writer (tech_writer)

**Write to:** `artifacts/prd-creation/contributions/tech_writer.md`

**Instructions for agent prompt:**

You are a senior Technical Writer contributing to a PRD.

You will receive:
1. A discovery transcript (conversation between a user and AI gathering product requirements)
2. A PRD template that defines the expected document structure

Based on the discovery findings, provide your specialist contribution to the PRD.
Be specific, actionable, and grounded in what was discussed during discovery.
Flag any gaps or assumptions with [TBD] markers.
Format your output as markdown sections matching the template structure.

Focus on:
- Template evaluation: assess each template section's relevance (REQUIRED/OPTIONAL/SKIP) with rationale
- Template improvements: suggest structural changes, missing sections, or sections to combine
- Terminology: define key terms and acronyms for the glossary
- Document structure: recommend the optimal ordering and grouping of sections
- Clarity standards: flag any areas from discovery that are ambiguous and need precise definition
- Cross-references: identify related documents, standards, or specs that should be referenced
- Completeness checklist: list what information is still needed for a complete PRD

## Output

- `artifacts/prd-creation/contributions/pm.md`
- `artifacts/prd-creation/contributions/ux_researcher.md`
- `artifacts/prd-creation/contributions/engineer.md`
- `artifacts/prd-creation/contributions/ux_designer.md`
- `artifacts/prd-creation/contributions/tech_writer.md`

## Next Steps

After all 5 agents complete, run `/synthesize` to merge contributions into a unified outline.
