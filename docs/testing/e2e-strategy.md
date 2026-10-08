# E2E strategy for Swax

Status: testing design adapted from Fakturax for this project's spec. The harness and product journeys are implementation work; the coverage map records planned coverage until executable tests exist.

## Reference and scope

Reviewed Fakturax at commit `bfbacf01267c7aa2fe25892ce94ec4e998c48255`. Its [E2E operating guide](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/tests/e2e/README.md), [Playwright configuration](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/playwright.config.ts), [automatic diagnostics fixture](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/tests/e2e/fixtures.ts), and [manual workflow](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/.github/workflows/e2e.yml) provide the operating pattern.

Swax uses that pattern for website improvement: projects, evidence, analyses, recommendations, actual changes, evaluations, AI reviews, and team-owned AI access. Its coverage map is [e2e-coverage.md](./e2e-coverage.md).

## Assertion seams

- Use Playwright against the rendered application as the primary E2E assertion seam. Fill real forms, follow navigation, and assert meaningful results after reload or a new session.
- Use accessible labels, roles, and names, with deliberate stable test selectors where an accessible locator is insufficient. Build helpers around Swax's own controls and copy, rather than Fakturax's invoice labels and routes.
- Public application requests may complement browser interactions to assert forbidden direct-object reads or writes. Obtain identifiers through visible links or public responses, then check the corresponding application endpoint.
- Prepare initial data through guarded seeders, but prove browser-visible behavior through UI or public application responses. Database assertions remain in Laravel feature/integration tests.
- Keep real authorization, tenant/project resolution, credential routing, context assembly, persistence, and evaluation active. Substitute GA4, GSC, page-origin, and AI traffic at server-side external-provider seams.
- Avoid browser-intercepted fake analysis responses that bypass Laravel. A delayed real browser request can make pending controls observable while still allowing the unchanged request to reach the application.
- Preserve Laravel feature tests for backend authorization, source contracts, numerical evaluation boundaries, and database constraints. Browser coverage complements these tests rather than reproducing every numerical case.

This adapts Fakturax's [tenant-isolation journey](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/tests/e2e/tenant-isolation.spec.ts) and [validation/recovery journeys](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/tests/e2e/validation-and-resilience.spec.ts) to Swax's ownership and workflow concepts.

## Deterministic fixtures

Use a disposable testing database with explicit fixtures. The seeder and any test-only controls must require a testing environment and an explicitly isolated runtime. Use fake credentials and source responses; routine E2E runs require no production analytics access or paid AI calls.

Prepare at least:

- Tenant A with a team owner, authorized member, and two projects with distinguishable pages, goals, evidence, briefs, recommendations, and history.
- Tenant B with its own owner/member and unrelated project records to exercise cross-tenant access.
- A superadmin for explicitly authorized application-wide operations once the permission rules are defined.
- An owner-key configuration and an owner-without-key configuration to prove owner-key versus app-key routing. Both keys are identifiable test fakes.
- OpenAI and Anthropic response cases that satisfy the common output contract, plus incomplete, refused, malformed, and unavailable responses.
- Fresh, stale, unavailable, and incomplete source evidence, including an untracked goal case.
- Independent changes and changes linked to several recommendations, with recorded go-live dates and prior input versions.
- Fixed counts, periods, and goal definitions with independently specified expected metrics. Classification fixtures depend on the evaluation rules that remain to be designed.
- Ready, pending, completed, failed, and allowance-exhausted run cases with realistic persisted context.

Tests must not depend on another test's mutations. Give each scenario its own mutable records or deliberately reset the disposable fixtures at a safe point with workers stopped. Use identifiable names and stable source fixture IDs to make isolation failures diagnosable.

Fakturax's [guarded E2E seeder](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/database/seeders/E2ETestSeeder.php) is the reference pattern; its billing-domain records are replaced with Swax's project-domain fixtures.

## Two execution profiles

### UI and workflow profile

Run the built application on a loopback URL with disposable database, storage, sessions, caches, application logs, and captured test mail. Use deterministic server-side external adapters. Synchronous job execution may support ordinary form and completed-result journeys, but this profile does not prove queued progress, worker isolation, or scheduled execution.

Carry over these initial Playwright settings from the reference configuration:

- Chromium as the initial browser.
- One worker and disabled full parallelism while fixtures and test clocks are shared.
- Zero automatic retries, so an unstable first attempt remains visible.
- Reject focused-only tests.
- Initial test timeout of 45 seconds, assertion/action timeout of 10 seconds, and navigation timeout of 20 seconds; adjust deliberately if measured behavior requires it.
- Retain traces, screenshots, and videos on failure.

