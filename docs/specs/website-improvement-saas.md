# Multi-tenant website improvement SaaS

## Problem Statement

Website operators have analytics, search-performance data, and website content in separate places. They need help identifying useful improvements, deciding what to implement, and understanding what happened after changes went live. Repeated AI analyses also need the business context and history of previous ideas, decisions, and results.

Fakturax is the first rollout, with completed account creation as the initial success event and signup conversion as the initial goal. The product must support other websites, customers, and goals from its first implementation. Adding Axiom or another customer's website must use the same capabilities, with independent project data and context.

## Solution

Build a multi-tenant SaaS in which each project represents one website. Collect evidence from GA4, Google Search Console, and page content; combine it with an editable project brief and retained history; and use AI to produce several prioritized, actionable recommendations.

The operator implements chosen changes outside the tool and records what changed and when. The application calculates measurements and evaluation outcomes using explicit, versioned rules, displaying evidence and uncertainty. A **Pass the data to AI** button lets users request an additional interpretation of selected measurements or an evaluation. Retain that interpretation in project history alongside the calculated results.

Use the team owner's configured AI key across the team's projects. When no owner key is configured, use the app's key. Initially support OpenAI and Anthropic through a shared analysis workflow and provider-specific adapters. Packages and commercial tiers are deferred.

Support on-demand and optional scheduled background analyses, persistent project context, source reconnection, retry feedback, usage visibility, and configurable operational limits. Every workflow must preserve the correct tenant and project ownership.

## User Stories

