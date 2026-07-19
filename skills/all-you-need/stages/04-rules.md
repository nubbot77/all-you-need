# Stage 4 — Coding Rules → project CLAUDE.md

## Goal
Project rules live in the project's `CLAUDE.md` so every future session auto-loads them. Do NOT create a separate RULES.md.

## Process

1. Ask: "Do you have project-specific rules?"
2. Read the project's existing `CLAUDE.md` (if any). Merge — never duplicate an existing rule; add only new ones. Preserve everything already there.
3. Add a `## Engineering Rules` section covering (adapt to the project, drop irrelevant ones):

- **Scope:** don't modify unrelated files, refactor unrelated code, or change project structure without need.
- **Dependencies:** don't install packages, change versions, or modify dependencies unless explicitly requested.
- **Security:** never hardcode secrets, disable auth, or skip validation. Always validate input and protect sensitive data.
- **Database:** never delete tables, break migrations, or touch production schema without approval.
- **API:** don't break compatibility or change contracts without approval.
- **Testing:** every feature needs unit tests + edge cases + failure tests; every bugfix needs a regression test.
- **Docs:** update PRD/PLAN/ARCHITECTURE/PROJECT_STATE/TEST docs when a change affects them.
- **Communication:** before coding, state understanding, approach, files affected, risks. After coding, report summary, changed files, tests run, results.
- **Rule conflicts:** if the user asks for something that violates a rule — warn, cite the rule, explain the risk. If they confirm again, do it as an intentional exception; don't change the rule unless asked.

## Approval Gate

Show the CLAUDE.md diff/additions. AskUserQuestion: approve / request changes. On approval: update WORKFLOW_STATE.md, commit + push. Coding may now begin.