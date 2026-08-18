## 1. Asset-lifecycle architecture page

- [x] 1.1 Create `docs/architecture/asset-lifecycle.md` covering asset identity (framework-owned `sdd-*` Cursor primitives only), supported categories (rules, skills, agents, optional thin commands), what is not an asset (docs, specs, `AGENTS.md`, prompts, vendor OpenSpec files, consuming-project extensions), dependent-command rule, and that the lifecycle is not a fifth layer, engine, catalog, or OpenSpec replacement
- [x] 1.2 Document classification before creation (universe gate; order: prompt, documentation, specification, identity, vendor OpenSpec, rule, skill, agent, optional command; cheapest home wins; spec vs docs by kind; type tests by pointer) and creation criteria (framework-wide, copy-valid, reusable, stable, recorded repetition, correct primitive, approved OpenSpec change; no hypothetical or stub catalog)
- [x] 1.3 Document conceptual stages (need, classify, propose, implement, validate, publish, adopt, maintain, deprecate, retire), stage boundaries, publication as eligibility after archive, mapping onto existing workflow and adoption without new commands (`/sdd-publish`, `/sdd-validate`, `/sdd-retire` forbidden)
- [x] 1.4 Document ownership, validation as existing review (copy-validity, no hidden spec, no docs dump, no wrapper), baseline versioning with no per-asset versions, adoption copy/pin by pointer, project-extension promotion as evidence, deprecation-then-retirement without a calendar, never-published removal still via OpenSpec, and that this page creates no `sdd-*` files

## 2. Navigation and entrypoints

- [x] 2.1 Add a `docs/README.md` index link to the asset-lifecycle architecture page
- [x] 2.2 Update `docs/architecture/overview.md` with a pointer to the asset-lifecycle page while keeping it the four-layer summary and adding no fifth layer
- [x] 2.3 Point `docs/architecture/cursor-integration.md` at the asset-lifecycle page for how assets are created and retired without copying the lifecycle into the constitution
- [x] 2.4 Point the Lifecycle sections of `docs/architecture/agent-system.md`, `docs/architecture/skill-system.md`, and `docs/architecture/rule-system.md` at the asset-lifecycle page without rewriting those operating models
- [x] 2.5 Point `docs/architecture/adoption.md` and `docs/architecture/workflow-system.md` at the asset-lifecycle page without copying copy/pin or collaboration stages
- [x] 2.6 Update `AGENTS.md` so an agent can locate the asset lifecycle; keep `AGENTS.md` a short router; retain the instruction not to invent a `sdd-*` catalog until a later change specifies it
- [x] 2.7 Update root `README.md` so it points at the asset lifecycle without copying it, and status reflects that the model exists while a skill/agent/rule/command catalog still does not

## 3. Boundary verification

- [x] 3.1 Verify this change did not add `.cursor/` files, `sdd-*` assets, templates, examples as assets, an installer, a manifest, release automation, MCP/plugin/hook config, a custom OpenSpec schema, application code, or a workflow engine
- [x] 3.2 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged
- [x] 3.3 Run `openspec validate define-sdd-asset-lifecycle-architecture --type change --strict` and resolve any validation issues in the change artifacts
