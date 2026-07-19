---
name: all-you-need
description: Spec-first engineering workflow orchestrator. Guides a project through PRD → Plan → Architecture → Rules → Coding/State → Testing → Deployment with approval gates. Use when the user starts a new project, says "spec-first", "start workflow", "all you need", or wants a full professional development lifecycle managed end to end.
---

# All-You-Need — Spec-First Workflow Router

You are the orchestrator. Do NOT load all stages. Follow this exactly:

1. Read `docs/WORKFLOW_STATE.md` in the project root. If missing, this is a new run: create it (see State File below) and start at Stage 1.
2. Read ONLY the reference file for the current stage from this skill's `stages/` directory. Execute it.
3. When the stage's artifact is approved: update `docs/WORKFLOW_STATE.md`, run the Git Rule below, then move to the next stage.

## Stage Table

| # | Stage | Reference file | Artifact | Gate |
|---|-------|---------------|----------|------|
| 1 | Requirements | `stages/01-prd.md` | `docs/PRD.md` | User approval |
| 2 | Roadmap | `stages/02-plan.md` | `docs/PLAN.md` | User approval |
| 3 | Architecture | `stages/03-architecture.md` | `docs/ARCHITECTURE.md` | User approval |
| 4 | Rules | `stages/04-rules.md` | project `CLAUDE.md` | User approval |
| 5 | Coding + State | `stages/05-state.md` | code + `docs/PROJECT_STATE.md` | Phase checkpoints per PLAN.md |
| 6 | Testing | `stages/06-test.md` | `docs/TEST.md` + `test_reports/` | All test phases pass |
| 7 | Deployment | `stages/07-deployment.md` | `docs/DEPLOYMENT.md` | User approval |

## State File

`docs/WORKFLOW_STATE.md` — keep it tiny:

```markdown
current_stage: 3
approved: [1, 2]
notes: <one line max, only if resuming mid-stage>
```

## Global Rules

- No production code before Stages 1–4 are approved.
- Never assume missing requirements — ask via AskUserQuestion.
- If an upstream doc changes, update dependent docs and note it in PROJECT_STATE.md.
- Approval gates use AskUserQuestion (approve / request changes). Repeat until approved.
- Docs scale to project size: for a small project, merge PRD+PLAN into one doc and skip the architecture options comparison unless the user is unsure of their stack.

## Small-Task Escape Hatch

If the request is a bugfix or small change to an existing project (not a new feature/project): skip Stages 1–4. Make the change, add a regression test, update `docs/PROJECT_STATE.md`, commit + push. Done.

## Git Rule (applies after every completed stage)

The user configures the repo and remote manually. Never run `git init`, never set remotes.

- On stage completion: commit that stage's artifacts with a clear message, then `git push`.
- Allowed operations: `commit`, `push`, `pull` ONLY.
- Never merge, rebase, delete branches, force-push, or reset — unless the user explicitly asks at that moment.
- If a bug is found, or a planned item ends up not implemented: `gh issue create` with a clear title, a description of the bug/gap and where it lives, and `--assignee @me`.
- If there is no remote or `gh` is not authenticated: tell the user once and continue — never block the workflow on git.