Use Swax's existing build command and supported runtime versions. The committed Composer dependencies require PHP 8.4.1 or newer; CI uses PHP 8.4 and Node 22. Install a locked compatible Playwright dependency during harness implementation. Fakturax's dependency versions, language-specific selectors, and feature suite are reference details rather than Swax configuration.

### Worker-backed profile

Run the Laravel app and an actual queue worker against the same isolated runtime, with the same external-provider fixtures. The profile must exercise the real dispatch and execution path for background analysis, AI review where queued, and scheduled work. The browser remains the assertion seam for user-visible progress and outcomes.

- Start work through the UI and observe meaningful pending/running and completed states.
- Process Tenant A and Tenant B jobs with the same worker process to reveal retained tenant-context leaks.
- Exercise failed-provider recovery and a retry, then assert one logical result and a meaningful attempt history through the app.
- Exercise owner-key/app-key resolution for member-triggered and scheduled work using identifiable fake provider outputs or a narrowly scoped test-only outbound-provider transcript.
- Advance time and invoke the normal scheduler entry point to trigger due work; observe results through the application.
- Exercise allowance exhaustion and pending-submit/replay protection using the agreed implementation policies.

An outbound-provider transcript, if needed, is limited to testing and records provider, redacted credential identity, project reference, and non-secret request metadata. It must never become a production debug endpoint or log real credentials. Public UI/results remain the proof of product behavior.

This profile verifies actual queued execution. Sustained load, transaction lock races, distributed scheduling, and production worker infrastructure need separate production-like integration checks once their design is selected.

## Time-sensitive scenarios

Adapt the [test-only Fakturax clock](https://github.com/AmerSikira/fakturax/blob/bfbacf01267c7aa2fe25892ce94ec4e998c48255/tests/e2e/clock.php) idea to evaluation windows, evidence freshness, and due analysis schedules. Freeze application business time while preserving browser/session transport time. Restore clock state after every scenario, and apply the same business clock to worker and scheduler processes.

Once date and evaluation policies are defined, include boundary fixtures for comparison periods, go-live instants, project time zones, evidence freshness, and schedules becoming due. The invoice-history month-end rerun and subscription-expiry logic from Fakturax are replaced with these project-specific checks.

## Diagnostics and evidence

Adopt the automatic diagnostic fixture: fail on unexpected uncaught page errors, unexpected console errors, and HTTP 5xx responses, including any additional pages or contexts opened by a journey.

Recognized framework transport behavior needs a narrow, demonstrably valid exception. For example, an Inertia external redirect should be recognized by the expected request/response semantics. Do not copy a blanket console-message allowlist or Fakturax's invoice-preview sandbox exception.

Publish HTML, JSON, and JUnit reports; a complete test transcript; relevant application, server, and worker logs; and failure traces, screenshots, and videos. Capture test mail only for journeys that exercise an existing email flow. Exclude secret key material from diagnostic fixtures and artifacts.

Record the checked-out commit, requested target ref, workflow/run/attempt, installed runtime and browser versions, lockfile hashes, test profile, and worker/retry/timeout settings. Provide pass/fail/skipped counts and reproduction commands in the run summary. If setup fails before Playwright starts, preserve setup logs and identify that failure distinctly.

## CI and local operation

Follow Fakturax's manual-workflow pattern initially, with an optional branch/tag/commit target and read-only repository permissions. Keep the existing automatic Laravel/lint/type-check CI. The manual E2E workflow should support the UI profile and worker-backed profile, record exactly which ref it tests, and always upload diagnostics. Use a Swax artifact name and the reference's 14-day retention as the initial policy.

The runner owns its temporary runtime and server/worker/scheduler processes. Clean up only those processes and that runtime on success or failure. Migrations and reseeding operate on the explicit disposable database. Existing developer or production databases and long-lived services are outside the runner's ownership.

After harness implementation, document focused runs, complete profile runs, browser installation, fixture initialization, and how to inspect reports. Keep commands aligned with the actual package scripts and CI runner rather than documenting commands that do not exist yet.

## Maintaining executable coverage

For each new or changed browser-visible workflow, add the smallest meaningful journey, assert the persisted/public outcome, and update the coverage map with the implementing test and current status. Page-render smoke checks supplement interaction tests.

Run the focused journey first, then the relevant complete profile. Coverage may be marked implemented only when its test exists and has passed; record planned, policy-dependent, and implemented coverage distinctly. Keep permissions, measurement thresholds, key-error behavior, and scheduling policies explicitly unresolved until their design work is complete.
