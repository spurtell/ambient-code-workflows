# /assess.full - Comprehensive Feasibility Assessment

## Purpose

Perform a thorough technical feasibility assessment of an RFE including codebase exploration, API verification, and detailed implementation planning. Produces a formal assessment document suitable for stakeholder review.

## Prerequisites

- RFE details available (via JIRA or user description)
- Relevant GitHub repositories identified
- If /assess.start was run, read `artifacts/rfe-feasibility/{RFE-ID}-context.md` for collected inputs

## Process

### Phase 1: Requirements Analysis

1. **Read the RFE thoroughly**
   - If JIRA: use `jira_get_issue` with full field expansion to get description, comments, linked issues
   - Extract: customer name, business need, current workaround, priority, acceptance criteria
   - Use `jira_search` to find related/duplicate issues if applicable

2. **Identify technical requirements**
   - What data needs to be displayed, stored, or processed?
   - What user interactions are required?
   - What system integrations are involved?
   - What are the non-functional requirements (performance, security, accessibility)?

### Phase 2: Frontend/UI Codebase Analysis

3. **Clone and explore the frontend repository**
   - Clone the relevant frontend repo if not already local
   - Use Glob to find relevant components, pages, and patterns
   - Use Grep to search for related features, data models, and API calls
   - Read key files to understand:
     - Component architecture and patterns
     - Data model structures (TypeScript interfaces, etc.)
     - Existing similar features that can serve as implementation templates
     - Extension points (where new code would be added)
     - Filter/search infrastructure if relevant

4. **Document frontend findings**
   - Existing patterns that support the feature
   - Required new components or modifications
   - Data flow from API to UI
   - Include relevant code snippets as examples

### Phase 3: Backend/API Verification

5. **Clone and explore the backend repository** (if applicable)
   - Clone the relevant backend repo
   - Use Grep to find API endpoints, data structures, schemas
   - Read key files to verify:
     - Required API fields exist and are populated
     - Data structures support the needed information
     - RBAC/permissions implications
     - Any API changes that would be needed

6. **Document API findings**
   - Confirmed API fields with structure details
   - Go structs, protobuf definitions, or OpenAPI schemas
   - Example API responses/payloads
   - Integration patterns with existing systems
   - Create a separate API verification document if findings are substantial

### Phase 4: Assessment Document Creation

7. **Write the feasibility assessment** with this structure:

   ```
   # Feasibility Assessment: {RFE-ID}
   # {RFE Title}

   ## Executive Summary
   - One-paragraph overview of the RFE and assessment findings
   - Feasibility: HIGH/MEDIUM/LOW
   - Complexity: LOW/MEDIUM/HIGH
   - Estimated Effort: X-Y story points (X-Y hours)
   - Recommendation: APPROVE / APPROVE WITH CONDITIONS / NEEDS MORE INVESTIGATION / REJECT

   ## 1. Requirements Overview
   ### 1.1 Customer Need
   ### 1.2 Business Context
   ### 1.3 Current Workaround
   ### 1.4 Acceptance Criteria

   ## 2. Technical Analysis
   ### 2.1 Architecture Overview
   (How the relevant system currently works)
   ### 2.2 Frontend Analysis
   (Component structure, existing patterns, extension points)
   ### 2.3 Backend/API Analysis
   (API support, data structures, schemas)
   ### 2.4 Code Examples
   (Relevant snippets from the codebase showing patterns to follow)

   ## 3. Implementation Plan
   ### Phase 1: {Name} (X hours)
   - Task 1
   - Task 2
   ### Phase 2: {Name} (X hours)
   - Task 1
   - Task 2
   ### Phase 3: {Name} (X hours)
   ### Phase 4: {Name} (X hours)

   ## 4. Effort Breakdown
   | Task | Estimate | Complexity |
   |------|----------|------------|
   | ... | X hours | LOW/MED/HIGH |
   | **Total** | **X-Y hours** | |

   ## 5. Risk Assessment
   | Risk | Likelihood | Impact | Mitigation |
   |------|-----------|--------|------------|
   | ... | LOW/MED/HIGH | LOW/MED/HIGH | ... |

   ## 6. Design Recommendations
   (Recommended approach, patterns to follow, UX considerations)

   ## 7. Dependencies and Prerequisites
   (What must be in place before implementation begins)

   ## 8. Success Criteria
   - [ ] Criterion 1
   - [ ] Criterion 2
   - [ ] Criterion 3

   ## 9. Appendix
   ### A. Repositories Analyzed
   ### B. Key Files Referenced
   ### C. Related Issues
   ```

8. **Write API verification document** (if backend analysis was substantial):

   ```
   # Backend API Verification: {RFE-ID}

   ## API Schema
   (Detailed field documentation with types and descriptions)

   ## Data Structures
   (Code snippets from backend source - Go structs, protobuf, etc.)

   ## Integration Patterns
   (How existing features consume this API)

   ## Example Payloads
   (JSON examples of API responses)

   ## Compatibility Notes
   (Kubernetes alignment, versioning, deprecation concerns)
   ```

## Output

- `artifacts/rfe-feasibility/{RFE-ID}-feasibility-assessment.md` - Primary assessment document
- `artifacts/rfe-feasibility/{RFE-ID}-api-verification.md` - API verification (if applicable)

## Success Criteria

After running this command, the assessment should have:
- [ ] All technical unknowns investigated and documented
- [ ] Codebase patterns identified with code examples
- [ ] API support verified (if applicable)
- [ ] Clear implementation plan with phased approach
- [ ] Effort estimated in story points and hours
- [ ] Risks identified with mitigations
- [ ] Actionable recommendation (approve/reject/investigate)

## Next Steps

- Share assessment with stakeholders for review
- Run `/assess.export` to upload to Google Drive
- If approved, use the implementation plan to create JIRA subtasks
