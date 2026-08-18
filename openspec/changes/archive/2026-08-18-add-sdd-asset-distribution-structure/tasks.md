## 1. Adoption and lifecycle documentation

- [x] 1.1 Update `docs/architecture/adoption.md` so the official model diagram and inventory list copy FROM `assets/cursor/**/sdd-*` and copy TO the consuming project's project-root `.cursor/**/sdd-*`, and state that this repository is the source rather than an installed consuming project
- [x] 1.2 Keep vendor exclusion, never-transfer inventory, methodology snapshot at `docs/sdd-framework/`, version pin, update replacement, and installer deferral unchanged except the FROM path
- [x] 1.3 Update `docs/architecture/asset-lifecycle.md` so identity, implement output, publish eligibility, and inventory point at `assets/cursor/**/sdd-*` as source and `.cursor/**/sdd-*` as the installed load path after copy/pin
- [x] 1.4 State that this repository does not self-install published `sdd-*` files into its own `.cursor/`, and that primitive directories under `assets/cursor/` are created only when a file of that primitive exists

## 2. Cursor constitution and type file contracts

- [x] 2.1 Update `docs/architecture/overview.md` and `docs/architecture/cursor-integration.md` so source vs installed paths are named, primitive meaning is unchanged, and this repository's `.cursor/` is not described as the published `sdd-*` home
- [x] 2.2 Update file-contract path wording in `docs/architecture/rule-system.md`, `docs/architecture/skill-system.md`, and `docs/architecture/agent-system.md` to record `assets/cursor/...` as source and `.cursor/...` as the installed project load path
- [x] 2.3 Document the optional command source mapping `assets/cursor/commands/sdd-*` without creating that directory

## 3. Entrypoints and hygiene

- [x] 3.1 Update `README.md` repository navigation so `assets/cursor/` is the published Cursor-asset source and `.cursor/commands/` plus `.cursor/skills/` remain vendor OpenSpec
- [x] 3.2 Add a short `AGENTS.md` pointer that published `sdd-*` files are authored under `assets/cursor/` and are not installed into this repository's `.cursor/`; keep Spec First as a routing constraint in `AGENTS.md` for this repo
- [x] 3.3 Update `.gitignore` comments so `assets/cursor/` remains trackable and this repository's `.cursor/` is described as vendor OpenSpec, not as the published `sdd-*` tree; do not ignore either tree

## 4. Migrate Spec First source file

- [x] 4.1 Create `assets/cursor/rules/` only, and move `.cursor/rules/sdd-spec-first.mdc` to `assets/cursor/rules/sdd-spec-first.mdc` without changing frontmatter or body
- [x] 4.2 Remove `.cursor/rules/` if it is empty after the move
- [x] 4.3 Verify vendor `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged
- [x] 4.4 Verify this change did not add empty `assets/cursor/skills/`, `assets/cursor/agents/`, or `assets/cursor/commands/` directories, an installer, a manifest, a catalog, a symlink or copy of the rule under this repository's `.cursor/`, or any new `sdd-*` asset

## 5. Validation

- [x] 5.1 Verify no new `docs/architecture/distribution.md` page, planned-name catalog, or application code was added
- [x] 5.2 Run `openspec validate add-sdd-asset-distribution-structure --type change --strict` and resolve any validation issues in the change artifacts
