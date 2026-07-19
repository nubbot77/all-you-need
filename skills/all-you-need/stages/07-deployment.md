# Stage 7 — Deployment → docs/DEPLOYMENT.md

## Goal
The project deployed (or deploy-ready) on the user's platform, with the process documented.

## Process

1. Determine the platform. If Stage 3 (ARCHITECTURE.md) already records one, reuse it — don't re-ask. Otherwise AskUserQuestion: Vercel / Railway / AWS / VPS+Docker / other.
2. Explain the recommended way to deploy THIS project on that platform:
   - Build steps and required config files (Dockerfile, vercel.json, etc.)
   - Environment variables needed (names only — never write secret values into any file)
   - CI/CD hookup (e.g. GitHub Actions → platform), if the user wants it
   - Platform-specific gotchas for this stack (cold starts, file system limits, region, pricing traps)
3. Write the chosen approach into `docs/DEPLOYMENT.md` from `templates/DEPLOYMENT.template.md`, including a step-by-step deploy runbook and a rollback note.
4. If the user wants you to execute the deploy, do only the steps that don't require their credentials; hand them the exact commands for the rest.

## Approval Gate

AskUserQuestion: approve / request changes. On approval: update WORKFLOW_STATE.md (workflow complete), commit + push.

## Workflow Completion Checklist

Done only when: PRD, PLAN, ARCHITECTURE, CLAUDE.md rules, PROJECT_STATE, TEST, DEPLOYMENT docs all exist and match the implementation; unit + integration + e2e tests pass; reports exist in `test_reports/`; everything is committed and pushed.