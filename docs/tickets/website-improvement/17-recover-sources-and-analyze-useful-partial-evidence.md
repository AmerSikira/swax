## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Make source failures and stale/missing evidence visible while allowing supported partial analysis.

Covers spec user stories 9, 11, 29, 30, 31, 32, 33, 34.

## Acceptance criteria

- [ ] Display missing/unavailable/outdated evidence and the specific correction or reconnect action in Pages & Data and run readiness.
- [ ] Let a user reconnect a failed source, recollect evidence, and see readiness recover without losing prior evidence or successful ideas.
- [ ] Include selected available GA4/GSC/page evidence with its periods/freshness/provenance in analysis inputs; run usefully when approved sufficiency permits.
- [ ] Withhold conversion conclusions when tracking or evidence is inadequate; distinguish analysis eligibility from numerical evaluation eligibility.
- [ ] Verify partial-source analysis, reconnect recovery, stale evidence/time boundaries, and per-source errors with browser/worker/feature journeys using controlled provider seams.

## Blocked by

- Draft ticket 10: Connect GA4 and inspect goal evidence
- Draft ticket 11: Connect GSC and inspect search evidence
- Draft ticket 12: Discover and capture public website pages
- Draft ticket 14: Run a queued OpenAI analysis and inspect recommendations
