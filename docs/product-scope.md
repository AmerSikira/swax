# Product scope

The product gathers website evidence, uses AI to recommend improvements, and evaluates results after the website operator implements changes.

## Customers, projects, and expansion

- Support multiple customer organizations and multiple projects from the initial implementation, including customers outside the operator's own organization.
- Each project represents one website and contains its pages, data connections, goals, recommendations, and history.
- Fakturax is the first rollout. Adding Axiom or another customer's website must use the same capabilities without rebuilding them for each project.
- Keep data, connections, recommendations, changes, and results scoped to the appropriate customer and project.
- Goals and success definitions are project configuration. Fakturax initially targets signup conversion, with success defined as completed account creation. Signup-button clicks are intermediate steps.
- Reuse collection, analysis, recommendation, and evaluation capabilities across projects. New source providers extend the shared integration capability.
- The stated roles are superadmin, team owner/admin, and regular user. Detailed permissions and user workflows remain deferred.

## Sources and page scope

- Initial sources are GA4, Google Search Console, and actual page content.
- Discover public pages and let the operator select which pages to analyze.
- Allow manually supplied content for inaccessible pages.
- Continue with available evidence when useful, identify missing or outdated evidence, and withhold unsupported conclusions.
- When completed signups are not tracked, explain what evidence or connection is needed before evaluating signup conversion.

## Project setup and overview

- Use a resumable setup checklist covering the website, goals, brief, sources, pages, and AI access, with readiness and missing items visible.
- Open each project at an overview showing available goal metrics, data issues, top recommendations, and ongoing evaluations, with a prominent Run analysis action.
- Project navigation consists of Overview, Pages & Data, Recommendations, Results, History, and Settings. Project Settings contains the brief, goals, and scheduling configuration; History includes past analyses, decisions, and changes.
- The main journey and screen planning are recorded in [user-journey.md](./user-journey.md).

## AI analysis and recommendations

- Generate several improvement ideas from project evidence and context.
- Present prioritized recommendation cards showing the page, proposed change, supporting evidence, target goal, and reason for priority.
- Make recommendations actionable and explain the strength of their supporting evidence.
- Support on-demand analyses and optional schedules configured per project. Scheduling is disabled until configured.
- Automatically use the team's owner-provided AI key when configured; otherwise use the app's AI key. This routing applies across the team's projects. Package-based access and pricing are deferred.
- Initially support OpenAI and Anthropic through provider adapters producing a shared recommendation format from the same project context and analysis workflow.
- Analyses run in the background with visible progress, clear failure messages, and a retry action. Earlier successful recommendations remain available while a new analysis runs.
- Identify disconnected sources and provide a reconnect action, applying the agreed partial-evidence rules where useful.

## Project context and continuity

- Each project has an editable brief describing its audience, offering, goals, and business constraints.
- Persist history of earlier analyses, recommendations and their disposition, implemented changes and go-live dates, and measured results.
- Retain the project's current state, including ongoing evaluations, open questions, and next steps.
- Continuity belongs to the project and carries across sessions, authorized project members, AI providers, and credential choices.
- Supply relevant brief and history information alongside current evidence for subsequent analyses, so AI can build on previous work and account for ideas already tried or rejected.

## Recommendation and change workflow

- Recommendations have suggested, planned, implemented, postponed, and dismissed states.
- The website operator implements changes and records their go-live dates, with an optional note describing the actual modification.
- Implemented changes have their own records and can link to several recommendations or be recorded without an AI recommendation. Changes applied together can be recorded and evaluated as a combined change.
- Attach evaluation results separately from recommendation progress. Implementation alone does not establish success.
- The rationale for these separate concepts is recorded in [ADR 0001](./adr/0001-separate-recommendations-changes-evaluations.md).

## Evaluation

- The app calculates metrics, comparisons, data-sufficiency checks, and evaluation outcomes in code using explicit, versioned rules.
- Initial evaluations compare goal performance before and after a recorded change.
- Report improved, declined, unchanged, or inconclusive results, accompanied by evidence.
- Show comparison periods, conversion rates, and traffic volume. Explain attribution uncertainty caused by overlapping changes or differences in traffic.
- The same evaluation workflow must accommodate controlled experiments alongside before-and-after comparisons.
- Provide a **Pass the data to AI** button so users can request an AI review of measured data and results. Display the review alongside the calculated results and retain it in project history.
- By default, send the currently selected report or evaluation, its date range, and the relevant project goal, brief, and history.
- AI can propose changes and interpret evidence; measured results remain reproducible from retained inputs and evaluation rules. This decision is recorded in [ADR 0005](./adr/0005-reproducible-evaluations-and-ai-reviews.md).

## AI settings and usage controls

- The team owner manages their AI key in account settings; app credentials are platform-managed. Project settings hold the default AI provider and model, schedules, and project usage limits. Credential ownership is at the team owner or application level; projects and individual team members do not supply separate keys.
- Show AI usage through the app and provide configurable limits for manual and scheduled analyses under either credential option.
- Pause further AI runs and display a clear notice when an allowance is exhausted.
- These controls cover usage through this app. Exact allowances, pricing, and accounting rules remain undecided.
- Current credential routing uses the team owner's configured key, otherwise the app key. Packages and commercial tiers are subsequent work.

## Confirmed technical foundation

- Keep the existing Laravel/Inertia React stack as one Laravel application organized into reusable modules, with background workers for collection and analysis.
- Use a shared tenant database with explicit tenant/project ownership enforced in queries, background work, relationships, and stored results.
- Store the project brief, history, recommendations, changes, and results as durable database records.
- Each analysis records the input versions it used so earlier recommendations remain explainable as website data, briefs, and goals change.
- Supply relevant stored context to the AI on each analysis. Generated summaries can be rebuilt from retained records.
- The technical design and its remaining choices are recorded in [technical-design.md](./technical-design.md).

## Deferred implementation decisions

- Detailed relationships between customer organizations and projects, and role permissions.
- Conversion-rate denominators and goal-to-source mappings.
- Model choices, credential management, and service-provided usage policies. The initial providers are confirmed as OpenAI and Anthropic.
- Scheduled execution permissions, provider/model selection for the effective team-owner or app credentials, handling unusable owner credentials, and changes of team ownership.
- Page discovery and content capture mechanics, evidence freshness rules, and prioritization criteria.
- Evaluation timing, automation, comparison windows, evidence thresholds, and detailed treatment of overlapping changes.
- Storage and retrieval of project context and history.

This records the agreed high-level product scope. Detailed design and implementation remain subsequent work.