1. As a team owner, I want multiple projects in my tenant, so that I can improve several websites using the same product.
2. As a team owner, I want each project to represent one website, so that its evidence, goals, recommendations, and results stay organized together.
3. As a team owner, I want to add Fakturax, Axiom, or another website through the same setup flow, so that onboarding another project requires configuration rather than a separate implementation.
4. As an authorized team member, I want to select a project from a projects list, so that I can work on the intended website.
5. As an authorized team member, I want my access to follow tenant and project authorization, so that I can work with the projects available to me.
6. As a team owner, I want project data kept within its tenant and project ownership scope, so that another customer or project cannot access it accidentally.
7. As a superadmin, I want to administer the SaaS across tenants through explicitly authorized operations, so that I can manage and support the application.
8. As a team owner, I want a resumable setup checklist, so that I can configure a project over several sessions.
9. As a team owner, I want the checklist to cover the website, goals, brief, sources, pages, and AI readiness, so that I know what the project needs before analysis.
10. As an authorized team member, I want completed and missing setup items shown, so that I can identify the next useful setup action.
11. As an authorized team member, I want useful analysis to proceed with partial setup when sufficient evidence exists, so that optional missing sources do not unnecessarily prevent progress.
12. As an authorized team member, I want to land on a project overview, so that I can quickly understand the current state of the website's improvement work.
13. As an authorized team member, I want the overview to show available goal metrics, so that I can understand current performance.
14. As an authorized team member, I want the overview to show data issues and ongoing evaluations, so that I can see what requires attention or more evidence.
15. As an authorized team member, I want top recommendations and a prominent Run analysis action, so that I can move directly from the overview to useful work.
16. As an authorized team member, I want consistent Overview, Pages & Data, Recommendations, Results, History, and Settings sections, so that the same navigation works across projects.
17. As a team owner, I want configurable project goals, so that websites with different business outcomes can use the same product.
18. As a team owner, I want a goal's measurement definition connected to an appropriate source, so that its results reflect the intended outcome.
19. As a Fakturax operator, I want completed account creation to count as a successful signup, so that signup-button clicks are tracked as intermediate behavior rather than the final outcome.
20. As an authorized team member, I want the goal metric's counting unit and denominator to be identifiable, so that I can understand what a reported conversion rate means.
21. As a team owner, I want an editable project brief covering audience, offering, goals, and constraints, so that AI recommendations reflect the business context.
22. As a team owner, I want to state constraints such as preserving current pricing, so that proposed improvements account for those restrictions.
23. As an authorized team member, I want earlier analyses to retain the brief and goal versions they used, so that subsequent edits do not obscure why an idea was proposed.
24. As a team owner, I want to connect GA4 to a project, so that website behavior and tracked goal evidence can inform analysis.
25. As a team owner, I want to connect Google Search Console to a project, so that search-performance evidence can inform analysis.
26. As an authorized team member, I want the actual page content considered alongside analytics, so that recommendations address the website visitors see.
27. As an authorized team member, I want public pages discovered and selectable, so that I can choose the scope of analysis.
28. As an authorized team member, I want to supply page content manually when a page is inaccessible, so that the project can still analyze that content.
29. As an authorized team member, I want evidence to show its source, collection period, and freshness, so that I can assess whether it supports a recommendation or evaluation.
30. As an authorized team member, I want missing, unavailable, and outdated evidence identified, so that I can understand the limitations of an analysis.
31. As an authorized team member, I want useful analysis to continue with available evidence, so that a disconnected source does not necessarily stop all work.
32. As an authorized team member, I want unsupported conclusions withheld, so that missing evidence is represented honestly.
33. As an authorized team member, I want a disconnected source identified with a reconnect action, so that I can restore its data collection.
34. As a Fakturax operator, I want missing completed-signup tracking explained, so that I know what must be connected before signup conversion can be evaluated.
35. As an authorized team member, I want to start an analysis on demand, so that I can request improvement ideas when I need them.
36. As an authorized team member, I want analysis to run in the background, so that I can continue working while it processes.
37. As an authorized team member, I want visible run progress and a recorded completion status, so that I can distinguish ongoing work from available results.
38. As an authorized team member, I want clear analysis failure feedback and a retry action, so that I can recover from unsuccessful runs.
39. As an authorized team member, I want earlier successful recommendations retained during new or failed analyses, so that useful work remains accessible.
40. As a team owner, I want optional schedules configured per project, so that analyses can run at a cadence appropriate to that website.
41. As a team owner, I want scheduling disabled until configured, so that automated AI usage starts deliberately.
42. As an authorized team member, I want manual and scheduled analyses to use the same project workflow, so that their context and results are consistent.
43. As an authorized team member, I want several improvement ideas per analysis, so that I can choose useful next steps.
44. As an authorized team member, I want prioritized recommendation cards, so that I can identify which ideas to consider first.
45. As an authorized team member, I want each recommendation to identify its page, proposed change, target goal, and supporting evidence, so that I understand the suggested action.
46. As an authorized team member, I want the reason for priority and strength of supporting evidence explained, so that I can judge how much weight to give an idea.
47. As an authorized team member, I want AI to consider the project brief and relevant history, so that new ideas account for business constraints and previous work.
48. As an authorized team member, I want previously tried, rejected, and postponed ideas included in relevant history, so that AI can explain a repeated idea or build on earlier decisions.
49. As an authorized team member, I want recommendations to have suggested, planned, implemented, postponed, and dismissed states, so that I can track decisions and progress.
50. As an authorized team member, I want to record the actual implemented modification and its go-live date, so that evaluation is tied to what happened on the website.
51. As an authorized team member, I want optional implementation notes, so that I can explain differences between the suggestion and the deployed change.
52. As an authorized team member, I want a separate change record linked to one or more recommendations, so that actual website work can group related ideas.
53. As an authorized team member, I want to record independently chosen changes without an AI recommendation, so that project history reflects all relevant improvement work.
54. As an authorized team member, I want changes applied together to be recorded as a combined change, so that their combined result can be evaluated honestly.
55. As an authorized team member, I want implementation progress and evaluation outcomes shown separately, so that an implemented idea is not automatically treated as successful.
56. As an authorized team member, I want initial evaluations to compare goal performance before and after a recorded change, so that I can understand the observed difference.
57. As an authorized team member, I want comparison periods, conversion rates, and traffic volume shown, so that I can inspect the basis of an evaluation.
58. As an authorized team member, I want improved, declined, unchanged, or inconclusive outcomes accompanied by evidence, so that the result is understandable.
59. As an authorized team member, I want data-sufficiency checks governed by explicit rules, so that inadequate evidence is not turned into a confident outcome.
60. As an authorized team member, I want overlapping changes and traffic differences reflected in the explanation of uncertainty, so that observed movement is not automatically presented as a proven causal effect.
61. As an authorized team member, I want grouped changes evaluated as a combined change, so that their individual effects are not claimed without supporting evidence.
62. As an authorized team member, I want calculated results reproducible from retained evidence, goal definitions, and evaluation rules, so that model or settings changes do not silently rewrite earlier measurements.
63. As an authorized team member, I want the evaluation workflow able to accommodate controlled-experiment results, so that stronger evaluation methods can use the same product concepts as capabilities expand.
64. As an authorized team member, I want a Pass the data to AI button beside measured data and results, so that I can request an additional interpretation.
65. As an authorized team member, I want that AI review to use the currently selected report or evaluation and its date range by default, so that the interpretation addresses the data I am viewing.
66. As an authorized team member, I want the selected data accompanied by the relevant goal, brief, and history, so that AI can interpret it in context.
67. As an authorized team member, I want the AI review displayed alongside calculated results, so that I can inspect both the measurements and the interpretation.
68. As an authorized team member, I want AI reviews retained with their input references in project history, so that subsequent analysis can build on them.
69. As an authorized team member, I want history to include analyses, recommendations, decisions, changes, results, and open questions, so that the project records its progress over time.
70. As an authorized team member, I want current state to include ongoing evaluations and next steps, so that I can resume work after a gap.
71. As an authorized team member, I want project continuity across sessions and authorized members, so that knowledge is available to the team.
72. As an authorized team member, I want project continuity across AI providers and credential changes, so that changing AI access does not reset the project.
73. As an authorized team member, I want each analysis to record the goal, brief, evidence, and relevant history versions it used, so that its recommendations remain explainable.
74. As an authorized team member, I want generated summaries rebuildable from retained records, so that project continuity does not depend on an opaque summary alone.
75. As a team owner, I want to configure my AI key in account settings, so that the team's projects can use owner-provided AI access.
76. As a team owner, I want my configured key used across the team's projects and authorized member-triggered or scheduled runs, so that AI access is centrally managed for the team.
77. As a team owner, I want the app key used when I have no configured key, so that the team can use AI before supplying its own credentials.
78. As an authorized team member, I want team-owner or app credentials resolved automatically, so that I can use AI without managing a separate member or project key.
79. As a team owner, I want initial OpenAI and Anthropic support through the shared workflow, so that provider-specific integrations do not require separate project features.
80. As an authorized team member, I want the effective provider, model, and credential source identifiable for a run, so that I can understand how its AI output was generated.
81. As a team owner, I want AI usage through the app visible, so that I can understand the consumption attributable to project work.
82. As a team owner, I want configurable operational limits covering manual and scheduled analyses and AI reviews, so that automated usage can be controlled.
83. As an authorized team member, I want further AI runs paused with a clear notice when an allowance is exhausted, so that I understand why work has stopped.
84. As a team owner, I want current AI access independent of commercial package configuration, so that the initial product follows the owner-key-or-app-key rule while packages are deferred.
85. As an authorized team member, I want background jobs to retain the correct tenant and project context, so that other tenants' data, credentials, or history do not enter my results.
86. As an authorized team member, I want retry behavior to preserve completed project records and show a meaningful run history, so that recovery does not silently duplicate recommendations or confuse outcomes.

