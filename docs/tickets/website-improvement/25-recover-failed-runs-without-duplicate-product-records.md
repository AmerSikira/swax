## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Provide understandable retries and meaningful attempt history while preserving earlier successful work.

Covers spec user stories 38, 39, 86.

## Acceptance criteria

- [ ] Show source/provider/refusal/incomplete/timeout failures and permitted retry actions for logical runs and AI reviews.
- [ ] Apply approved attempt coordination and replay/idempotency policy; repeated clicks, stale submissions, worker redelivery, and uncertain external outcomes preserve one intended logical operation.
- [ ] Retain prior successful recommendations, reviews, and results; expose meaningful attempt/usage history without secrets.
- [ ] Verify delayed real submissions and pending controls without replacing browser responses, plus failure/recovery and repeat worker delivery using controlled external adapters.
- [ ] Cover owner-key/provider errors according to recorded policy and document separate live-provider/concurrency verification limits.

## Blocked by

- Draft ticket 23: Display AI usage and enforce operational allowances
