# /synthesize - Synthesize Contributions into Outline

## Purpose

Merge all 5 specialist contributions into a unified, structured PRD outline that resolves conflicts and integrates the best insights from each specialist.

## Prerequisites

- Discovery transcript: `artifacts/prd-creation/discovery.md`
- All 5 specialist contributions in `artifacts/prd-creation/contributions/`

## Process

1. **Read all inputs**

   Read the following files:
   - `artifacts/prd-creation/discovery.md`
   - `artifacts/prd-creation/contributions/pm.md`
   - `artifacts/prd-creation/contributions/ux_researcher.md`
   - `artifacts/prd-creation/contributions/engineer.md`
   - `artifacts/prd-creation/contributions/ux_designer.md`
   - `artifacts/prd-creation/contributions/tech_writer.md`
   - `templates/prd-template.md`

2. **Synthesize into a unified outline**

   Act as a senior Product Manager synthesizing inputs from five specialists into a unified PRD outline.

   Create a unified, structured outline that:
   - Integrates the best insights from all specialists without redundancy
   - Resolves any conflicts between specialist recommendations (note the resolution)
   - Follows the template structure, incorporating the Technical Writer's section relevance assessment
   - Includes key points, data, and decisions for each section
   - Notes where information is solid vs. where assumptions are being made
   - Flags remaining gaps with [TBD] markers
   - Is detailed enough that a full draft can be written from the outline alone

   Format as a markdown outline matching the template's section structure.

3. **Write the outline**

   Write the synthesized outline to `artifacts/prd-creation/outline.md`.

## Output

- `artifacts/prd-creation/outline.md` — Unified PRD outline

## Next Steps

After synthesis, run `/draft` to write the full PRD from the outline.
