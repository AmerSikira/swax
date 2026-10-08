## Parent

Part of #1 — https://github.com/AmerSikira/swax/issues/1

## What to build

Switch providers and produce equivalent recommendation records without resetting project context.

Covers spec user stories 72, 79.

## Acceptance criteria

- [ ] Implement the selected Anthropic adapter/model with the common validated recommendation contract and approved credential/provider-selection policy.
- [ ] Use the existing scoped analysis/run/attempt/context pipeline and expose effective provider/model/source in the same interface.
- [ ] Demonstrate owner-key and app-key cases, actor/provider switching, persisted original inputs, and retained prior successful results.
- [ ] Test provider-specific translation, authentication, refusal/incomplete/malformed output, and errors at the adapter seam; prove a real browser workflow with controlled server-side responses.
