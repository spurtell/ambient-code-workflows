# /speedrun - Run Full Workflow End-to-End

## Purpose

Execute all 6 phases of the PRD creation workflow sequentially with minimal interaction. Only the discovery phase is interactive — all other phases run automatically.

## Process

1. **Phase 1: Discovery** (interactive)

   Run the `/discover` command. Conduct the full interactive discovery session with the user. This is the only interactive phase — gather thorough requirements before proceeding.

2. **Phase 2: Specialist Contributions** (automatic)

   Once discovery is saved, immediately run `/contribute`. Launch all 5 specialist agents in parallel. Wait for all to complete.

3. **Phase 3: Synthesis** (automatic)

   Once all contributions are in, run `/synthesize`. Merge contributions into a unified outline.

4. **Phase 4: Draft** (automatic)

   Once the outline is ready, run `/draft`. Write the full PRD draft.

5. **Phase 5: Specialist Reviews** (automatic)

   Once the draft is complete, run `/review`. Launch all 5 review agents in parallel. Wait for all to complete.

6. **Phase 6: Refinement** (automatic)

   Once all reviews are in, run `/refine`. Ask the user for any final feedback, then produce the final PRD.

## Output

All artifacts from every phase:

- `artifacts/prd-creation/discovery.md`
- `artifacts/prd-creation/contributions/*.md`
- `artifacts/prd-creation/outline.md`
- `artifacts/prd-creation/draft.md`
- `artifacts/prd-creation/reviews/*.md`
- `artifacts/prd-creation/prd-final.md`

## Notes

- Do not skip any phase — each depends on the previous
- Between phases, briefly inform the user what phase is starting next
- If any phase fails, stop and report the error rather than continuing