## Implementation Decisions

### Application structure and modules

- Keep the existing Laravel, Inertia, React, and TypeScript stack as one Laravel application. Background workers share the application's product code.
- Organize reusable modules around Projects and access, Evidence collection, Project context, Analysis, Changes, Evaluation, and AI access and usage. Their interfaces should expose meaningful product operations and keep provider-specific implementation details local.
- Reuse the current authentication and account-settings foundation. The existing application is a starter with a placeholder dashboard; project and analytics capabilities still need implementation.
- Build shared customer/project capabilities from the beginning. Fakturax-specific goal configuration is data rather than a separate workflow.
- Respect the recorded ADRs: separate recommendations, changes, and evaluations; keep one modular Laravel application; retain versioned project context; use shared tenant storage; calculate reproducible evaluations with separate AI reviews; and resolve credentials through the team owner and application.

### Ownership and durable relationships

- Use a shared database with explicit tenant and project ownership. Enforce access and ownership consistency in application queries, relationships, background work, and stored results.
- A project represents one website and owns its page scope, source configuration, goal definitions, brief, evidence, analysis runs, recommendations, change records, evaluations, AI reviews, and history.
- Preserve customer/project scope in all background tasks. Resolve access on the backend rather than trusting an identifier supplied by the frontend. Job execution must not inherit a different tenant's context from an earlier job.
- Persist team ownership and the credential source used by each AI run. The team owner's key and the app key are the two credential sources; projects and regular members do not supply separate keys.
- Store durable records for project configuration, versioned briefs and goals, collected evidence, analysis runs and attempts, recommendations and their disposition, change records and recommendation links, evaluations, AI reviews, schedules, and usage. Final table layouts and membership cardinalities remain implementation-design work.
- Change records can link to zero, one, or several recommendations. Record modifications deployed together as a combined change where appropriate. Evaluations refer to actual changes and goal definitions independently of recommendation status.
- Keep input versions or retained snapshots available so historical analysis and evaluation references remain meaningful. Reuse references rather than copying the complete history into every run.

