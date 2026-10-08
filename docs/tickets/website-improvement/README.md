# Website improvement ticket breakdown

Status: **draft awaiting breakdown approval**. These are publication bodies, not published GitHub implementation issues. The source is [GitHub spec #1](https://github.com/AmerSikira/swax/issues/1) and its [repository copy](../../specs/website-improvement-saas.md); GitHub publication will make each ticket its sub-issue and set native blocking edges.

Tickets 01–05 are explicit decision gates required by the spec's unresolved dependencies. They deliver reviewed contracts and independently verifiable examples rather than product code. They close only after their outstanding business decisions and access requirements are resolved. Tickets 06 and 15 deliver working browser/worker verification journeys. Product tickets cut through persistence, authorization, application operations, UI, and meaningful tests; the starter needs no wide prefactor.

A blocker means work needed before the slice can be completed and verified. Work the unblocked frontier; later ticket numbers do not imply a linear chain. Every browser-visible slice updates the control coverage map with actual test evidence. All initial stories are assigned below; retaining a mapping does not claim implementation coverage.

| Draft | Title                                                                                                                              | Blocked by     | What it delivers                                                                                                             |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 01    | [Decide tenancy, authorization, and runtime contracts](01-decide-tenancy-authorization-and-runtime-contracts.md)                   | None           | Settle the access and deployment contract before tenant-owned workflows are implemented.                                     |
| 02    | [Decide source connections, capture, and freshness](02-decide-source-connections-capture-and-freshness.md)                         | None           | Define how projects acquire trustworthy GA4, GSC, and page evidence.                                                         |
| 03    | [Decide signup measurement and evaluation rules](03-decide-signup-measurement-and-evaluation-rules.md)                             | 02             | Make conversion reports and evaluation outcomes independently reproducible before implementing them.                         |
| 04    | [Decide AI execution, credential, and usage policies](04-decide-ai-execution-credential-and-usage-policies.md)                     | None           | Freeze the provider and execution rules needed for predictable owner-key-or-app-key AI access.                               |
| 05    | [Decide context retention and recommendation lifecycle](05-decide-context-retention-and-recommendation-lifecycle.md)               | None           | Define how project knowledge stays explainable and how recommendation decisions evolve.                                      |
| 06    | [Add the isolated Playwright authentication journey](06-add-the-isolated-playwright-authentication-journey.md)                     | 01             | Run a real authenticated browser journey locally and in a manual GitHub Actions workflow using the adapted Fakturax pattern. |
| 07    | [Create and switch tenant-owned website projects](07-create-and-switch-tenant-owned-website-projects.md)                           | 06             | Let owners create website projects and authorized users select them, with explicit superadmin access and isolation.          |
| 08    | [Edit versioned project goals and business briefs](08-edit-versioned-project-goals-and-business-briefs.md)                         | 03, 05, 07     | Configure each website's goals, audience, offering, and constraints while retaining historical versions.                     |
| 09    | [Select pages and supply manual page content](09-select-pages-and-supply-manual-page-content.md)                                   | 02, 05, 07     | Let users choose analysis pages and provide durable content for inaccessible pages.                                          |
| 10    | [Connect GA4 and inspect goal evidence](10-connect-ga4-and-inspect-goal-evidence.md)                                               | 08             | Connect a project's GA4 property and display source-backed goal evidence with identifiable counting semantics.               |
| 11    | [Connect GSC and inspect search evidence](11-connect-gsc-and-inspect-search-evidence.md)                                           | 02, 07         | Connect a project's Search Console site and display trustworthy search-performance evidence.                                 |
| 12    | [Discover and capture public website pages](12-discover-and-capture-public-website-pages.md)                                       | 09             | Discover selectable public pages and retain their content as analysis evidence.                                              |
| 13    | [Manage owner credentials and project AI defaults](13-manage-owner-credentials-and-project-ai-defaults.md)                         | 04, 07         | Let the team owner manage their AI key in account settings while projects configure provider/model defaults.                 |
| 14    | [Run a queued OpenAI analysis and inspect recommendations](14-run-a-queued-openai-analysis-and-inspect-recommendations.md)         | 08, 09, 13     | Start a background analysis of selected manual page evidence and receive several actionable recommendation cards.            |
| 15    | [Verify analysis with a real worker and shared business clock](15-verify-analysis-with-a-real-worker-and-shared-business-clock.md) | 14             | Exercise pending-to-completed analysis through actual queue workers without borrowing browser session or prior-job context.  |
| 16    | [Run the shared analysis workflow through Anthropic](16-run-the-shared-analysis-workflow-through-anthropic.md)                     | 14             | Switch providers and produce equivalent recommendation records without resetting project context.                            |
| 17    | [Recover sources and analyze useful partial evidence](17-recover-sources-and-analyze-useful-partial-evidence.md)                   | 10, 11, 12, 14 | Make source failures and stale/missing evidence visible while allowing supported partial analysis.                           |
| 18    | [Track recommendation decisions and implementation intent](18-track-recommendation-decisions-and-implementation-intent.md)         | 14             | Let users plan, postpone, dismiss, and inspect recommendations with durable decisions.                                       |
| 19    | [Record independent and grouped implemented changes](19-record-independent-and-grouped-implemented-changes.md)                     | 18             | Record what actually went live, when, and which zero, one, or several recommendations it implements.                         |
| 20    | [Calculate reproducible before-and-after results](20-calculate-reproducible-before-and-after-results.md)                           | 10, 19         | Evaluate recorded changes against a configured goal and show measurements, outcomes, and uncertainty.                        |
| 21    | [Pass selected reports or evaluations to AI](21-pass-selected-reports-or-evaluations-to-ai.md)                                     | 16, 20         | Request and retain an AI interpretation beside the exact measured data the user selected.                                    |
| 22    | [Resume project work through history and rebuilt context](22-resume-project-work-through-history-and-rebuilt-context.md)           | 21             | Make prior ideas, decisions, changes, results, reviews, and next steps usable across sessions and providers.                 |
| 23    | [Display AI usage and enforce operational allowances](23-display-ai-usage-and-enforce-operational-allowances.md)                   | 15, 21         | Show consumption and safely pause further analyses or AI reviews when configured allowances are exhausted.                   |
| 24    | [Schedule scoped analyses with usage controls](24-schedule-scoped-analyses-with-usage-controls.md)                                 | 17, 23         | Let owners enable per-project schedules and run due analyses through the same workflow as manual work.                       |
| 25    | [Recover failed runs without duplicate product records](25-recover-failed-runs-without-duplicate-product-records.md)               | 23             | Provide understandable retries and meaningful attempt history while preserving earlier successful work.                      |
| 26    | [Resume project setup and show analysis readiness](26-resume-project-setup-and-show-analysis-readiness.md)                         | 17             | Offer a persisted checklist that guides project setup without demanding every optional source.                               |
| 27    | [Complete the project overview and navigation](27-complete-the-project-overview-and-navigation.md)                                 | 22, 24, 26     | Open projects on a useful overview that connects measurements, issues, recommendations, active evaluations, and analysis.    |
| 28    | [Validate Fakturax and a second independent website](28-validate-fakturax-and-a-second-independent-website.md)                     | 25, 27         | Prove the agreed complete improvement loop works through ordinary configuration on more than one website.                    |

## Story coverage

- Ticket 07: stories 1, 2, 3, 4, 5, 6, 7, 16.
- Ticket 08: stories 17, 18, 19, 20, 21, 22, 23.
- Ticket 09: stories 26, 28, 29.
- Ticket 10: stories 18, 19, 20, 24, 29, 34.
- Ticket 11: stories 25, 29.
- Ticket 12: stories 26, 27, 29.
- Ticket 13: stories 75, 76, 77, 78, 79, 80, 84.
- Ticket 14: stories 11, 31, 32, 35, 36, 37, 39, 43, 44, 45, 46, 47, 73, 80, 85.
- Ticket 15: stories 36, 37, 85.
- Ticket 16: stories 72, 79.
- Ticket 17: stories 9, 11, 29, 30, 31, 32, 33, 34.
- Ticket 18: stories 44, 45, 46, 48, 49, 55.
- Ticket 19: stories 49, 50, 51, 52, 53, 54, 55.
- Ticket 20: stories 55, 56, 57, 58, 59, 60, 61, 62, 63.
- Ticket 21: stories 64, 65, 66, 67, 68.
- Ticket 22: stories 23, 47, 48, 68, 69, 70, 71, 72, 73, 74.
- Ticket 23: stories 81, 82, 83, 84.
- Ticket 24: stories 40, 41, 42, 76, 82, 85.
- Ticket 25: stories 38, 39, 86.
- Ticket 26: stories 8, 9, 10, 11.
- Ticket 27: stories 12, 13, 14, 15, 16, 70.
- Ticket 28: stories 1, 3, 19, 85.

## Approval and publication

Review granularity, whether each blocking edge is necessary, and any desired merges/splits before publishing. The manifest records source bodies, dependencies, story mapping, and published identifiers so publication can resume without duplicate issues. Keep dependency links native on GitHub; retain a parent reference in every child body and a text fallback if the native API is unavailable. Preserve the parent issue's body/status.
