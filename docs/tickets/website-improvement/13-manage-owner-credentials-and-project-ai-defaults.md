## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Let the team owner manage their AI key in account settings while projects configure provider/model defaults.

Covers spec user stories 75, 76, 77, 78, 79, 80, 84.

## Acceptance criteria

- [ ] Store owner-provided credentials securely and provide authorized save/replace/remove controls in owner account settings; app credentials remain platform-managed.
- [ ] Expose supported project provider/model defaults without adding member or project API keys.
- [ ] Resolve effective credentials from the project's team owner, otherwise app credentials, following the approved compatibility/failure/ownership policy; disclose only non-secret provider/model/source information.
- [ ] Verify owner/member permissions, two same-tenant projects, another tenant, absence fallback, mismatches, and owner replacement with feature/adapter tests and browser settings journeys.
- [ ] Ensure key material is absent from client output, context, history, logs, and test artifacts; update owner/app credential coverage.

## Blocked by

- Draft ticket 04: Decide AI execution, credential, and usage policies
- Draft ticket 07: Create and switch tenant-owned website projects
