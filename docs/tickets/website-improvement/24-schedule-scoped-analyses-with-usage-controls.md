## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Let owners enable per-project schedules and run due analyses through the same workflow as manual work.

Covers spec user stories 40, 41, 42, 76, 82, 85.

## Acceptance criteria

- [ ] Keep scheduling disabled initially; provide authorized cadence/time-zone configuration and clear enable/disable state.
- [ ] Use the normal scheduler path and scoped queue pipeline with approved execution permissions, owner/app routing, input context, progress, and history.
- [ ] Apply current allowance rules; due work pauses clearly on exhaustion or approved permission/credential failure and follows the approved recovery policy.
- [ ] Verify due/not-due/disabled/date-boundary cases with the shared business clock and actual scheduler/worker processes.
- [ ] Demonstrate different projects/tenants due in the same worker without context or key leakage and update schedules/time-boundary coverage.
