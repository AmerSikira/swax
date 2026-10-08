## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Settle the access and deployment contract before tenant-owned workflows are implemented.

Decision or verification prerequisite for the product slices.

## Acceptance criteria

- [ ] Record membership/cardinality, owner replacement, regular-member capabilities, and explicitly authorized superadmin operations as a permission matrix; retain the deferred scope of full membership-management UI.
- [ ] Select and document the production database, queue driver, worker/scheduler operation, and verification environment using the existing Laravel stack.
- [ ] Show allowed and rejected same-tenant, cross-tenant, same-tenant cross-project, and worker-without-session examples, including credential ownership after owner replacement.
- [ ] List business decisions requiring owner review and obtain recorded approval before closing this gate; document infrastructure decisions with their rationale.

## Blocked by

None (can start immediately).
