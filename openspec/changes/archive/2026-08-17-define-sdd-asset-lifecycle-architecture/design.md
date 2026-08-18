## Context

See `proposal.md` for why. Cursor constitution, agent/skill/rule operating models, workflow, adoption copy/pin, and human-AI prompt promotion already exist. Type models only require an OpenSpec change to create, change, or deprecate an asset. They do not own classification before a file exists, evidence of repetition, publication into the baseline, or deprecate-then-retire.

`cursor-asset-model` already reserves `sdd-*` and primitive-matched paths. `project-adoption` already lists those paths as copyable and defines replace-on-update. `cursor-component-model` already owns cheapest-fitting-primitive meaning. This change must compose those contracts, not reopen them.

Implementation is documentation and specs. It does not create Cursor files, catalogs, manifests, or release automation.

## Goals / Non-Goals

**Goals:**
- Give `docs/architecture/asset-lifecycle.md` a single, navigable lifecycle operating model that specs can be validated against.
- Keep constitution, type operating models, workflow, and adoption in their current roles; add pointers, not second copies.
- Record asset identity, classification order, evidence bar, conceptual stages, ownership, publication-as-eligibility, and deprecation without a release calendar so later catalog changes cannot smuggle a catalog, installer, or per-asset version scheme.
- Leave vendor OpenSpec assets and existing requirement contracts untouched except navigation.

