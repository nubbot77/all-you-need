# Stage 1 — Requirements Discovery → docs/PRD.md

## Goal
Fully understand the project before anything is designed or built.

## Process

1. Ask the user: "Explain your project idea — the problem, goals, users, and expected outcome. If you have a written doc, share it instead."
2. Run the `grill-with-docs` skill on whatever they supply:
   - Idea described in chat → grill that idea.
   - Document provided → grill that document.
   The grilling output is the raw material for the PRD.
3. If `grill-with-docs` is unavailable, run the interview yourself. Cover: problem, users, features, requirements, constraints, business logic, expected behavior, edge cases, future plans. Ask follow-ups until nothing important is ambiguous.
4. Summarize your understanding back to the user and confirm it before writing the PRD.

## Generate docs/PRD.md

Copy `templates/PRD.template.md` from this skill and fill every section. Delete sections that genuinely don't apply rather than leaving placeholders.

## Approval Gate

Show the PRD. Use AskUserQuestion: approve / request changes. Apply changes and re-ask until approved. Do not proceed to Stage 2 without approval.

On approval: update WORKFLOW_STATE.md, commit + push per the Git Rule.