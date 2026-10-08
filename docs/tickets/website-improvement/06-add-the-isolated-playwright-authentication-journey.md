## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Run a real authenticated browser journey locally and in a manual GitHub Actions workflow using the adapted Fakturax pattern.

Decision or verification prerequisite for the product slices.

## Acceptance criteria

- [ ] Exercise guest redirect, invalid/valid login, logout, and existing account-settings behavior against an isolated real application with guarded deterministic test fixtures.
- [ ] Use the project's supported runtime/build and locked Playwright/Chromium dependency: one worker, full parallelism disabled, zero automatic retries, forbid focused-only tests, and the documented initial timeouts.
- [ ] Fail on unexpected page errors, console errors, and HTTP 5xx; retain failure trace/screenshots/video with HTML, JSON, JUnit, transcripts, and runtime/commit/lockfile/application logs.
- [ ] Provide a manual workflow with optional target ref, read-only permissions, disposable state, cleanup, always-upload diagnostics, and 14-day artifact retention; preserve automatic existing checks.
- [ ] Implement a test-only business-clock facility that preserves real session/transport time and can be shared with workers; mark only executed authentication coverage as implemented.

## Blocked by

- Draft ticket 01: Decide tenancy, authorization, and runtime contracts
