# Stage 2 — Development Roadmap → docs/PLAN.md

## Goal
A phased, production-level roadmap derived from the approved PRD.

## Process

1. Ask: "Do you already have an implementation plan?"
   - Yes → collect it, improve it, convert it into the structure below.
   - No → generate the plan from the PRD.
2. The plan must:
   - Divide development into phases with a goal per phase.
   - Separate independent modules (parallelizable, can go to sub-agents) from dependent modules (sequential).
   - Develop modules that touch the same files incrementally, never in parallel.
   - Put a testing checkpoint after each phase: verify new work didn't break existing features.
   - Include rollback notes for risky phases.

## Generate docs/PLAN.md

Copy `templates/PLAN.template.md` and fill it. For a small project, keep it to one phase list — don't manufacture phases.

## Approval Gate

AskUserQuestion: approve / request changes. Iterate until approved. On approval: update WORKFLOW_STATE.md, commit + push.