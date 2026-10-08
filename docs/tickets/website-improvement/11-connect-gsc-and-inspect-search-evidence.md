## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Connect a project's Search Console site and display trustworthy search-performance evidence.

Covers spec user stories 25, 29.

## Acceptance criteria

- [ ] Provide approved consent/site selection and source collection with source-specific dimensions, meanings, periods, and freshness.
- [ ] Retain project-owned evidence and safe connection state; expose authentication/quota/freshness errors and a functioning reconnect path.
- [ ] Keep GSC measures distinct from GA4 conversion denominators rather than combining incompatible counts.
- [ ] Use deterministic server-side adapter fixtures for provider contracts and browser/feature tests for connect/collect/render/reload, validation recovery, and isolation.
- [ ] Record separate live-provider verification requirements and update source/control coverage.

## Blocked by

- Draft ticket 02: Decide source connections, capture, and freshness
- Draft ticket 07: Create and switch tenant-owned website projects
