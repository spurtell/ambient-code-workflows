# /assess.quick - Quick Feasibility Scan

## Purpose

Perform a rapid feasibility scan of an RFE without deep codebase analysis. Produces a concise assessment covering completeness, blockers, and rough sizing in ~15-30 minutes.

## Prerequisites

- RFE details available (via JIRA or user description)
- If /assess.start was run, read `artifacts/rfe-feasibility/{RFE-ID}-context.md` for collected inputs

## Process

1. **RFE Completeness Check**
   Evaluate whether the RFE has sufficient information:
   - Clear problem statement? (YES/NO)
   - Defined acceptance criteria? (YES/NO)
   - Customer/business justification? (YES/NO)
   - Priority assigned? (YES/NO)
   - Related issues or dependencies noted? (YES/NO)
   - Flag any critical gaps that would block implementation

2. **Technical Feasibility Scan**
   Based on the RFE description (without deep code analysis):
   - Is this technically possible with the current architecture?
   - Are there obvious blockers (missing APIs, platform limitations, incompatible patterns)?
   - Does this require new infrastructure or can it extend existing systems?
   - Are there known similar implementations to reference?
   - Any security, performance, or scalability concerns?

3. **Rough Sizing**
   Provide an estimated range:
   - Story points (e.g., 1-2, 3-5, 8-13, 13+)
   - T-shirt size (XS, S, M, L, XL)
   - Rough effort in hours/days
   - Confidence level in the estimate (HIGH/MEDIUM/LOW)

4. **Quick Verdict**
   Deliver ratings:
   - **Feasibility**: HIGH / MEDIUM / LOW
   - **Complexity**: LOW / MEDIUM / HIGH
   - **Risk**: LOW / MEDIUM / HIGH
   - **Recommendation**: APPROVE / APPROVE WITH CONDITIONS / NEEDS MORE INVESTIGATION / REJECT
   - If "NEEDS MORE INVESTIGATION", recommend running /assess.full

5. **Write Quick Assessment**
   Create the output document with the following structure:

   ```
   # Quick Feasibility Assessment: {RFE-ID}

   ## RFE Summary
   (1-2 sentence summary of the request)

   ## Completeness Check
   (Table of YES/NO for each criterion, notes on gaps)

   ## Technical Feasibility
   (Brief analysis of feasibility, blockers, and concerns)

   ## Sizing Estimate
   | Metric | Estimate |
   |--------|----------|
   | Story Points | X-Y |
   | T-Shirt Size | M |
   | Effort | X-Y days |
   | Confidence | MEDIUM |

   ## Verdict
   | Rating | Value |
   |--------|-------|
   | Feasibility | HIGH |
   | Complexity | LOW |
   | Risk | LOW |
   | Recommendation | APPROVE |

   ## Notes
   (Any caveats, assumptions, or recommendations)
   ```

## Output

- `artifacts/rfe-feasibility/{RFE-ID}-quick-assessment.md`

## Next Steps

- If the quick assessment recommends further investigation, run `/assess.full`
- If ready to share, run `/assess.export` to upload to Google Drive
