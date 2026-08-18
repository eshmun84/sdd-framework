## Why

This repository is the source of reusable SDD Framework Cursor assets. It is not a consuming Cursor project. Storing published `sdd-*` files under `.cursor/` mixes three roles: the distributable baseline, this repository's local Cursor load tree, and vendor OpenSpec files. That mix makes the copy/pin FROM path ambiguous now that the first framework-owned rule exists, and it will get worse as more `sdd-*` files appear.

## What Changes

- Introduce an official **source** tree at `assets/cursor/` for published framework-owned `sdd-*` Cursor assets.
- Keep `.cursor/` as the **installed** Cursor load path in any repository where Cursor must execute those assets.
- **BREAKING** for copy/pin FROM: the published inventory is copied from `assets/cursor/**/sdd-*`, not from this repository's `.cursor/**/sdd-*`. The landing TO path remains the consuming project's project-root `.cursor/` tree.
- Split source vs installed in adoption, asset lifecycle, Cursor asset ownership, and rule/skill/agent file contracts.
- **BREAKING** for `sdd-spec-first`: migrate `.cursor/rules/sdd-spec-first.mdc` to `assets/cursor/rules/sdd-spec-first.mdc` without changing the rule's functional content. This repository SHALL NOT keep a published `sdd-*` copy under `.cursor/`.
- Align documentation and repository hygiene so `assets/cursor/` is trackable and empty placeholder directories are not created.

## Capabilities

### New Capabilities

- None. Source vs installed is a distribution-layout distinction inside existing adoption, lifecycle, and asset-ownership contracts. A second capability would split inventory from consumption.

### Modified Capabilities

- `project-adoption`: Copy/pin FROM is `assets/cursor/**/sdd-*`. Copy/pin TO remains project-root `.cursor/**/sdd-*`. This repository is the source, not an installed consuming project. Vendor OpenSpec exclusion, never-transfer inventory, methodology snapshot, version pin, update replacement, and installer deferral stay.
- `sdd-asset-lifecycle-architecture`: Implement writes source files under `assets/cursor/`. Publish eligibility is that source tree. Inventory is existing `assets/cursor/**/sdd-*` files plus adoption path patterns. Classification, evidence, stages, no-catalog, zero-assets-ok, baseline versioning, and deprecation stay.
- `cursor-asset-model`: Primitive-matched **source** paths live under `assets/cursor/`. Primitive-matched **installed** paths remain under `.cursor/`. Vendor OpenSpec files remain in this repository's `.cursor/` and are not framework source.
- `cursor-component-model`: Naming-and-paths wording distinguishes source location from Cursor load location. Primitive meaning, cheapest-primitive, and OpenSpec-not-wrapped stay.
- `sdd-rule-architecture`: Rule file contract records source path `assets/cursor/rules/sdd-<concern>.mdc` and installed path `.cursor/rules/sdd-<concern>.mdc`. Activation, quality, and copy-validity of content stay.
- `sdd-skill-architecture`: Skill file contract records source path `assets/cursor/skills/sdd-<procedure>/SKILL.md` and installed path `.cursor/skills/sdd-<procedure>/SKILL.md`. Invocation and quality stay.
- `sdd-agent-architecture`: Agent file contract records source path `assets/cursor/agents/sdd-<role>.md` and installed path `.cursor/agents/sdd-<role>.md`. Stance and forbidden ownership stay.
- `sdd-spec-first`: Canonical file location becomes `assets/cursor/rules/sdd-spec-first.mdc`. Installed load path after copy/pin remains `.cursor/rules/sdd-spec-first.mdc`. Operational constraint, activation, and copy-valid body stay unchanged.
- `repository-hygiene`: Ignore rules MUST allow tracking `assets/cursor/` when those files exist. This repository's `.cursor/` remains trackable for vendor OpenSpec assets. Published `sdd-*` files are not required to exist under this repository's `.cursor/`.
- `documentation-architecture`: Adoption, lifecycle, overview, Cursor integration, type operating models, README navigation, and related entrypoints MUST describe source vs installed without adding a second adoption page or a catalog.

## Impact

- Documentation and specification deltas listed above, plus a physical move of one existing rule file.
- After archive, copy/pin reads `assets/cursor/**/sdd-*` and lands files in the consuming project's `.cursor/`.
- This repository's `.cursor/` keeps vendor `opsx-*` / `openspec-*` only for local OpenSpec use. It is not the published subset.
- Spec First continues to bind here through this repository's `AGENTS.md`. Consuming projects receive the rule through copy/pin into their `.cursor/`.
- No application code, installer, adoption script, manifest, catalog, new `sdd-*` asset, or empty placeholder directory.
- Vendor OpenSpec Cursor files stay where they are and stay unmodified.

## Non-goals

- An installer, CLI, adoption script, sync tool, or path-mapping automation.
- `sdd-manifest.yaml`, git tags, releases, or per-asset versions.
- New `sdd-*` rules, skills, agents, or commands, including empty stubs.
- Empty `assets/cursor/` primitive directories created as placeholders.
- Moving, wrapping, renaming, or editing vendor `opsx-*` commands or `openspec-*` skills.
- Templates, tooling packages, prompt catalogs, or expanding asset identity beyond Cursor `sdd-*` primitives.
- Reopening classification, creation evidence, lifecycle stages, deprecation, reserved prefixes, or primitive meaning except the path split above.
- Installing this repository's published subset into its own `.cursor/` (symlink, dual-commit, or copy).
- Changing the Spec First rule's functional content, activation, or copy-valid pointers.
- Consuming-project product requirements or copying this repository's `openspec/` into other repos.
