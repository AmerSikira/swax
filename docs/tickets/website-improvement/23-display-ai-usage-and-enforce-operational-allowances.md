## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Show consumption and safely pause further analyses or AI reviews when configured allowances are exhausted.

Covers spec user stories 81, 82, 83, 84.

## Acceptance criteria

- [ ] Provide usage visibility and authorized operational-limit settings using approved units/scope; packages/subscriptions remain deferred.
- [ ] Apply the same allowance/reservation/settlement controls to manual analysis and AI review, with scheduler integration exposed for the later schedule slice.
- [ ] Enforce limits under concurrent requests and workers; handle retries and uncertain external outcomes without silently double-charging or granting unbounded work.
- [ ] Show exhausted/paused notices with recovery information while retaining earlier successful records.
- [ ] Verify allowed/exhausted/recovered workflows in browser and worker profiles and meaningful concurrency/atomicity integration cases against the selected production database.
