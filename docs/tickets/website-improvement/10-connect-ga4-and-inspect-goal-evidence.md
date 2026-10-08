## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Connect a project's GA4 property and display source-backed goal evidence with identifiable counting semantics.

Covers spec user stories 18, 19, 20, 24, 29, 34.

## Acceptance criteria

- [ ] Provide the approved secure connection/consent/property-selection flow and collect GA4 evidence through a server-side adapter.
- [ ] Display metric definitions, numerator/denominator, period, freshness, and provenance; explicitly explain absent completed-signup tracking and the required correction.
- [ ] Retain evidence versions for later reports/analyses, scope connections and fetched data correctly, and keep OAuth tokens out of browser responses/logs.
- [ ] Expose connection/error/reconnect states and validate provider translation, quota/auth failures, counting semantics, and period boundaries with deterministic adapter fixtures.
- [ ] Verify connect/select/collect/render/reload and unauthorized cross-project access through the real application; record separate live connectivity verification requirements.
