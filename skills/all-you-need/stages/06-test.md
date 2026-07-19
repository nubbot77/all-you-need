# Stage 6 — Testing → docs/TEST.md + test_reports/

## Goal
A written test strategy, executed in three phases, with reports on disk.

## Generate docs/TEST.md

Copy `templates/TEST.template.md`: strategy, scope, unit/integration/e2e plans, regression strategy, performance and security testing (if applicable), coverage goals.

## Execution

Create `test_reports/unit/`, `test_reports/integration/`, `test_reports/e2e/`.

**Token rule: write reports to disk, never read full reports back into context. Work from the test runner's summary output — pass/fail counts and failing test names only.**

### Phase 1 — Unit
Run unit tests. Save report (passed, failed, errors, coverage, missing tests) to `test_reports/unit/`. Fix failures, re-run until stable.

### Phase 2 — Integration
Test APIs, database, auth, services, external integrations. Save to `test_reports/integration/`. Fix, repeat until stable.

### Phase 3 — End-to-End
Test complete user journeys: business logic, UI flows, data persistence, error handling. Save to `test_reports/e2e/`. Fix all critical failures.

## Completion

All three phases pass → update WORKFLOW_STATE.md, commit + push. Any known-but-deferred bug gets a GitHub issue (`gh issue create`, `--assignee @me`). Proceed to Stage 7.