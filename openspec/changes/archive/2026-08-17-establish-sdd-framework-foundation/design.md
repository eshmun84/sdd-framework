## Context

The repository already has OpenSpec 1.7.0 with the package `spec-driven` schema, empty `openspec/specs/` and `openspec/changes/` (aside from this change), stock Cursor `opsx-*` commands and `openspec-*` skills, and a two-line `README.md`. There is no `docs/`, `AGENTS.md`, `.gitignore`, or `openspec/config.yaml` context. See `proposal.md` for why that is insufficient.

This change is documentation and contract only. Implementation creates files in this repository; it does not add runtime code, Cursor custom assets, or an installer.

## Goals / Non-Goals

**Goals:**
- Give humans and agents a single, navigable map of the repository.
- Encode the four-layer model and adoption contract in durable specs plus matching docs.
- Constrain later OpenSpec work through `openspec/config.yaml` context and artifact rules.
- Keep vendor Cursor assets untouched while documenting the `sdd-*` namespace for later changes.
- Add technology-neutral hygiene so methodology assets can be versioned without noise.

**Non-Goals:**
- File-by-file wording beyond the contracts in the specs (exact prose is implementation, not a second spec).
- Installing or syncing assets into any consuming project.
- Forking or wrapping the OpenSpec CLI.
- Creating `.cursor/rules/`, custom agents, or `sdd-*` skills/commands.

## Decisions

### Decision 1: Docs are the methodology; OpenSpec specs are the requirements

**Choice:** Put readable methodology under `docs/`. Keep `openspec/specs/` as the requirement contract for the framework itself.

**Why:** Consuming humans and agents need prose they can navigate. OpenSpec needs behavioral specs that archive. Mixing those in one tree either makes specs unreadable or makes docs untestable.

**Alternatives considered:**
- Specs-only (no `docs/`): fails as a human baseline and forces `README.md` to become a dump.
- Docs-only (skip specs): bypasses the lifecycle this framework is supposed to teach.

### Decision 2: Two root entrypoints with different audiences

**Choice:**
- `README.md` — human overview and navigation.
- `AGENTS.md` — concise agent operating contract and router.

**Why:** One file cannot serve both well. Humans need purpose and status. Agents need boundaries and pointers. Both MUST link into `docs/` instead of owning architecture, adoption, lifecycle, or governance.

**Alternatives considered:**
- `AGENTS.md` as a full copy of `docs/`: drifts immediately.
- Cursor rules instead of `AGENTS.md`: rules are not yet a framework-owned catalog; the root agent entrypoint is still required.

### Decision 3: Foundational `docs/` layout

**Choice:** Create this tree during apply:

```
docs/
  README.md
  principles.md
  architecture/
    overview.md
    adoption.md
  lifecycle/
    openspec-workflow.md
  governance/
    working-agreements.md
```

**Why:** Matches the four topics the specs require without inventing later catalogs (skills, agents, Git workflows, release). `architecture/overview.md` owns the four-layer diagram. `architecture/adoption.md` owns the consumption contract so adoption is not buried in overview.

**Alternatives considered:**
- Flat `docs/*.md`: gets noisy as soon as later changes add skills and Git workflows.
- Deeper trees now (`docs/cursor/skills/`, `docs/agents/`): documents capabilities this change explicitly excludes.

### Decision 4: Versioned copy/pin adoption, installer deferred

**Choice:** Document that consuming projects will install or synchronize a **versioned** set of framework assets into their **Cursor project context**. Do not implement copy, submodule, store registration, or CLI. Do not couple the framework to application runtime or production.

**Why:** The user locked this direction. OpenSpec stores are spec-centric and do not ship Cursor assets. Submodules are painful for `.cursor/`. Copy/pin is the contract later automation can implement.

**Alternatives considered:**
- Git submodule of this entire repo: couples product repos to framework git history and invites spec-universe mixing.
- OpenSpec store as the adoption mechanism: useful later for spec reference, insufficient as the Cursor-asset distribution model.
- Implement an installer now: out of scope and would freeze packaging before the asset catalog exists.

### Decision 5: Keep package `spec-driven`; fill config instead of forking

**Choice:** Leave schema as package `spec-driven`. Add `context` and per-artifact `rules` in `openspec/config.yaml`. Do not add `operations` guidance unless a later change needs apply/archive advice.

