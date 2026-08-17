## Why

The foundation adoption contract says consuming projects will take a versioned Cursor-context baseline and that an installer is later. It does not define the adopted unit, what may be copied, what must never transfer, how vendor OpenSpec assets are obtained, how a project records the version it consumes, or how updates replace framework-owned files without overwriting product work. Without that contract, projects such as AIRen and Nexus will invent incompatible adoption shapes and mix specification universes.

## What Changes

- Expand the **project adoption contract** into a professional integration architecture: versioned baseline copy/pin of a controlled subset; ownership after copy; Cursor path rules; OpenSpec isolation; vendor separation; version pin; update lifecycle; production boundary.
- Keep `docs/architecture/adoption.md` as the single authoritative adoption page. Expand it to carry the integration contract. Entrypoints summarize or link; they do not own a second copy.
- Refine the foundation baseline: framework-owned Cursor assets and a methodology snapshot may be copied; vendor `opsx-*` / `openspec-*` assets are **not** distributed by this framework; framework OpenSpec artifacts, `AGENTS.md`, `README.md`, and git metadata are never transferred.
- Record a future version-pin model (git tag, commit SHA, `sdd-manifest.yaml`) and a reviewed-replacement update model without implementing releases, manifests, or sync tooling.

This change is documentation and specification only. It does **not** implement an installer, create `sdd-*` catalog files, or modify consuming-project repositories.

## Capabilities

### New Capabilities

- None. Integration architecture belongs in the existing adoption capability.

### Modified Capabilities

- `project-adoption`: Replace the thin “install or synchronize later” contract with normative requirements for copy/pin of a defined subset, transfer and never-transfer inventories, vendor OpenSpec obtained in the consuming project, independent OpenSpec universes, version pin (tag + SHA + manifest as contract only), update replace-vs-never-touch rules, conceptual adopt/update lifecycle, and development-time vs production exclusion. The installer remains a future change.

## Impact

- Documentation and specs only: expanded `docs/architecture/adoption.md`; pointer updates in `docs/architecture/overview.md`, `docs/README.md`, `README.md`, and `AGENTS.md` if they still describe vendor files as part of the copied baseline; delta spec as listed above.
- No application code, installer, CLI, sync scripts, package manager, MCP, plugins, hooks, or Cursor asset files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched in this repository.
- Consuming projects are unaffected until a later change implements adoption. This change only defines the contract those later implementations and manual adoptions must follow.

## Non-goals

- Installer, bootstrap CLI, or synchronization scripts.
- Package manager distribution.
- MCP integrations, Cursor plugins, or hooks.
- Cloud runtime or application dependencies.
- Creating `sdd-*` catalog assets, including empty stubs.
- Creating consuming-project templates (including an `AGENTS.md` template file or a sample `sdd-manifest.yaml` file in this repository).
- Implementing git tags, GitHub Releases, or any manifest file.
- Modifying AIRen, Nexus, or any other consuming-project repository.
- Git submodules, git subtrees, or OpenSpec stores as the Cursor-asset distribution model.
- Reopening Cursor component, agent, or skill operating models except where adoption must state that copied `sdd-*` assets remain framework-owned.
- Changing the OpenSpec schema or adding product requirements to this repository.
