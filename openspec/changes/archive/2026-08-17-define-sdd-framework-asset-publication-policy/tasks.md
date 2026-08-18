## 1. Publication policy on the asset-lifecycle page

- [x] 1.1 Replace the Catalog status section of `docs/architecture/asset-lifecycle.md` with a publication policy: a published baseline may contain zero `sdd-*` files; that absence is not incompleteness; no planned-name catalog exists; inventory is existing `.cursor/**/sdd-*` files plus adoption path patterns; each future asset is its own OpenSpec change (skill plus optional command allowed); classification, stages, evidence, ownership, validation, versioning, deprecation, and retirement stay unchanged
- [x] 1.2 Close remaining catalog-as-remaining-work wording on that page (including “lifecycle precedes catalog creation” and “later catalog changes create files”) so the page forbids a catalog document and empty stubs without adding a new architecture page

## 2. Entrypoints and overview

- [x] 2.1 Update `docs/architecture/overview.md` so it no longer describes a custom `sdd-*` catalog as a later required change; keep it the four-layer summary with a pointer to asset lifecycle
- [x] 2.2 Update the Catalog status section of `docs/architecture/cursor-integration.md` so later per-asset OpenSpec changes follow the constitution and lifecycle; do not present a catalog change as remaining work; keep existing example names labeled non-normative and do not add names
- [x] 2.3 Update root `README.md` status so methodology, architecture, and OpenSpec governance are in place, the published Cursor subset may be empty, and a skill/agent/command/rule catalog is not remaining foundation work
- [x] 2.4 Update `AGENTS.md` so it still forbids inventing a catalog and no longer implies that a later OpenSpec change should specify one; keep `AGENTS.md` a short router

## 3. Adoption completeness pointer

- [x] 3.1 Update `docs/architecture/adoption.md` so a copy/pin subset with the methodology snapshot and zero `sdd-*` files is a complete published baseline; do not reopen copy/pin, landing paths, never-transfer inventory, vendor exclusion, or installer deferral

## 4. Example names and out-of-scope pages

- [x] 4.1 Confirm existing non-normative `sdd-*` example names on the Cursor constitution and type pages remain labeled as illustrations, are not presented as backlog, and that this change does not add new example names
- [x] 4.2 Confirm `docs/architecture/skill-system.md`, `rule-system.md`, `agent-system.md`, `workflow-system.md`, and `docs/practices/human-ai-interaction.md` are unchanged except any existing pointers already required by prior changes

## 5. Boundary verification

- [x] 5.1 Verify this change did not add `.cursor/rules/`, `.cursor/skills/`, `.cursor/agents/`, `.cursor/commands/`, any `sdd-*` file, a catalog page, a planned-name inventory, a manifest, an installer, or release automation
- [x] 5.2 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged
- [x] 5.3 Verify asset-lifecycle identity, classification order, creation criteria, and conceptual stages were not rewritten
- [x] 5.4 Run `openspec validate define-sdd-framework-asset-publication-policy --type change --strict` and resolve any validation issues in the change artifacts
