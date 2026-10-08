# Technical design

Status: single Laravel application, shared tenant database, durable versioned project context, and initial OpenAI/Anthropic support are confirmed. Remaining model, credential, and execution details are listed below.

## Existing application

The repository is a Laravel React starter using Laravel, Inertia, React, and TypeScript. Application code currently covers authentication, account settings, and a placeholder dashboard. The product's customer/project, evidence, AI, recommendation, change, and evaluation domain still needs to be implemented.

Queue configuration and queue-table migrations already exist. The configured default is the database queue unless overridden by the runtime environment; runtime configuration has not been inspected.

## Confirmed application shape

Keep one Laravel application organized into modules with focused interfaces. Web requests and background workers share the same product code; the frontend presents persisted state and starts work through the backend.

This choice is recorded in [ADR 0002](./adr/0002-modular-laravel-application.md).

| Module | Responsibility behind its interface |
| --- | --- |
| Projects and access | Resolve customer/project ownership, authorize operations, and maintain project configuration. |
| Evidence collection | Collect source-specific metrics and page content, retain provenance and collection periods, and report freshness or failures. |
| Project context | Maintain brief versions and durable project history; assemble relevant context for an analysis. |
| Analysis | Coordinate evidence and context, execute the selected AI configuration, validate output, and persist recommendations and run status. |
| Changes | Record actual website modifications, go-live dates, notes, and links to zero or more recommendations. |
| Evaluation | Assess a recorded change against a goal using a named evaluation method and report evidence and uncertainty. |
| AI access and usage | Resolve the team owner's key or app credentials, enforce usage allowances, and record attempts and usage. |

Use adapters where external behavior actually differs, especially GA4, GSC, and page content collection. Preserve source-specific metric meanings and dimensions while giving callers a consistent way to request evidence and inspect its provenance.

The initial AI providers are OpenAI and Anthropic. Their adapters produce a shared recommendation format and use the same project context and analysis workflow, handling provider-specific credentials, request formats, model capabilities, and response validation. Exact models and supported schema features remain to be selected. Both providers document structured outputs: [OpenAI](https://developers.openai.com/api/docs/guides/structured-outputs) and [Anthropic](https://platform.claude.com/docs/en/build-with-claude/structured-outputs).

## Customer and project isolation

Use a shared database for tenants, with explicit tenant and project ownership on project records. Enforce ownership in queries, cross-record relationships, background jobs, and stored results. AI credentials belong to the team owner or application and are resolved for the project's tenant under the relevant execution permissions.

Every project operation, stored artifact, and queued task must retain the correct customer/project scope. The backend resolves access rather than trusting a project identifier supplied by the frontend. Background work must resolve the intended scope independently of any browser session and must not inherit another job's customer context.

Project history and configuration remain project-owned. Precise membership relationships, superadmin access mechanics, and scheduled execution permissions remain open design choices. The storage decision and trade-off are recorded in [ADR 0004](./adr/0004-shared-tenant-database.md).

## Confirmed durable context and analysis records

Store project configuration, brief versions, evidence collections, analysis runs, recommendation decisions, change records, evaluations, and usage as durable database records.

Each analysis records which goal definition, brief version, evidence collections, and relevant history it used, alongside its provider/model configuration and outputs. Retain the referenced versions or necessary input snapshots so those references remain meaningful after project settings change. Records should reference retained evidence rather than repeatedly copying the entire project history.

Assemble relevant context for each AI request from these records. Generated summaries can help reduce context size, while the underlying facts remain available for rebuilding a summary and explaining a recommendation. Context belongs to the project across users, sessions, providers, and credential choices.

This choice is recorded in [ADR 0003](./adr/0003-durable-versioned-project-context.md).

## Background execution

Create the analysis run and its intended project scope before dispatching background work. Dispatch jobs that depend on new records after the database transaction commits. Collection, analysis, and evaluation should persist progress and errors for the interface, while prior successful results remain accessible.

Retries must preserve the distinction between a logical run and its attempts, avoid duplicate product records, and account for uncertain external outcomes. Scheduling, concurrency, usage reservations, provider timeouts, and reconciliation need detailed design before implementation.

Laravel documents queue workers and transaction-aware dispatch in its official [queue documentation](https://laravel.com/framework/docs/13.x/queues#jobs-and-database-transactions). Worker operation and deployment are described under [running queue workers](https://laravel.com/framework/docs/13.x/queues#running-the-queue-worker).

## Confirmed credential routing

Resolve AI access through the project's team owner: use the owner's configured key, otherwise use the app's key. Apply this rule across the team's projects for authorized member-triggered and scheduled analyses. The team owner manages their key in account settings; app credentials are platform-managed. Package-based access and pricing are deferred. Previously agreed usage visibility and configurable operational limits remain part of the design.

Projects have no keys of their own, and regular team members do not supply separate keys. Provider/model selection for the effective credentials, handling unusable owner keys, scheduled execution permissions, and changes of team ownership remain open. Record the effective provider, model, and credential ownership for each run without including key material in its context or outputs. This ownership decision is recorded in [ADR 0006](./adr/0006-team-owner-and-app-ai-credentials.md).

## Evaluation inputs

The app calculates counts, rates, comparisons, data-sufficiency checks, and evaluation outcomes using explicit, versioned code. AI proposes changes and interprets the recorded measurements; calculated results remain reproducible from retained evidence and rules.

An evaluation identifies the change record, goal definition, measurement source, comparison periods, evidence, and evaluation method. Initial before-and-after comparisons and future controlled experiments use the same product concept with method-specific implementations.

Keep measured counts and rates available alongside any AI explanation. Preserve the metric definition and denominator used in a comparison; changing goal definitions must not silently change historical results. Grouped modifications are evaluated as a combined change, with uncertainty about individual effects retained.

## User-requested AI review

Provide **Pass the data to AI** alongside measured data and results. By default, send the currently selected report or evaluation, its date range, and the relevant project goal, brief, and history. This starts a user-requested AI review under the same context, credential routing, usage accounting, and project isolation as other AI analyses. Retain its input references and response in project history and display the AI interpretation alongside calculated results. Detailed presentation remains open.

The distinction between reproducible evaluations and AI reviews is recorded in [ADR 0005](./adr/0005-reproducible-evaluations-and-ai-reviews.md).

## Next decisions

- Define membership relationships and permission mechanics when the deferred user workflows are addressed.
- Choose supported models and resolve provider matching for team-owner/app credentials, unusable owner keys, scheduled execution permissions, and changes of team ownership.
- Define source-to-goal mapping, evidence retention, and evaluation eligibility.
- Design concrete interfaces, queue orchestration, and the first implementation sequence.
