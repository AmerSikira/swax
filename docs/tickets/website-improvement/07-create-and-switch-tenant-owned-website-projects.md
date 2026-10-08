## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Let owners create website projects and authorized users select them, with explicit superadmin access and isolation.

Covers spec user stories 1, 2, 3, 4, 5, 6, 7, 16.

## Acceptance criteria

- [ ] Persist a tenant's multiple website projects and provide create/list/select flows plus the agreed project navigation; names/domains are configuration rather than Fakturax-specific code.
- [ ] Use the approved permission matrix for owner, regular member, and superadmin operations, including any minimal provisioning needed to demonstrate the roles without building deferred user-management workflows.
- [ ] Scope reads, writes, selectors, and relationship validation on the backend; reject foreign tenant and same-tenant foreign-project identifiers where inappropriate.
- [ ] Prove persistence after reload and switching between two projects in tenant A, and rejection of tenant B access through browser/public requests and authenticated feature tests.
- [ ] Maintain existing authentication/settings regressions and update project/navigation coverage with actual test evidence.

## Blocked by

- Draft ticket 06: Add the isolated Playwright authentication journey