### Evidence and provider interfaces

- Initially integrate GA4, Google Search Console, and page content collection. Source adapters support a common evidence-collection workflow while preserving source-specific identifiers, meanings, dimensions, provenance, and collection periods.
- Discover public pages, let operators choose scope, and support manually provided content for inaccessible pages.
- Identify missing, unavailable, and outdated evidence. Continue when the available evidence supports useful analysis; withhold unsupported conclusions and indicate the next setup or reconnection action.
- Completed account creation is the initial Fakturax success event. The actual source event, counting unit, denominator, and goal mapping must be verified and defined before implementing conversion evaluation.
- Initially support OpenAI and Anthropic adapters with a shared recommendation-output contract. The contract covers the page, proposed change, supporting evidence, goal, priority reason, and strength of evidence; exact schemas and supported models remain to be selected.
- Validate AI output before turning it into product records. Provider-specific handling must account for unsupported output formats, incomplete responses, refusals, and failures. These conditions must not present an unsuccessful run as a completed recommendation set.

### Credential routing and usage

- Resolve AI access through the project's team owner. Use the configured owner key when present, otherwise the app key. Apply this ownership rule to authorized manual analyses, scheduled analyses, and user-requested AI reviews.
- The owner manages their key in account settings; app credentials are platform-managed. Project configuration can include model/provider defaults but does not contain an API key.
- Record effective provider, model, and credential ownership without including secret key material in project briefs, AI context, history output, or client-facing run data.
- Preserve the confirmed routing rule when designing provider compatibility. The rejected per-member credential model and the unconfirmed personal-provider-precedence proposal are not implementation decisions.
- Handling an unusable configured owner key, provider mismatch, owner replacement, and scheduled execution permissions is unresolved. The confirmed fallback condition is absence of an owner key; other failure policies require an explicit implementation decision.
- Show in-app AI usage and enforce configurable operational limits. When an allowance is exhausted, pause further AI runs and show a clear notice. Exact accounting units, limits, concurrency enforcement, and reconciliation of uncertain provider outcomes remain to be designed.
- Packages, subscriptions, commercial tiers, and package-based credential routing are deferred.

### Context and background workflow

- Each analysis receives relevant current evidence, the project brief, goal definitions, and history of earlier analyses, decisions, changes, and results. Include relevant ongoing evaluations, open questions, and next steps.
- Persist the input references, effective AI configuration, and output of each analysis run. Provider or credential changes preserve the project's context.
- Generated summaries may reduce context size, but retained records remain available for rebuilding summaries and explaining decisions. Detailed retention and retrieval policies remain open.
- Support on-demand runs and optional per-project schedules. Scheduling starts disabled until configured.
- Persist an analysis run and its project context before dispatching background work that depends on it; dispatch after the corresponding transaction commits.
- Expose progress, completion, failure feedback, retry actions, and source reconnect actions. Preserve earlier successful recommendations while later work runs or fails.
- Treat a logical run and its execution attempts distinctly. Retry and concurrency behavior must avoid duplicate product records and preserve traceability of uncertain external outcomes. Queue configuration and exact coordination rules remain implementation-design work.

### Measurements and AI reviews

