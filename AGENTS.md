# Codex Workflow Contract (Portable)

This workspace is structured so Codex can immediately plan and execute project work.

## Trigger

When the user asks for:
- "프로젝트 계획 시작"
- "plan this project"
- "start implementation from brief"

Codex must run this workflow in order.

## Required Inputs

Read these files first:
1. `docs/project-brief.md`
2. `docs/tech-context.md` (if present)
3. `docs/conventions.md` (if present)
4. `create-prd.md`
5. `generate-tasks.md`

## Workflow

1. Validate context completeness from `docs/project-brief.md`.
2. Ask only essential clarifying questions (3-5 max, options A/B/C/D).
3. Generate PRD using `create-prd.md`.
4. Save PRD as `tasks/prd-[feature-name].md`.
5. Generate parent tasks using `generate-tasks.md`, then wait for user confirmation ("Go").
6. Generate sub-tasks + relevant files, then wait for user confirmation ("Approve files").
7. Save final task list as `tasks/tasks-[feature-name].md`.
8. Start implementation from task `0.0` and mark checkboxes as each sub-task completes.
9. Keep implementation aligned to `docs/conventions.md` and constraints from `docs/project-brief.md`.
10. Log major decisions in `docs/decision-log.md`.

## Execution Rules

- Use small, reviewable changes.
- Include tests for each implementation slice where applicable.
- Never skip updating checkbox progress in `tasks/tasks-[feature-name].md`.
- If blocked, report blocker + propose the smallest unblocking next action.

