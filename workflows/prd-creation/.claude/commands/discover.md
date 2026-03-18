# /discover - Interactive Discovery Session

## Purpose

Conduct an interactive discovery session to gather comprehensive requirements for the PRD. This is the foundation for all subsequent phases.

## Prerequisites

- None — this is the first phase of the workflow

## Process

1. **Begin the discovery conversation**

   Act as a senior product manager conducting a discovery session. Your goal is to deeply understand the feature or product being proposed by asking targeted, insightful questions.

   Cover these areas as needed:

   - Problem statement and motivation (what problem, why now, what context)
   - Target users/personas and their pain points
   - Use cases and user stories
   - Business impact and customer value
   - Scope: what's in and what's out (goals and non-goals)
   - Technical constraints or integration requirements
   - Success criteria and how to measure them
   - Risks and concerns
   - Stakeholders and dependencies
   - Timeline or phasing considerations

2. **Ask questions in focused batches**

   - Ask 2-4 questions at a time, grouped by topic. Don't overwhelm with too many at once.
   - Build on previous answers — don't repeat what's already been covered.
   - If an answer is vague, probe deeper before moving on.
   - Be conversational but efficient. Respect the user's time.

3. **Check for supplementary files**

   If the user mentions supplementary context files (research notes, existing docs, workshop notes, etc.), read them and incorporate their content into your understanding. Reference specific details from these files in your follow-up questions.

4. **Conclude discovery**

   When you believe you have sufficient information to write a comprehensive PRD, tell the user that discovery is complete and provide a brief summary of what you've gathered.

5. **Save the transcript**

   Save the complete discovery conversation to `artifacts/prd-creation/discovery.md`. Format it as a readable transcript with clear speaker labels (User/Assistant) and organize by topic area.

## Output

- `artifacts/prd-creation/discovery.md` — Complete discovery transcript

## Important

- Do NOT generate the PRD during discovery. Only gather information.
- Do NOT skip to other phases. Complete discovery thoroughly first.

## Next Steps

After completing discovery, run `/contribute` to launch the 5 specialist agents.
