# Stage 3 — Architecture → docs/ARCHITECTURE.md

## Goal
A production-grade architecture the user has consciously chosen.

## Process

1. Ask (AskUserQuestion, batch related choices) about: languages, frameworks, database, cloud/deployment platform, auth, storage, cache, messaging, monitoring, CI/CD. Skip categories that obviously don't apply to the project.
2. If the user is unsure of their stack:
   - Generate 2–3 architecture options. Each: tech stack, design sketch, advantages, disadvantages, scalability, complexity, cost, best-fit scenarios.
   - If the user proposed their own stack too, compare it against your options and explain trade-offs.
   - Let the user choose via AskUserQuestion.
3. If the user knows their stack, don't run the options comparison — just validate for obvious mismatches and flag them.

Record the chosen deployment platform explicitly — Stage 7 reuses it.

## Generate docs/ARCHITECTURE.md

Copy `templates/ARCHITECTURE.template.md` and fill it. Depth scales with project size: a solo tool doesn't need disaster-recovery planning; a SaaS does.

## Approval Gate

AskUserQuestion: approve / request changes. Iterate until approved. On approval: update WORKFLOW_STATE.md, commit + push.