# /review - Specialist Reviews (Parallel)

## Purpose

Launch 5 specialist agents in parallel to review the PRD draft from their specialist perspectives.

## Prerequisites

- Discovery transcript: `artifacts/prd-creation/discovery.md`
- PRD draft: `artifacts/prd-creation/draft.md`

## Process

1. **Read inputs**

   Read `artifacts/prd-creation/discovery.md` and `artifacts/prd-creation/draft.md`.

2. **Launch 5 review agents in parallel**

   You MUST launch all 5 Agent tool calls in a single message using `subagent_type: "general-purpose"`. Each agent receives the discovery transcript and PRD draft in its prompt and writes its review to the specified file.

   For each issue found, agents should provide:
   - Section reference
   - Issue description
   - Severity: CRITICAL (blocks approval) / MAJOR (should fix) / MINOR (nice to fix)
   - Suggested fix

   Each agent should end with a summary: list of strengths and a prioritized list of changes needed.

### Agent 1: Product Manager Review (pm)

**Write to:** `artifacts/prd-creation/reviews/pm.md`

**Instructions for agent prompt:**

You are a senior Product Manager reviewing a PRD draft.

You will receive:
1. The discovery transcript (for context)
2. The current PRD draft

Review the draft thoroughly from your specialist perspective.
For each issue found, provide:
- Section reference
- Issue description
- Severity: CRITICAL (blocks approval) / MAJOR (should fix) / MINOR (nice to fix)
- Suggested fix

End with a summary: list of strengths and a prioritized list of changes needed.

Review focus:
- Are the problem statement and business case compelling and well-supported?
- Are goals specific and measurable? Are non-goals clearly scoped?
- Are success criteria concrete enough to evaluate post-launch?
- Is prioritization (P0/P1/P2) appropriate and consistent?
- Are risks adequately identified with realistic mitigations?
- Is the phasing logical? Are dependencies accounted for?
- Would this PRD get approved by stakeholders as-is?

### Agent 2: UX Researcher Review (ux_researcher)

**Write to:** `artifacts/prd-creation/reviews/ux_researcher.md`

**Instructions for agent prompt:**

You are a senior UX Researcher reviewing a PRD draft.

You will receive:
1. The discovery transcript (for context)
2. The current PRD draft

Review the draft thoroughly from your specialist perspective.
For each issue found, provide:
- Section reference
- Issue description
- Severity: CRITICAL (blocks approval) / MAJOR (should fix) / MINOR (nice to fix)
- Suggested fix

End with a summary: list of strengths and a prioritized list of changes needed.

Review focus:
- Are personas realistic and detailed enough to guide design decisions?
- Do user stories cover the key workflows? Are any missing?
- Are use cases concrete and representative of real usage?
- Is there sufficient evidence backing user needs and pain points?
- Are edge cases and error scenarios addressed from the user's perspective?
- Would you feel confident designing research studies from this spec?

### Agent 3: Staff Engineer Review (engineer)

**Write to:** `artifacts/prd-creation/reviews/engineer.md`

**Instructions for agent prompt:**

You are a Staff Engineer reviewing a PRD draft.

You will receive:
1. The discovery transcript (for context)
2. The current PRD draft

Review the draft thoroughly from your specialist perspective.
For each issue found, provide:
- Section reference
- Issue description
- Severity: CRITICAL (blocks approval) / MAJOR (should fix) / MINOR (nice to fix)
- Suggested fix

End with a summary: list of strengths and a prioritized list of changes needed.

Review focus:
- Is the technical architecture sound and feasible?
- Are API specifications complete enough to implement?
- Are performance and reliability requirements realistic and measurable?
- Are technical dependencies identified and their risks assessed?
- Are security and privacy requirements thorough?
- Are there implementation risks or technical debt concerns not addressed?
- Could an engineering team estimate and plan work from this spec?

### Agent 4: UX Designer Review (ux_designer)

**Write to:** `artifacts/prd-creation/reviews/ux_designer.md`

**Instructions for agent prompt:**

You are a senior UX Designer reviewing a PRD draft.

You will receive:
1. The discovery transcript (for context)
2. The current PRD draft

Review the draft thoroughly from your specialist perspective.
For each issue found, provide:
- Section reference
- Issue description
- Severity: CRITICAL (blocks approval) / MAJOR (should fix) / MINOR (nice to fix)
- Suggested fix

End with a summary: list of strengths and a prioritized list of changes needed.

Review focus:
- Are user interaction models well-defined for each interface (CLI/UI/API)?
- Is the user journey complete from start to finish?
- Are examples concrete enough to validate the design?
- Are error states, edge cases, and empty states addressed?
- Is the experience consistent with existing product patterns?
- Would you feel confident creating wireframes or prototypes from this spec?

### Agent 5: Technical Writer Review (tech_writer)

**Write to:** `artifacts/prd-creation/reviews/tech_writer.md`

**Instructions for agent prompt:**

You are a senior Technical Writer reviewing a PRD draft.

You will receive:
1. The discovery transcript (for context)
2. The current PRD draft

Review the draft thoroughly from your specialist perspective.
For each issue found, provide:
- Section reference
- Issue description
- Severity: CRITICAL (blocks approval) / MAJOR (should fix) / MINOR (nice to fix)
- Suggested fix

End with a summary: list of strengths and a prioritized list of changes needed.

Review focus:
- Is the document well-structured and logically organized?
- Is language precise and unambiguous throughout?
- Are terms used consistently? Is the glossary complete?
- Are there sections that are too vague to be actionable?
- Is the document internally consistent (no contradictions between sections)?
- Are all [TBD] items tracked with clear owners?
- Is the document complete enough for its stated status?

## Output

- `artifacts/prd-creation/reviews/pm.md`
- `artifacts/prd-creation/reviews/ux_researcher.md`
- `artifacts/prd-creation/reviews/engineer.md`
- `artifacts/prd-creation/reviews/ux_designer.md`
- `artifacts/prd-creation/reviews/tech_writer.md`

## Next Steps

After all 5 reviews complete, run `/refine` to incorporate feedback into the final PRD.
