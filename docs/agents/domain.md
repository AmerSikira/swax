# Domain documents

This repository uses one domain context. Before specifying or implementing product behavior, read the root glossary and the relevant decisions in the architecture-decision directory.

- [Glossary](../../GLOSSARY.md) defines the product vocabulary.
- [Architecture decisions](../adr/) record constraints and their rationale.
- [Product spec](../specs/website-improvement-saas.md) records the agreed behavior and unresolved decisions.
- [E2E strategy](../testing/e2e-strategy.md) defines browser and worker verification. For a browser-visible workflow change, update the [coverage map](../testing/e2e-coverage.md).

Preserve agreed decisions while implementing a slice. Record newly resolved policies before dependent work starts; identify business decisions needing user review rather than treating a test fixture as approval.
