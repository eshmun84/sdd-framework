## Context

See `proposal.md` for why. Adopted contracts already specify copy/pin of a published `sdd-*` subset into a consuming project's project-root `.cursor/` tree, and they already exclude vendor OpenSpec files from that subset. They still treat this repository's `.cursor/` as both the authoring home and the Cursor load path. The first published rule now sits beside vendor `opsx-*` / `openspec-*` files, so the FROM path is no longer obvious.

This repository is the framework source. It already has a local vendor OpenSpec Cursor installation. It is not a consuming project and MUST NOT install its own published subset into `.cursor/`. Cursor still loads only project-root `.cursor/` in repositories that have adopted the baseline.

Implementation is documentation, specification sync, repository hygiene, and a one-file move. It does not add an installer.

## Goals / Non-Goals

**Goals:**
- Make `assets/cursor/` the only published source tree for framework-owned `sdd-*` files.
- Keep `.cursor/` as the only Cursor load path after copy/pin.
- Record FROM → TO so a later installer can only automate this inventory.
- Move Spec First to the source tree without changing the rule body.
- Leave vendor OpenSpec files where they are.

**Non-Goals:**
- Design-level restatement of proposal non-goals (no installer, no manifests, no new assets, no empty dirs, no templates/tooling).
- Changing primitive meaning, classification, or publication-policy completeness of a zero-asset baseline.
- A second documentation page for “distribution” besides adoption + lifecycle + asset model.

## Decisions

### Decision 1: Extend existing capabilities; do not add `sdd-asset-distribution`

**Choice:** Delta `project-adoption`, `sdd-asset-lifecycle-architecture`, `cursor-asset-model`, `cursor-component-model`, type file contracts, `sdd-spec-first`, `repository-hygiene`, and `documentation-architecture`. Do not create a new capability or `docs/architecture/distribution.md`.

**Why:** Adoption already owns copy/pin inventory. Lifecycle already owns implement/publish eligibility. A new capability would split “where files live” from “how projects consume them,” the same split rejected when project-integration extended `project-adoption`.

**Alternatives considered:**
- New `sdd-asset-distribution` capability: clearer name, duplicate home, drift with adoption.
- Docs-only change with `skip_specs`: the FROM path and Spec First location are requirement-level.

### Decision 2: Nested `assets/cursor/`, not a mixed `assets/` dump

**Choice:** Published Cursor primitives live under `assets/cursor/{rules,skills,agents,commands}/` using the same primitive names as the installed tree. Canonical methodology stays in `docs/`. Vendor OpenSpec stays in `.cursor/`.

**Why:** Nested `cursor/` leaves room for other future payload kinds without implying that `docs/` or templates are Cursor assets. Matching primitive folder names keeps copy/pin a prefix-preserving copy into `.cursor/`.

**Alternatives considered:**
- `assets/rules` without `cursor/`: collides conceptually with non-Cursor artifacts.
- `dist/` or `publish/`: release-artifact smell; this tree is source, not a build output.
- Keep publishing from `.cursor/**/sdd-*` with a written filter only: still mixes vendor, dogfood, and published files in one tree.

### Decision 3: Prefix-preserving copy/pin; no path rewriting

**Choice:**

```
FROM  assets/cursor/<primitive>/sdd-*
TO    <consuming-project>/.cursor/<primitive>/sdd-*
```

Manual copy remains valid. The later installer, if any, MUST copy that mapping and MUST NOT invent a different one.

**Why:** Cursor load paths are already specified. Changing only FROM avoids a mapping table and keeps update replacement on the same installed paths.

**Alternatives considered:**
- Copy into `assets/cursor/` in the consuming project: Cursor would not load the files.
- Keep TO as this repository's `.cursor/` layout including vendor files: re-mixes universes.

### Decision 4: This repository does not self-install published `sdd-*`

**Choice:** After the move, this repository's `.cursor/` contains vendor OpenSpec assets only (plus any future project-named non-`sdd-*` dogfood). No symlink, dual-commit, or copy of `assets/cursor/**/sdd-*` into this `.cursor/`. Spec First continues to bind here through `AGENTS.md`.

