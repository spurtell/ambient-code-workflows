# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Repository Purpose

This repository contains workflow definitions for the Ambient Code Platform (ACP). Workflows are automatically discovered by the platform from the `workflows/` directory — no registration needed. Changes pushed to GitHub are live after a ~5-minute cache expiry.

## Architecture

Each workflow is a self-contained directory under `workflows/` with an `.ambient/ambient.json` config file (the only ACP-specific requirement). Workflows leverage the Claude Code extension system: commands, skills, subagents, hooks, and MCP. The platform fetches workflows dynamically from GitHub at runtime.

**Key relationship**: `systemPrompt` in ambient.json defines *what the workflow does* (phases, commands, outputs). An optional per-workflow `CLAUDE.md` defines *how Claude should behave* while doing it (conventions, agent usage rules).

## Available Workflows

- `workflows/bugfix/` — 5-phase bug resolution (reproduce, diagnose, fix, test, document)
- `workflows/triage/` — Issue backlog triage with HTML reports and bulk operation scripts
- `workflows/spec-kit/` — Spec-driven development (specify, plan, tasks, implement)
- `workflows/prd-rfe-workflow/` — PRD creation and RFE breakdown
- `workflows/amber-interview/` — Guided user feedback collection
- `workflows/claude-md-generator/` — CLAUDE.md generation
- `workflows/template-workflow/` — Starter template for new workflows

## Repository-Level Skills

Two skills exist at the repo root for workflow authoring:

| Skill | Location | Purpose |
|-------|----------|---------|
| `workflow-creator` | `.claude/skills/workflow-creator/SKILL.md` | Create new workflows from scratch |
| `workflow-editor` | `.claude/skills/workflow-editor/SKILL.md` | Modify existing workflows safely |

Always use the appropriate skill rather than making ad-hoc changes.

## Validation

There is no build system, test suite, or linter. After editing any `ambient.json`:

- Verify valid JSON (no trailing commas, proper quoting)
- Confirm all 4 required fields exist: `name`, `description`, `systemPrompt`, `startupPrompt`
- Check that commands referenced in `systemPrompt` have corresponding `.claude/commands/*.md` files
- Ensure `results` glob patterns match paths mentioned in `systemPrompt`

## Key Reference Documents

- `WORKFLOW_DEVELOPMENT_GUIDE.md` — Complete development guide with examples
- `AMBIENT_JSON_SCHEMA.md` — ambient.json field reference (5 fields: name, description, systemPrompt, startupPrompt, results)
- `WORKSPACE_NAVIGATION_GUIDELINES.md` — File navigation best practices for systemPrompts

## PR Workflow

- Push to a personal fork, not directly to main
- Submit PRs as drafts first
- Add review changes as new commits (no amending/rebasing)
- Test workflows via ACP's "Custom Workflow..." feature before merging
