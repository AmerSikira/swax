## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Start a background analysis of selected manual page evidence and receive several actionable recommendation cards.

Covers spec user stories 11, 31, 32, 35, 36, 37, 39, 43, 44, 45, 46, 47, 73, 80, 85.

## Acceptance criteria

- [ ] Persist the scoped logical run and immutable input references before after-commit dispatch; use the shared workflow and approved OpenAI adapter/model.
- [ ] Show pending/progress/completion and preserve earlier successful results while new work runs; include brief, goal, selected pages, and relevant available history.
- [ ] Validate several cards containing page/change/goal/evidence/priority reason/evidence strength; withhold unsupported claims and reject invalid/refused/incomplete provider output.
- [ ] Record effective provider/model/credential source and usage facts without secrets; tenant/member-triggered execution uses the owner/app rule.
- [ ] Prove real request-to-persisted-result behavior using controlled server-side AI responses with feature/adapter tests and an initial browser journey; subsequent worker profile establishes independent-process behavior.

## Blocked by

- Draft ticket 08: Edit versioned project goals and business briefs
- Draft ticket 09: Select pages and supply manual page content
- Draft ticket 13: Manage owner credentials and project AI defaults