**Why:** Custom schemas are justified only by new artifact types. The gap is identity, not workflow shape. Context and rules are the native place to constrain later `/opsx-propose` runs.

**Context MUST state, in substance:**
- This repository is the SDD Framework, a reusable methodology and tooling baseline.
- It is not a product, domain, language, or application.
- Implementation work is documentation, governance, and Cursor/OpenSpec assets.
- Consuming-project product specifications do not live here.
- Vendor `opsx-*` / `openspec-*` assets must not be redefined; framework-owned Cursor assets use `sdd-*`.

**Artifact rules MUST, in substance:**
- `proposal`: include non-goals; keep scope inside the framework; no product requirements.
- `specs`: behavioral requirements only; no stack-specific implementation.
- `design`: record layer-boundary decisions; do not invent installers or custom schemas without a dedicated change.
- `tasks`: small, reviewable documentation/tooling steps; no application code.

**Alternatives considered:**
- Fork `spec-driven` to add ADR/release artifacts: premature.
- Leave `config.yaml` empty until a later change: later proposals would keep inventing identity.

### Decision 6: Vendor Cursor assets stay; namespace is documentation-only for now

**Choice:** Do not move, rename, or wrap generated `.cursor/commands/opsx-*.md` or `.cursor/skills/openspec-*/`. Document ownership in `docs/architecture/overview.md` (and a short pointer from `AGENTS.md`). Future framework-owned assets use `sdd-*`.

**Why:** OpenSpec CLI upgrades expect to regenerate vendor files. Mixing methodology into them creates unmergeable drift.

**Alternatives considered:**
- Prefix everything `sdd-` now by copying vendor skills: forks OpenSpec semantics, which the constraints forbid.
- Add empty `sdd-*` stubs: fake catalog, out of scope.

### Decision 7: Technology-neutral `.gitignore`

**Choice:** Ignore categories, not a language stack:

- OS: `.DS_Store`, `Thumbs.db`, `Desktop.ini`
- Editor/IDE user state: `.idea/`, `*.swp`, `.vscode/*` except shared settings if added later (ignore user-specific; do not ignore `.cursor/commands` or `.cursor/skills`)
- Env: `.env`, `.env.*`, keep `.env.example` un-ignored if added later
- Temp/logs: `*.log`, `tmp/`, `*.tmp`
- Secrets/noise: `*.pem`, `*.key` if present as local accidents

Do **not** add Python/Node/Java build trees as if they were this repo's stack. A short comment block MAY mention that language-specific ignores belong in consuming projects.

**Why:** This is a documentation/tooling repository. Stack ignores would lie about identity.

## Risks / Trade-offs

- **[Risk] Adoption contract without an installer is easy to ignore** → Mitigation: state the contract and the deferred installer explicitly in `docs/architecture/adoption.md` and `AGENTS.md`; later change owns the mechanism.
- **[Risk] Vendor OpenSpec assets are overwritten on CLI upgrade** → Mitigation: document them as vendor-managed; never put framework rules inside them.
- **[Risk] Docs and specs drift** → Mitigation: `docs/` explains; `openspec/specs/` is canonical after archive; `AGENTS.md` points to both roles instead of copying either.
- **[Risk] Filling `config.yaml` now does not retroactively constrain this change** → Mitigation: acceptable; this change *creates* the constraint for everything after it.
- **[Trade-off] Copy/pin vs store vs submodule** → Copy/pin into Cursor context is chosen for Cursor assets. OpenSpec store remains available later for spec referencing, not as the foundation distribution model.

## Migration Plan

Greenfield for framework docs. No production system to migrate.

1. Apply creates `README.md` expansion, `AGENTS.md`, `docs/**`, `.gitignore`, and `openspec/config.yaml` context/rules.
2. Existing vendor Cursor files stay in place.
3. Archive syncs the six new capabilities into `openspec/specs/`.
4. Consuming projects are unchanged until a later adoption-implementation change.

Rollback is reverting the applied files; there is no runtime rollback.

## Open Questions

None that affect this change. Installer packaging, whether an OpenSpec store is later used for spec reference, and the first `sdd-*` asset set are deferred to dedicated changes.
