# /refine - Refine Draft into Final PRD

## Purpose

Incorporate specialist review feedback and optional user feedback into a polished, final PRD.

## Prerequisites

- PRD draft: `artifacts/prd-creation/draft.md`
- All 5 specialist reviews in `artifacts/prd-creation/reviews/`

## Process

1. **Ask for user feedback**

   Before refining, ask the user if they have any additional feedback, corrections, or priorities they want incorporated. Wait for their response. If they say none, proceed.

2. **Read all inputs**

   Read the following files:
   - `artifacts/prd-creation/draft.md`
   - `artifacts/prd-creation/reviews/pm.md`
   - `artifacts/prd-creation/reviews/ux_researcher.md`
   - `artifacts/prd-creation/reviews/engineer.md`
   - `artifacts/prd-creation/reviews/ux_designer.md`
   - `artifacts/prd-creation/reviews/tech_writer.md`

3. **Produce the final PRD**

   Act as a senior Product Manager producing the final PRD draft.

   Produce an updated PRD that addresses the review feedback:
   - Apply all CRITICAL fixes
   - Apply MAJOR fixes where they improve the document
   - Apply MINOR fixes where practical
   - If you disagree with a suggestion, keep the original and briefly note why
   - Incorporate any additional user feedback

   Output the complete, final PRD in markdown format. Do not include review commentary — just the clean, polished document.

4. **Write the final PRD**

   Write the final PRD to `artifacts/prd-creation/prd-final.md`.

5. **Provide summary**

   After writing, provide a brief summary of:
   - Key changes made based on reviews
   - Any CRITICAL/MAJOR issues that were addressed
   - Any suggestions that were intentionally not applied, with rationale
   - Location of the final document

## Output

- `artifacts/prd-creation/prd-final.md` — Final, polished PRD

## Next Steps

The PRD creation workflow is complete. The final PRD is at `artifacts/prd-creation/prd-final.md`.
