## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Exercise pending-to-completed analysis through actual queue workers without borrowing browser session or prior-job context.

Covers spec user stories 36, 37, 85.

## Acceptance criteria

- [ ] Provide a disposable worker-backed profile using the approved queue runtime, process lifecycle/cleanup, and shared testing-only business clock.
- [ ] Run tenant A then tenant B work through the same long-lived worker, with distinguishable evidence/history and owner/app credentials; assert each rendered result uses only its own scoped inputs.
- [ ] Observe genuine queued/running/completed states through browser/public responses and keep workflow/context/persistence real while external adapters are controlled on the server.
- [ ] Capture server/worker/scheduler logs and diagnostics, exercise the selected production database's relevant constraints, and record executed worker coverage.
- [ ] Show that after-commit work cannot consume missing uncommitted records and verify no duplicate logical result on the approved replay boundary.
