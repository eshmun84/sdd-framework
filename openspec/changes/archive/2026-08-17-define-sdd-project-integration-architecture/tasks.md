## 1. Adoption contract page

- [x] 1.1 Rewrite `docs/architecture/adoption.md` so the official model is versioned baseline copy/pin of a controlled subset (not the whole repository), and document rejected models: git submodule, git subtree, package distribution, and runtime dependency; keep OpenSpec stores out of the Cursor-asset channel
- [x] 1.2 Document ownership: consuming project owns product specs, domain, code, its OpenSpec workspace, project Cursor extensions, and `AGENTS.md`; copied `sdd-*` assets remain framework-owned; this repository's `AGENTS.md` and `README.md` are never copied verbatim
- [x] 1.3 Document the published inventory: copyable `sdd-*` Cursor paths and `docs/sdd-framework/`; never-transfer of this repository's `openspec/`, change history, `AGENTS.md`, `README.md`, and git metadata; empty `sdd-*` catalog remains valid
- [x] 1.4 Document vendor separation: `opsx-*` / `openspec-*` are obtained from OpenSpec in the consuming project and are not distributed by this framework
- [x] 1.5 Document Cursor landing paths (project-root `.cursor/`, methodology snapshot at `docs/sdd-framework/`), independent OpenSpec universes, and that later `sdd-*` assets must remain valid in a consuming project (docs root here vs `docs/sdd-framework/` there)
- [x] 1.6 Document the version-pin contract (git tag primary, commit SHA, `sdd-manifest.yaml`) without creating tags, releases, or a manifest file
- [x] 1.7 Document update as reviewed replacement of framework-owned copied assets only, never-overwrite of project `AGENTS.md`, product OpenSpec, application code, and project-named Cursor assets, the conceptual lifecycle discover → adopt → configure → develop → update, and production exclusion of `.cursor/`, OpenSpec artifacts, the documentation snapshot, and the manifest
- [x] 1.8 Keep the installer, CLI, and sync scripts as a future change; do not add a second adoption or integration documentation page

## 2. Navigation and entrypoints

- [x] 2.1 Update `docs/architecture/overview.md` consume wording so it matches copy/pin of a subset without reproducing the adoption contract
- [x] 2.2 Confirm `docs/README.md` still links to the adoption page as the contract home and does not add a duplicate integration page
- [x] 2.3 Update root `README.md` only where it still implies vendor OpenSpec files are part of the copied baseline or that adoption is unspecified beyond “installer later”
- [x] 2.4 Update `AGENTS.md` so an agent can locate the expanded adoption contract; keep it a short router; retain the instruction not to add an installer or invent a `sdd-*` catalog unless a later change specifies it

## 3. Boundary verification

- [x] 3.1 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged and still documented as vendor-managed
- [x] 3.2 Verify this change did not add `.cursor/rules/`, `.cursor/agents/`, any `sdd-*` Cursor files, `sdd-manifest.yaml`, git tags, templates, scripts, an installer, MCP/plugin/hook config, a custom OpenSpec schema, application code, or `docs/sdd-framework/` in this repository
- [x] 3.3 Run `openspec validate define-sdd-project-integration-architecture --type change --strict` and resolve any validation issues in the change artifacts
