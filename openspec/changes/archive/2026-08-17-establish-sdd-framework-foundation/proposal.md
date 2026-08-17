## Why

This repository is intended to be a reusable Spec-Driven Development (SDD) framework — a common engineering baseline for multiple professional software projects. Today it is only a tooling bootstrap: a two-line README, an empty OpenSpec workspace, and vendor-generated Cursor commands and skills. Without an explicit identity, documentation architecture, asset-ownership model, and adoption contract, later work will invent conflicting answers and consuming projects will mix product specs with framework specs.

The foundation must be established now, before skills, agents, Git workflows, or installers exist, so those later changes have a stable contract to extend.

## What Changes

- Establish SDD Framework identity: independent methodology repository, not a product, domain, language, or application.
- Define repository responsibilities and the four-layer relationship: SDD Framework, OpenSpec, Cursor, and consuming project repositories.
- Introduce a documentation architecture under `docs/` with human (`README.md`) and AI (`AGENTS.md`) entrypoints that route to deeper material rather than duplicating it.
- Define Cursor asset ownership: OpenSpec-generated `opsx-*` / `openspec-*` assets remain vendor-managed; future framework-owned assets use an `sdd-*` namespace. This change defines the boundary only.
- Define an initial project adoption contract: consuming projects will eventually install or synchronize a versioned set of framework assets into their Cursor context. No installer is implemented here. The framework is not coupled to any project's runtime or production deployment.
- Configure this repository's OpenSpec `context` and artifact `rules` so later changes inherit identity and governance. Keep the stock `spec-driven` schema. Framework OpenSpec specs stay in this repository; consuming projects keep their own.
- Add technology-neutral repository hygiene (`.gitignore`) appropriate for a documentation/tooling repository.

Out of scope (independent future changes): complete multi-agent architecture; reusable skill catalog; custom SDD Cursor agents, skills, or commands; project bootstrap CLI or installer; release management; Git workflow assets; custom OpenSpec schema; technology-specific or product-specific guidance; application code.

## Capabilities

### New Capabilities

- `framework-identity`: What this repository is and is not; layer responsibilities; isolation of framework specs from consuming-project product specs.
- `documentation-architecture`: `docs/` structure, navigation, `README.md` as human entrypoint, `AGENTS.md` as AI entrypoint, documentation conventions for this foundation.
- `cursor-asset-model`: Ownership and naming of Cursor commands, skills, rules, and agents (vendor `opsx-*` / `openspec-*` vs framework `sdd-*`).
- `project-adoption`: Architectural contract for how consuming projects take a versioned framework baseline without coupling runtime or product specs.
- `openspec-governance`: How this repository uses OpenSpec (schema, config context/rules, change lifecycle, spec isolation).
- `repository-hygiene`: Technology-neutral ignore rules and exclusion of operating-system, editor, temporary, environment, and generated noise.

### Modified Capabilities

- None. `openspec/specs/` is empty.

## Impact

- Documentation and repository contract only: expanded `README.md`, new `AGENTS.md`, new `docs/` tree, `.gitignore`, and `openspec/config.yaml` context/rules.
- No application code, APIs, runtime dependencies, or Cursor custom assets.
- Vendor OpenSpec Cursor commands and skills are retained and not renamed.
- Consuming projects are unaffected until a later adoption/installer change; this change only documents the contract they will use.
- After archive, the six new capabilities become this repository's first main specs.