- Calculate counts, rates, comparisons, data-sufficiency checks, and evaluation outcomes in code using explicit, versioned rules.
- Initial evaluation uses before-and-after comparisons against a defined goal. Retain its change record, goal definition, measurement source, counting unit, denominator, periods, evidence, evaluation method, and rule version.
- Outcomes are improved, declined, unchanged, or inconclusive, supported by comparison data and uncertainty. Numerical thresholds and statistical rules are unresolved; an implementer must not invent them as if approved.
- Show comparison periods, conversion rates, and traffic volume. Explain limitations introduced by traffic differences, missing tracking, and overlapping changes. Combined changes are evaluated as combined changes.
- Keep the evaluation concept extensible to controlled experiments. Initial implementation of experiment assignment, automated website variants, or an A/B testing engine is outside this spec.
- Provide **Pass the data to AI** beside measurements and evaluations. Its default input is the selected report or evaluation, selected date range, and relevant project goal, brief, and history.
- Run the AI review through the same tenant scope, context, credential-routing, and usage controls as other analyses. Retain its input references and response in project history and display the interpretation alongside calculated results.

### Screens and interactions

- Use a projects list for creating or selecting website projects and a resumable setup checklist for website, goals, brief, sources, pages, and AI readiness.
- Open projects at an overview containing available goal metrics, data issues, top recommendations, ongoing evaluations, and a prominent Run analysis action.
- Provide Overview, Pages & Data, Recommendations, Results, History, and Settings sections with the agreed responsibilities.
- Settings contains the brief, goals, project AI defaults, schedules, and usage limits. Owner credentials remain in owner account settings and app credentials at application level.
- Recommendation cards expose suggested, planned, implemented, postponed, and dismissed disposition states. Recording implementation captures the actual modification, go-live date, and optional notes, through an independent change record.
- Results exposes measurements and evaluations, including AI review. History exposes earlier analyses, decisions, changes, outcomes, reviews, and current open questions.
- Precise layouts, independent-change entry points, transition rules, and error-message details remain implementation design rather than settled product requirements.

## Testing Decisions

### Testing seams adapted from Fakturax

- Use Playwright with Chromium as the primary E2E seam for rendered controls and user journeys against a real, isolated Laravel application. Submit real forms, follow navigation, reload persisted state, and assert meaningful product outcomes. Public application requests may complement browser assertions for direct-object authorization.
- Preserve the authenticated Laravel feature-test seam for backend authorization, request validation, database relationships, and application outcomes. Use focused module tests for numerical evaluation boundaries and provider contracts. Browser journeys complement these established tests.
- Prepare deterministic fixtures for at least two tenants and multiple projects within one tenant, with distinguishable evidence, history, roles, owner keys, and app-key fallback cases. Fixtures are test-only, guarded, and isolated from developer or production data.
- At external-provider seams, substitute source and AI responses on the server so tests are deterministic and do not spend provider credits. Keep the real project authorization, context assembly, credential routing, workflow, and persistence active. Browser-intercepted fake analysis responses must not bypass the application workflow.
- Add focused adapter contract tests only for provider-specific translation, output validation, authentication selection, refusals, incomplete responses, and errors that the main workflow fixtures cannot exercise. These are internal external-provider seams, not additional product interfaces.
- Maintain a deterministic UI/workflow E2E profile and a focused worker-backed profile. The latter runs actual queue workers and the normal scheduler path to prove progress, retry/replay behavior, due runs, and tenant-context isolation between jobs. Synchronous queues and dispatch assertions alone cannot establish those behaviors.
- Exercise reproducible evaluation rules through the Evaluation module's interface using fixed evidence and goal definitions once those rules are specified. Use focused tests for meaningful boundary cases that are cumbersome to express through the main request workflow.
- Maintain a control-to-journey coverage map that distinguishes planned, policy-dependent, and implemented coverage. Update it with every browser-visible workflow change; a rendered route alone is supplemental smoke coverage.
- Test browser-visible outcomes through rendered state and public application responses. Use database access for fixture preparation and backend/integration assertions, rather than as proof that a browser control worked.

### E2E execution and diagnostics