**Why:** The user-facing identity is source, not installed consuming project. Dual presence recreates the mix this change removes. Symlinks are a hidden installer. This repository is the one place `AGENTS.md` is the framework router and is allowed to carry the constraint.

**Alternatives considered:**
- Git symlink `.cursor/rules/sdd-spec-first.mdc` → source file: restores always-apply here; re-mixes trees; Windows/clone risk.
- Dual-commit both paths: guaranteed drift.
- Treat this repo as first adoptante with a local copy script: forbidden installer-shaped work.

### Decision 5: Create primitive directories only when a file exists

**Choice:** Apply creates `assets/cursor/rules/` because Spec First moves there. Do not create empty `skills/`, `agents/`, or `commands/` directories. Optional commands keep a documented source mapping for when a later skill+command change exists.

**Why:** Empty trees read as a planned catalog. Publication policy already forbids stubs.

**Alternatives considered:**
- Scaffold all four primitive dirs: looks like a catalog.
- Omit `commands/` from the mapping entirely: the constitution still allows a dependent command; the mapping must exist in docs/specs even if the directory does not.

### Decision 6: Move Spec First; do not edit the rule body

**Choice:** `git mv` (or equivalent) `.cursor/rules/sdd-spec-first.mdc` to `assets/cursor/rules/sdd-spec-first.mdc`. Leave frontmatter and body byte-for-byte the same. Remove `.cursor/rules/` if it becomes empty. Do not touch vendor `.cursor/commands/` or `.cursor/skills/`.

**Why:** The path is the defect. The rule is already copy-valid. Editing it would reopen `sdd-spec-first` semantics.

**Alternatives considered:**
- Rewrite pointers while moving: out of scope and risk.
- Leave a stub at the old path: a stub is a catalog/compatibility hack.

### Decision 7: Documentation homes stay; wording splits source vs installed

**Choice:** Update `docs/architecture/adoption.md` as the copy/pin contract (FROM/TO diagram). Update `docs/architecture/asset-lifecycle.md` for implement/publish inventory paths. Update overview, Cursor integration, rule/skill/agent file contracts, README navigation, and a short `AGENTS.md` pointer. Do not add a distribution page.

**Why:** Documentation architecture already assigns those homes. A new page would duplicate adoption.

**Alternatives considered:**
- New `docs/architecture/distribution.md`: second contract for the same topic.

## Risks / Trade-offs

- **[Risk] Spec First no longer always-applies in this repository via Cursor rules** → Mitigation: `AGENTS.md` already encodes the same must-not for this repo; consuming projects get the rule through copy/pin. Do not add a hidden always-apply copy under `.cursor/`.
- **[Risk] Contributors copy `.cursor/` by habit** → Mitigation: adoption inventory lists `assets/cursor/` as FROM; README navigation names the source tree; this repo’s `.cursor/` is documented as vendor-only.
- **[Risk] Archive merges miss a path string in docs** → Mitigation: tasks enumerate the pages that currently hardcode `.cursor/**/sdd-*` as the framework home, distinct from vendor load paths.
- **[Trade-off] No self-install means this repo cannot dogfood Cursor loading of `sdd-*`** → Accepted. Loading is a consuming-project concern. This repo authors and publishes.

## Migration Plan

1. Human accepts this change.
2. Apply writes documentation and hygiene updates, then moves the one rule file to `assets/cursor/rules/`.
3. If `.cursor/rules/` is empty, remove it. Leave vendor `.cursor/` files untouched.
4. Review: source file exists; old published path is gone; vendor files unchanged; rule body unchanged; no empty placeholder dirs; no installer.
5. Rollback: move the rule back to `.cursor/rules/` and revert the documentation/spec path split.

No consuming-project migration is required: there is no released pin of the old FROM path, and the TO path is unchanged.

## Open Questions

None. Self-install vs move-only is Decision 4. Command directories vs command mapping is Decision 5.
