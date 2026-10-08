## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Make conversion reports and evaluation outcomes independently reproducible before implementing them.

Decision or verification prerequisite for the product slices.

## Acceptance criteria

- [ ] Verify Fakturax's completed-account-creation tracking when access exists; otherwise record the missing access as a blocker and provide the exact verification steps. A button click must not become the signup success event.
- [ ] Define goal/source mapping, counting unit, eligible denominator, duplicate-event handling, and project time-zone boundaries; support different goals as project configuration.
- [ ] Define before/after windows, minimum evidence, thresholds, unchanged versus inconclusive, traffic/overlap caveats, grouped-change treatment, and evaluation timing/automation.
- [ ] Provide independently calculated fixtures covering all four outcomes and time/evidence boundaries, and a method contract that can later support controlled experiments without building an A/B engine.
- [ ] Obtain recorded approval for business/statistical policies and verified tracking before closing this gate; dependent implementation remains blocked by unresolved decisions.

## Blocked by

- Draft ticket 02: Decide source connections, capture, and freshness