**Non-Goals:**
- Exact sentence-by-sentence wording of the new page (prose is apply work; contracts are in the specs).
- Creating `.cursor/` assets, `sdd-*` files, templates, or examples.
- A `command-system.md` page (commands stay constitution meaning plus this lifecycle's dependent-asset rule).
- Spec deltas on agent, skill, rule, adoption, workflow, or Cursor constitution capabilities.
- Git tags, `sdd-manifest.yaml`, or release mechanics.

## Decisions

### Decision 1: New page, not a fifth layer and not an expanded type handbook

**Choice:** Authoritative prose lives at `docs/architecture/asset-lifecycle.md`. `docs/architecture/overview.md` stays the four-layer summary and gains a pointer. Do not add a box or table row for assets or lifecycle as a layer. Do not fold the lifecycle into `cursor-integration.md` or into agent/skill/rule pages.

**Why:** The four layers remain OpenSpec, Cursor, SDD Framework, and consuming projects. Lifecycle is how framework-owned Cursor files evolve across those layers, the same way workflow is how a change collaborates. Folding it into a type page would create three incomplete copies. Folding it into the constitution would mix "what a primitive is" with "when a file may exist."

**Alternatives considered:**
- Expand each type model's Lifecycle section: duplicates the shared stages and would require spec deltas this change forbids.
- Expand `docs/architecture/adoption.md`: adoption distributes a published subset; it does not decide whether a skill should exist.
- `docs/lifecycle/asset-lifecycle.md`: collides with the vendor OpenSpec surface page and invites treating stages as commands.

### Decision 2: New capability `sdd-asset-lifecycle-architecture`

**Choice:** Add `sdd-asset-lifecycle-architecture` for the operating model. Extend `documentation-architecture` so the docs tree requires the page and forbids duplication. Do not modify `cursor-component-model`, `cursor-asset-model`, `sdd-agent-architecture`, `sdd-skill-architecture`, `sdd-rule-architecture`, `sdd-workflow-architecture`, `project-adoption`, `human-ai-interaction`, or `openspec-governance`.

**Why:** Shared lifecycle behavior is a distinct contract. Overloading a type spec would reopen creation criteria. Overloading adoption would restate copy/pin. Overloading workflow would mix change collaboration with file evolution. Pointers belong on those pages via documentation-architecture.

**Alternatives considered:**
- Only extend `documentation-architecture`: would require a page without saying what the lifecycle must establish.
- Delta every type spec's "requires an OpenSpec change" requirement: true but redundant; those SHALLs remain true as the mutation rule this page composes.

### Decision 3: Framework assets are Cursor `sdd-*` primitives only

**Choice:** An SDD Framework asset is a rule, skill, agent, or optional command in the reserved namespace and primitive-matched `.cursor/` path. Docs, OpenSpec specs, `AGENTS.md`, prompts, vendor OpenSpec files, consuming-project extensions, and this repository's non-`sdd-*` dogfood rules are not assets in this model. The docs snapshot at `docs/sdd-framework/` remains adoption payload, not a Cursor asset.

**Why:** If docs and specs were assets, this capability would duplicate `documentation-architecture` and `openspec-governance`. The lifecycle still *classifies* needs into those homes; it *governs* only the Cursor files that survive classification.

**Alternatives considered:**
- Broad "published baseline item" including the docs snapshot: blurs methodology snapshot with executable primitives; adoption already owns the snapshot.
- Include `AGENTS.md`: that file is a routing contract and is never copied as adopted baseline.

### Decision 4: Classification order with a universe gate and kind-based spec vs docs

**Choice:** Product, domain, or stack work exits to the consuming project before the type list. Remaining needs are asked in this order: prompt, documentation, specification, repository identity, vendor OpenSpec lifecycle, rule, skill, agent, optional command. Stop at the first fit; cheapest valid home wins. When the need is behavior the framework must guarantee, it is a specification even if it could also be written as prose. Type tests stay on the existing operating models; this page does not reprint them.

**Why:** The list is a lifecycle gate, not a second constitution. Spec-vs-docs must be by kind (requirement vs explanation) so a hidden spec cannot hide in `docs/`. Universe selection is already a workflow human gate; repeating it here prevents `sdd-*` product files without modifying the workflow spec.

**Alternatives considered:**
- Spec before docs in the numbered list: equivalent outcome for requirements, worse match to the agreed classify-before-create prompt.
- Reprint rule/skill/agent creation tests here: guaranteed drift with those pages.

### Decision 5: Optional commands are dependent assets; no command-system page

**Choice:** A command is never proposed alone. It is an optional thin trigger for a skill, same `sdd-*` name. It is deprecated and retired with that skill. Command *meaning* stays in the constitution.

**Why:** A third operating model for a file that must not own procedure text would invite command-only catalogs. The lifecycle only needs the dependency rule.

**Alternatives considered:**
- `docs/architecture/command-system.md` now: no independent creation criteria left after "thin trigger."
- Allow command-only assets for named human triggers without a skill: contradicts the constitution.

### Decision 6: Evidence is recorded repetition, not an incubation calendar

**Choice:** A proposal that would create an asset must record more than one observed occurrence (prompt pattern, dogfood miss, or project extension). Hypothetical usefulness is not evidence. No mandatory waiting period. Absence of assets remains valid. Empty stubs are not a catalog. One OpenSpec change may create a skill and its optional command; it must not create a catalog.

**Why:** Type models already say when a primitive *kind* is justified. They do not say *whether now*. A calendar would be process theater and would collide with "no release calendar." Recording evidence on the proposal is observable.

**Alternatives considered:**
- Formal dogfood period before any `sdd-*` file: unenforceable without release machinery.
- Allow the first catalog change to skip evidence "to have something to adopt": exactly the premature-creation failure this model exists to prevent.

### Decision 7: Conceptual stages compose workflow and adoption; no new commands

**Choice:** Need → classify → propose → implement → validate → publish → adopt → maintain → deprecate → retire are concepts. Propose/implement/validate map onto existing workflow propose/apply/review. Adopt/maintain-via-update map onto adoption. Do not create `/sdd-publish`, `/sdd-validate`, `/sdd-retire`, or a workflow engine.

**Why:** A parallel command surface would wrap OpenSpec. Naming the stages still gives later catalog changes a shared vocabulary.

**Alternatives considered:**
- Only say "use OpenSpec": leaves publication, deprecation window, and classification unnamed — the original gap.
- New vendor-like commands: forbidden by non-goals and by workflow's no-wrapper rule.

### Decision 8: Publish means eligible after archive; tags remain a later release change

**Choice:** After the creating change is archived, an asset that lives in a published-inventory path is eligible for copy/pin. Git tags remain the baseline identifier already specified by adoption. This change does not require tags, GitHub Releases, or `sdd-manifest.yaml` to exist.

**Why:** Blocking publish on a release-architecture capability would stop this operating model until installer-adjacent work exists. Eligibility-after-archive is enough for later catalog changes. Inventing tags here would smuggle release automation.

**Alternatives considered:**
- Require a git tag before any asset is "published": couples this change to unimplemented release work.
- Treat apply-time file existence as published: skips review and archive gates.

### Decision 9: Assets ride the baseline; no per-asset versions

**Choice:** Compatible edits and additive assets arrive on the next whole-subset update. Breaking changes (meaning change, rename, removal) use deprecation then retirement when the asset was eligible for the published subset. No per-asset semver, version catalog, or partial update.

**Why:** Adoption already replaces the framework-owned subset as a unit. Per-asset versions would invent a manifest and a sync tool.

**Alternatives considered:**
- Semver each skill: catalog plus installer, both non-goals.
- Allow projects to skip individual assets on update: forks the baseline.

### Decision 10: Deprecate then retire, without a calendar; never-published may skip the window

**Choice:** Deprecation is an OpenSpec change that marks the asset and keeps it in the published subset. Retirement is a later OpenSpec change that removes it. No day-count or "next major" SLA. An asset that was never eligible for the published subset may be removed by an OpenSpec change without a prior deprecation period. Silent deletion remains forbidden. In-place hotfix of copied `sdd-*` remains forbidden; a consuming project may add a project-named extension or wait for framework change plus update.

**Why:** A calendar needs a release train this repository does not have. A window is still required for anything adopters could have copied. Never-published files have no adopted copies, so a second change would be ceremony. Hotfix-in-place would create silent forks.

**Alternatives considered:**
- "At least one tagged baseline" as the window: depends on tags that do not exist; restated as "remain available during transition" instead.
- Same-change deprecate-and-delete for published assets: adopters see a surprise removal on the next update with no marked transition.
- Emergency edit of copied `sdd-*` in the project: reserved-prefix fork.

### Decision 11: Type-model Lifecycle sections get pointers only

**Choice:** Apply adds a short pointer from agent/skill/rule Lifecycle sections, from the constitution, adoption, and workflow, to `asset-lifecycle.md`. Do not rewrite those operating models and do not delta their specs.

**Why:** The existing "requires an OpenSpec change; silent deletion forbidden" sentences stay true. The shared stages live on one page so they cannot drift.

**Alternatives considered:**
- Replace type Lifecycle sections with "see asset lifecycle" only: would remove the type-specific justification recording those specs still require.
- Delta type specs to mention the new stages: reopens architecture this change pledged not to modify.

### Decision 12: This apply creates zero Cursor asset files

**Choice:** Apply writes `docs/architecture/asset-lifecycle.md` and navigation links. It does not add `.cursor/rules/`, `.cursor/agents/`, `sdd-*` skills or commands, empty stubs, templates, or examples as assets. Non-normative naming mentions on the page, if any, are not files to create.

**Why:** Same as constitution, agent, skill, rule, and workflow changes: stubs fake a catalog. Lifecycle definition must precede catalog creation.

**Alternatives considered:**
- Empty `sdd-*` placeholders "so the lifecycle has something to describe": forbidden by the proposal non-goals.

## Risks / Trade-offs

- **[Risk] Contributors read this as permission to create the catalog** → Mitigation: specs make absence valid; tasks do not create Cursor files; `AGENTS.md` keeps "do not invent the catalog"; the page states lifecycle precedes catalog.
- **[Risk] Named stages are implemented as `/sdd-*` commands** → Mitigation: specs forbid `/sdd-publish`, `/sdd-validate`, and `/sdd-retire`; workflow already forbids wrapping `/opsx-*`.
- **[Risk] Classification list drifts from type operating models** → Mitigation: this page owns the gate and points at type pages for tests; it does not copy those handbooks.
- **[Risk] Soft deprecation window lets published assets vanish in the next chat** → Mitigation: retirement is a distinct OpenSpec change; same-change removal is allowed only when the asset was never published.
- **[Risk] Constitution page and lifecycle page drift** → Mitigation: constitution keeps primitive meaning plus a pointer; lifecycle lives on one page; entrypoints link.
- **[Trade-off] Eligibility-after-archive vs tag-gated publish** → Eligibility is locked so this change is not blocked on release architecture.
- **[Trade-off] Operating model without a starter catalog** → Examples stay non-normative; first assets remain a dedicated later change.

## Migration Plan

Greenfield documentation. No asset catalog to migrate.

1. Apply writes `docs/architecture/asset-lifecycle.md` and adds thin links from `docs/README.md`, `docs/architecture/overview.md`, `docs/architecture/cursor-integration.md`, agent/skill/rule pages, `docs/architecture/adoption.md`, `docs/architecture/workflow-system.md`, `README.md`, and `AGENTS.md`.
2. Vendor `.cursor/` files stay unchanged. No `sdd-*` files are added.
3. Archive syncs `sdd-asset-lifecycle-architecture` into `openspec/specs/` and merges the ADDED delta into `documentation-architecture`.

Rollback is reverting the documentation and change artifacts.

## Open Questions

None that affect this change. The first `sdd-*` catalog and the release/tag implementation remain dedicated later changes.
