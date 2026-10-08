## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Let users choose analysis pages and provide durable content for inaccessible pages.

Covers spec user stories 26, 28, 29.

## Acceptance criteria

- [ ] Create/select project-owned pages and save manual content with provenance, capture time, and an explicit manual-source indicator.
- [ ] Persist page scope and content across reloads; changing a page/content version preserves earlier retained inputs.
- [ ] Show useful validation and unavailable-content states and keep arbitrary page identifiers scoped to the selected project.
- [ ] Demonstrate two independent projects with different selected pages/content through browser and feature tests; update Pages & Data coverage.

## Blocked by

- Draft ticket 02: Decide source connections, capture, and freshness
- Draft ticket 05: Decide context retention and recommendation lifecycle
- Draft ticket 07: Create and switch tenant-owned website projects
