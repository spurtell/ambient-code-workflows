# CLAUDE.md — PRD Creation Workflow

## Behavioral Guidelines

You are executing a multi-agent PRD creation workflow. Follow these rules throughout.

### Session State

- All workflow state is persisted as markdown files in `artifacts/prd-creation/`
- Discovery transcript: `artifacts/prd-creation/discovery.md`
- Specialist contributions: `artifacts/prd-creation/contributions/<agent-key>.md`
- Synthesized outline: `artifacts/prd-creation/outline.md`
- Draft PRD: `artifacts/prd-creation/draft.md`
- Specialist reviews: `artifacts/prd-creation/reviews/<agent-key>.md`
- Final PRD: `artifacts/prd-creation/prd-final.md`

### Agent Keys

Five specialist agents contribute and review: `pm`, `ux_researcher`, `engineer`, `ux_designer`, `tech_writer`

### Parallel Execution

Steps 2 (contributions) and 5 (reviews) MUST launch all 5 agents as parallel Agent tool calls in a single message. Each agent uses `subagent_type: "general-purpose"`. Each agent reads the required input files, generates its output, and writes its result to the appropriate artifact file.

### Phase Ordering

Execute phases in order: discovery -> contribute -> synthesize -> draft -> review -> refine. Each phase depends on artifacts from the previous phase. Do not skip phases.

### PRD Template

The PRD template at `templates/prd-template.md` defines the expected document structure. Specialist agents should reference it when generating contributions and the draft should follow its structure.

### Supplementary Files

If the user provides supplementary context files (research notes, existing docs, etc.), read them and include their content as context for all specialist agents.

### Discovery Phase

- Ask 2-4 questions at a time, grouped by topic
- Build on previous answers — don't repeat covered ground
- When sufficient information is gathered, save the full transcript to `artifacts/prd-creation/discovery.md`
- Do NOT generate the PRD during discovery — only gather information

### Writing Standards

- Use clear, precise language appropriate for a technical audience
- Mark uncertain areas with [TBD] markers
- Replace all template placeholder text with actual content
- Maintain professional formatting with proper markdown
