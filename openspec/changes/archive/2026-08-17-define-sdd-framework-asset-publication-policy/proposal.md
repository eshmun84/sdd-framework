## Why

Asset lifecycle already treats absence of `sdd-*` files as valid and forbids empty stubs, but several pages still read as if a future catalog is remaining foundation work. That ambiguity invites a planned-name inventory or a first-release Cursor catalog. This change locks the publication reading: a complete framework baseline may contain zero Cursor assets, and the first `sdd-*` files arrive only through later evidence-gated OpenSpec changes.

## What Changes

- Add a **publication policy** to the existing asset-lifecycle architecture: a published baseline may contain zero framework-owned Cursor assets; that absence is not an incomplete implementation; there is no planned or future asset catalog; example `sdd-*` names in documentation are illustrations, not backlog or creation intent; publishing a baseline does not require Cursor assets; each future asset is its own OpenSpec change that follows the existing lifecycle.
- Close wording that presents “a later catalog change” as remaining work. Keep asset identity, classification, creation criteria, stages, ownership, validation, deprecation, and retirement unchanged.
- Align README status, architecture overview, Cursor constitution catalog-status wording, and a thin adoption pointer so the empty Cursor subset is described as a complete published state.

This change is documentation and specification only. It does **not** create `.cursor/` files, `sdd-*` assets, a catalog page, a planned-name inventory, a manifest, or tooling.

## Capabilities

### New Capabilities

- None. Publication policy is an interpretation of the existing lifecycle and published baseline, not a new architecture layer or capability.

### Modified Capabilities

- `sdd-asset-lifecycle-architecture`: ADD publication-policy requirements. The lifecycle model (identity, classification order, creation evidence, stages, ownership, validation, versioning, deprecation, retirement) MUST remain unchanged. New requirements MUST state that a published baseline MAY contain zero `sdd-*` files, that this is not incompleteness, that no planned-name catalog exists, that documentation examples are non-normative, and that each future asset requires its own OpenSpec change.
- `documentation-architecture`: README status, architecture overview, and related catalog-status wording MUST NOT present a future `sdd-*` catalog as remaining foundation work. The asset-lifecycle page MUST document the publication policy. Example `sdd-*` names MUST remain labeled as non-normative illustrations and MUST NOT be presented as a backlog.
- `project-adoption`: Narrow clarification only: a copy/pin subset with methodology snapshot and zero `sdd-*` files is a complete published baseline. Copy/pin, inventory categories, vendor exclusion, and installer deferral stay unchanged.

## Impact

- Documentation and specs only: extend `docs/architecture/asset-lifecycle.md`; fix catalog-as-backlog wording on overview, Cursor integration, docs index if needed, `README.md`, and a pointer on adoption; delta specs as listed above.
- No application code, installer, MCP, plugins, hooks, templates, manifests, release automation, or Cursor asset files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Workflow, human-AI interaction, skill, rule, and agent operating models are not reopened.
- Adoption copy/pin is not replaced; only the completeness reading of an empty Cursor subset is clarified.
- Consuming projects may pin a docs-only baseline. No `sdd-*` files are introduced for them to copy.

## Non-goals

- Creating `.cursor/rules/`, `.cursor/skills/`, `.cursor/agents/`, `.cursor/commands/`, or any `sdd-*` file, including empty stubs.
- A catalog document of current or future assets.
- A planned-name inventory, asset backlog, or example assets treated as work to implement.
- An asset manifest, installer, synchronization tooling, or release automation.
- Changing asset-lifecycle classification, creation criteria, stages, ownership, validation, versioning, deprecation, or retirement.
- Reopening workflow, human-AI interaction, skill, rule, or agent architecture.
- Reopening adoption copy/pin, landing paths, never-transfer inventory, or vendor OpenSpec exclusion except the completeness pointer above.
- Wrapping, renaming, or redefining vendor OpenSpec commands (`/opsx-*`) or skills (`openspec-*`).
- Product-specific assets or consuming-project repository changes.
- Changing the OpenSpec schema or mixing specification universes.