- Carry over Fakturax's initial Chromium profile with one worker, disabled full parallelism, zero automatic retries, and focused-only tests rejected. Initially use a 45-second test timeout, 10-second action/assertion timeout, and 20-second navigation timeout, adjusted deliberately when justified by actual behavior.
- Fail journeys on unexpected uncaught page errors, unexpected console errors, and HTTP 5xx responses. Any expected framework transport exception must be narrow and verified against this application; billing-preview exceptions from the reference project are not applicable.
- Prefer accessible locators and Swax-specific helpers. Delay a real request only when necessary to observe a pending control, letting the unchanged request reach the application.
- Use a testing-only business clock for date-sensitive evaluation periods, source freshness, and due schedules while preserving browser/session transport time. Restore state after each scenario and share the intended clock with worker/scheduler processes.
- Provide an initially manual GitHub Actions E2E workflow with an optional branch/tag/commit target, read-only repository permissions, a disposable runtime, and cleanup of its own application/worker processes. Preserve the existing automatic backend/lint/type-check CI.
- Retain HTML, JSON, and JUnit reports; run transcripts; runtime/commit/lockfile context; application/server/worker logs; and failure traces, screenshots, and videos. Always upload diagnostics, using a project-specific artifact name and initial 14-day retention. Keep credential secrets out of reports and logs.
- Use the current project's build command and supported PHP/Node runtime, with a compatible locked Playwright dependency. Billing fixtures, pricing/subscription journeys, source-project runtime pins, and invoice-specific time reruns are replaced with project-domain fixtures and boundaries.
- Routine fixtures require no live Google consent, production analytics access, or paid AI calls. Provider connectivity, sustained concurrency, production database behavior, and deployment infrastructure require separate integration verification.

### What makes a good test

- Test external behavior and product invariants, not method-call counts, private helpers, directory layouts, or implementation-shaped snapshots.
- Assert concrete outcomes: the correct tenant's evidence and credential source, retained history and input versions, understandable readiness and errors, usable recommendations, accurately linked change records, and reproducible evaluation results.
- Cover the behavior that would break for another tenant, another project, another source, or the second AI provider. A test passing only for a hard-coded Fakturax configuration is insufficient.
- Keep numerical fixtures explicit and independent of the implementation being tested. Do not derive expected values by calling the same production calculation.
- Verify meaningful failure and uncertainty cases as well as the happy path. Provider output fixtures must preserve the distinction between missing evidence, invalid output, failed execution, and valid inconclusive evaluation.
- Retain existing authentication and account-settings regression coverage as the product integrates with the starter.

### Modules and behaviors to cover

- **Projects and access:** same-tenant multiple-project behavior; cross-tenant and cross-project reads/writes; authorized superadmin operations; invalid ownership relationships; and background execution without browser session context.
- **Evidence collection:** GA4, GSC, and page-content adapter results; source provenance and time ranges; missing or stale data; selected-page scope; manual content; and disconnected-source recovery.
- **Project context:** brief/goal edits with historical input references preserved; relevant earlier decisions and results; continuity across actors and providers; reproducible summary rebuilding; and isolation from unrelated projects.
- **Analysis:** several validated recommendation cards; common output behavior for both initial providers; progress and failure; useful partial-evidence runs; retained previous successful results; retry behavior; and separate execution attempts.
- **AI access and usage:** owner key present versus absent; team-wide routing regardless of triggering member; accurate effective credential references; no key material in project output; allowed versus exhausted operational usage; and credential-error policies once decided.
- **Changes:** one or several linked recommendations; independent changes; grouped modifications; actual implementation notes and dates; and separation between disposition and measured success.
- **Evaluation:** configured numerator/denominator and time ranges; versioned rules; insufficient tracking or evidence; overlapping changes and traffic caveats; unchanged versus inconclusive semantics once specified; and method-specific behavior through the shared evaluation concept.
- **AI review:** selected report/evaluation and date-range scope; relevant brief, goal, and history; the same owner/app routing and usage rules; retained input/output history; and calculated results preserved alongside interpretation.
- **Scheduling and recovery:** explicit schedule configuration; equivalent scoped workflow for manual and scheduled runs; progress and retry feedback; reconnect behavior; and pause-on-allowance-exhaustion.

### Existing prior art

The starter's dashboard feature tests exercise guest redirects and authenticated page access. Authentication tests submit requests and assert authentication, redirects, rate limits, and session behavior. Profile-update tests combine authenticated requests, validation assertions, redirects, and refreshed database records. These tests use PHPUnit-style Laravel test classes with database refresh and model factories. The existing test environment uses an in-memory SQLite database and synchronous queue execution.

