# GitHub issue tracker

Specs and tickets live in GitHub Issues for `AmerSikira/swax`. Use `gh` with an explicit `--repo AmerSikira/swax` when creating, reading, or editing issues and pull requests.

## Publishing

Create the spec parent with its complete Markdown body and the `ready-for-agent` label. Create approved tickets in dependency order, one issue per ticket, using `--body-file` for multiline content. Read the issue body and comments before working on an existing issue.

Attach each ticket to the spec using GitHub sub-issues. Add native blocked-by relationships using the blocker's database ID, rather than its issue number. Verify the relationships after creation. If the API cannot support either relationship, retain the parent reference and explicit blocking issue links in the child body. Preserve the parent's body and status.

Work on tickets whose blockers are complete. The `ready-for-agent` label does not override a dependency or an unresolved decision gate.

PRs as a request surface: **no**.

## Commands

- Create: `gh issue create --repo AmerSikira/swax --title "..." --body-file <body-file> --label ready-for-agent`.
- Read: `gh issue view <number> --repo AmerSikira/swax --json number,title,body,labels,comments`.
- List: `gh issue list --repo AmerSikira/swax --state open --limit 100 --json number,title,labels`.
- Sub-issue: `gh issue edit <parent> --repo AmerSikira/swax --add-sub-issue <child>`.
- Database ID: `gh api repos/AmerSikira/swax/issues/<number> --jq .id`.
- Blocking edge: `gh api --method POST repos/AmerSikira/swax/issues/<child>/dependencies/blocked_by -F issue_id=<blocker-database-id>`.

For the approval and publishing sequence, follow the explicitly invoked spec or ticket skill. Record published numbers and URLs with the ticket breakdown so an interrupted publication can resume without duplicates.
