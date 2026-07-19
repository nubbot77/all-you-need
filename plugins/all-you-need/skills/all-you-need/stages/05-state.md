# Stage 5 — Coding + docs/PROJECT_STATE.md

## Goal
Execute PLAN.md phase by phase while maintaining PROJECT_STATE.md — a bounded snapshot of the codebase that any model can read instead of scanning the repo.

## PROJECT_STATE.md rules

- It is a **current-state snapshot, not a changelog**. Git history records changes; this file records what IS.
- Create it from `templates/PROJECT_STATE.template.md` at the start of coding (analyze the repo if code already exists).
- After every meaningful change: **rewrite the affected sections in place**. Never append dated entries. If a section grows long or stale, rewrite it shorter.
- Must always answer: what exists, how it's organized, what decisions were made, what's broken, what's pending.

## Coding loop (per phase in PLAN.md)

1. Announce phase, tasks, files affected, risks.
2. Implement. Use sub-agents for independent modules where PLAN.md marks them parallel; sequential for anything sharing files.
3. Run the phase checkpoint: existing tests still pass, new behavior works.
4. Update PROJECT_STATE.md sections touched by this phase.
5. Commit + push (Git Rule). If a bug was found and deferred, or a planned item was cut: `gh issue create` with description, `--assignee @me`.
6. Next phase.

When all phases are checkpointed, update WORKFLOW_STATE.md and go to Stage 6.