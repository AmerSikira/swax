# User journey and screen planning

Status: agreed high-level journey and screen organization. Detailed interface work is listed below.

## Main journey

1. Open the projects list and create or select a project.
2. Configure the website, goals, and editable project brief.
3. Connect available sources and select pages. AI uses the team owner's configured key, otherwise the app key.
4. Run an analysis on demand or configure an optional schedule.
5. Review prioritized recommendation cards and decide which ideas to plan, postpone, or dismiss.
6. Implement chosen changes outside the tool and record their go-live dates and any implementation notes.
7. Review evaluations, evidence, and uncertainty. Continue analyzing with the accumulated project brief and history.

## Confirmed setup and project entry

- Setup is a resumable checklist covering the website, goals, brief, sources, pages, and AI access.
- Show completed and missing setup items and let the operator save progress and return later.
- Useful analyses can proceed with partial setup when sufficient evidence is available.
- Opening a project leads to its overview, showing available goal metrics, data issues, top recommendations, and ongoing evaluations.
- Provide a prominent Run analysis action and access to recommendations, results, history, and configuration.

## Confirmed project navigation

The Projects screen is the entry point for creating or selecting a website project. Within a project, use the six sections below.

| Section | Responsibility |
| --- | --- |
| Overview | Show available goal performance, data issues, top recommendations, and ongoing evaluations; provide Run analysis. |
| Pages & Data | Manage source connections, choose pages, supply manual content, and show evidence freshness or missing data. |
| Recommendations | Review ideas, inspect supporting evidence, and record decisions and implementation. |
| Results | Review evaluations linked to implemented changes, with comparison data and uncertainty; request an AI review using Pass the data to AI. |
| History | Review past analyses, decisions, changes, results, and open questions. |
| Settings | Maintain the project brief, configure goals, and manage the default AI provider/model, schedules, and project usage limits. |

The team owner manages their AI key in account settings; app credentials are platform-managed. Project configuration and shared history remain with the project when users or credential choices change. Projects and regular team members do not supply separate AI keys.

## Confirmed AI access and data review

- Automatically use the team owner's configured key, otherwise the app key, across the team's projects. Packages and commercial tiers are deferred.
- Provide **Pass the data to AI** alongside measured data and results so the user can request an AI interpretation.
- Display the AI review alongside the app's calculated results and keep it in project history.
- By default, send the currently selected report or evaluation, its date range, and the relevant project goal, brief, and history.
- Provider/model selection for the effective credentials and unusable-owner-key handling remain to be settled.

## Confirmed change recording

- Implemented changes have separate records with go-live dates and optional notes about the actual modifications.
- A change record can link to several recommendations or describe a change made independently of AI recommendations.
- Changes implemented together, such as a headline and signup-button update, can be recorded and evaluated together.
- Evaluation results describe the combined change where applicable and account for uncertainty about individual effects.

## Confirmed analysis progress and recovery

- Analyses run in the background with visible progress, clear failure messages, and a retry action.
- Earlier successful recommendations stay available while a new analysis runs or after a failed attempt.
- Identify a disconnected source and provide a reconnect action.
- Apply the agreed partial-evidence rules when a source is unavailable, withholding unsupported conclusions.

## Situations to account for

- A project can be configured over time; incomplete or missing evidence must be visible.
- Useful analyses can proceed with available evidence; unsupported conclusions are withheld.
- Missing goal tracking prevents unsupported goal evaluations and should explain the next setup action.
- An exhausted AI allowance pauses further AI runs and displays a notice.
- Recommendations and evaluation results remain distinct.
- Project history carries across sessions, authorized members, AI providers, and credential choices.

## Detailed interface work

- Choose the entry point for recording a change that is not linked to a recommendation.
- Design detailed layouts, forms, analysis status presentation, and recovery messages.
- Define scheduled execution permissions and team-owner changes with the detailed tenant and permission design.
- Design how user-requested AI reviews are presented.