Build on this request-and-persisted-outcome pattern. There is currently no product-domain workflow, adapter contract suite, or browser suite in Swax. Once the production database engine is selected, verify important database constraints and concurrency behavior against that engine in appropriate integration coverage.

The additional E2E prior art is Fakturax at commit bfbacf01267c7aa2fe25892ce94ec4e998c48255: its Playwright configuration, operating guide, control-to-test coverage map, diagnostics fixture, guarded seeding, tenant-isolation and validation/recovery journeys, test-only clock, and manual workflow. Adapt the operating pattern to Swax's projects, owner/app credentials, analysis, history, changes, evaluations, and worker execution.

## Out of Scope

- Commercial packages, subscriptions, payment processing, tier-based allowances, and package-based routing.
- Separate API keys for projects or regular team members.
- Automatic editing, deploying, or publishing changes to customer websites.
- Initial implementation of Hotjar or other additional data providers beyond GA4, GSC, and page content; the shared integration design must remain extensible.
- Initial AI providers beyond OpenAI and Anthropic; the shared analysis/context design must remain extensible.
- Model fine-tuning as the mechanism for project continuity. Continuity is supplied from retained project records and relevant context.
- An automated A/B testing engine, visitor assignment, or website variant deployment. Accommodating controlled evaluations in the domain remains required.
- A promise that before-and-after observations prove causation or that AI can evaluate untracked goal outcomes.
- A Fakturax-only application, single-customer shortcuts, or separate copies of the product workflow for each website.
- Expanding detailed user management, invitation flows, and granular role design during this spec's synthesis. The existing stated roles and required tenant/project isolation are retained; concrete permission decisions are dependencies for affected implementation work.
- Implementing the SaaS or decomposing it into implementation tickets as part of this to-spec operation.

## Further Notes

### Confirmed understanding

This spec synthesizes the current conversation, domain glossary, product scope, screen journey, technical design, and ADRs 0001 through 0006. The most recent credential clarification governs: the team owner's configured key is used across the team, otherwise the app key. Earlier per-user or project-key interpretations are superseded.

Fakturax is the initial rollout and completed signup conversion is its initial goal. Multi-tenant, multi-project use and configurable goals are requirements of the first implementation.

### Open decisions and discovery dependencies

The following are explicitly unresolved. Resolve them in design or focused discovery work before assigning affected implementation tickets; this spec does not silently choose values or policies:

1. Database engine, production queue driver, worker deployment, and production verification environment.
2. Tenant membership/cardinality, exact regular-user permissions, superadmin access mechanics, and changes of team ownership.
3. Supported AI models, model/provider selection when owner credentials differ from project defaults, unusable-owner-key behavior, and scheduled execution permissions.
4. Actual Fakturax signup tracking, the goal-to-source mapping, event/visitor counting semantics, eligible conversion denominator, and relevant time-zone boundaries.
5. Evaluation comparison windows, minimum evidence, numerical and statistical thresholds, unchanged/inconclusive distinctions, and detailed treatment of overlapping changes.
6. Evaluation timing and automation after change recording; analysis scheduling alone does not settle evaluation scheduling.
7. Source authentication and connection setup, provider quotas, page discovery and capture mechanics, and data freshness rules.
8. Retention of evidence, input versions, and history; context selection and summary rebuilding; and deletion semantics that preserve intended traceability.
9. Usage units and operational limits, accounting for concurrent runs, provider pricing if money-based limits are used, and reconciliation after uncertain external outcomes.
10. Concrete module interfaces, run/attempt coordination, recommendation disposition transitions, prioritization criteria, and detailed screen forms and recovery behavior.

### Implementation handoff

The user confirmed the testing plan and requested adaptation of Fakturax's E2E approach. The Testing Decisions section records that direction; the companion E2E strategy and coverage map distinguish planned journeys from implemented coverage. Feature implementation has not started.

GitHub Issues in AmerSikira/swax is the selected tracker. Publish this spec as the parent issue and implementation tickets as sub-issues, with native blocking relationships and the ready-for-agent label. Resolve the discovery dependencies through explicit decision gates before assigning the affected implementation work. The label is a workflow instruction and does not settle unresolved policies.
