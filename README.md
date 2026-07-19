# all-you-need

A spec-first engineering workflow orchestrator for [Claude Code](https://claude.com/claude-code). It guides a project through the full professional development lifecycle — no code before the specs are approved.

```
Idea → PRD → Plan → Architecture → Rules → Code → Test → Deploy
```

## Why

AI agents jump straight to code and guess at requirements. This skill forces the workflow a senior engineer would follow: interview first, document decisions, gate each stage on your approval, keep a bounded state file so any model can resume the project without re-scanning the repo.

## Install

```
/plugin marketplace add nubbot77/all-you-need
/plugin install all-you-need@all-you-need
```

Then in any project, say **"start workflow"** or invoke `/all-you-need`.

## Stages

| # | Stage | Produces | Gate |
|---|-------|----------|------|
| 1 | Requirements interview | `docs/PRD.md` | Your approval |
| 2 | Phased roadmap | `docs/PLAN.md` | Your approval |
| 3 | Architecture (with options if unsure) | `docs/ARCHITECTURE.md` | Your approval |
| 4 | Coding rules | project `CLAUDE.md` | Your approval |
| 5 | Coding + living state snapshot | code + `docs/PROJECT_STATE.md` | Phase checkpoints |
| 6 | Unit → integration → e2e testing | `docs/TEST.md` + `test_reports/` | All tests pass |
| 7 | Deployment for your platform | `docs/DEPLOYMENT.md` | Your approval |

## Design

- **Token-efficient:** thin router `SKILL.md`; only the active stage's instructions are ever loaded into context.
- **Resumable:** `docs/WORKFLOW_STATE.md` tracks the current stage — new sessions pick up where you left off.
- **State snapshot, not changelog:** `PROJECT_STATE.md` is rewritten in place; git history handles the past.
- **Small-task escape hatch:** bugfixes skip the ceremony — change, regression test, state update, done.
- **Git-safe:** commits and pushes after each approved stage; never merges, rebases, or deletes without an explicit ask. Found bugs become GitHub issues automatically.

## Requirements

- Claude Code
- Optional: `grill-with-docs` skill for a sharper requirements interview (falls back to built-in questions)
- Optional: `gh` CLI authenticated, for automatic issue creation

## License

MIT
