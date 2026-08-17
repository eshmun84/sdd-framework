## 1. Repository hygiene

- [x] 1.1 Add a root `.gitignore` that ignores OS metadata, editor/IDE user state, local environment files, temporary files, logs, and accidental key material without assuming an application language or runtime
- [x] 1.2 Confirm `.gitignore` does not exclude `docs/`, `README.md`, `AGENTS.md`, `openspec/`, `.cursor/commands/`, or `.cursor/skills/`

## 2. OpenSpec governance configuration

- [x] 2.1 Add `context` to `openspec/config.yaml` identifying this repository as the SDD Framework methodology source of truth, not a product or application, with implementation limited to documentation and tooling assets
- [x] 2.2 Add artifact `rules` in `openspec/config.yaml` for proposal, specs, design, and tasks that keep later changes inside framework scope and forbid consuming-project product requirements
- [x] 2.3 Confirm the configured schema remains stock `spec-driven` with no project-local schema fork

## 3. Documentation tree

- [x] 3.1 Create `docs/README.md` as the documentation index linking to principles, architecture, adoption, lifecycle, and governance
- [x] 3.2 Create `docs/principles.md` with core SDD framework principles (spec-driven lifecycle, Cursor as execution environment, reusable baseline, spec-universe isolation)
- [x] 3.3 Create `docs/architecture/overview.md` documenting the four-layer relationship (SDD Framework, OpenSpec, Cursor, consuming projects) and the Cursor asset ownership model (`opsx-*`/`openspec-*` vendor vs `sdd-*` framework)
- [x] 3.4 Create `docs/architecture/adoption.md` documenting versioned Cursor-context adoption, consuming-project ownership, runtime/production decoupling, and that the installer is a future change
- [x] 3.5 Create `docs/lifecycle/openspec-workflow.md` describing the native explore → propose → apply → sync → archive lifecycle and the installed `opsx-*` command surface without redefining OpenSpec semantics
- [x] 3.6 Create `docs/governance/working-agreements.md` describing how framework changes are specified, reviewed, and archived in this repository

## 4. Repository entrypoints

- [x] 4.1 Expand root `README.md` into the human entrypoint covering identity, purpose, core principles, architecture overview, repository navigation, documentation entrypoint, and foundational project status, linking to `docs/` for detail
- [x] 4.2 Create root `AGENTS.md` as the AI-agent routing contract covering repository identity, documentation location, OpenSpec usage, governance boundaries, vendor-asset rules, spec-universe isolation, and pointers into `docs/`
- [x] 4.3 Verify `README.md` and `AGENTS.md` summarize or link rather than duplicating architecture, adoption, lifecycle, and governance documents

## 5. Boundary verification

- [x] 5.1 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged and still documented as vendor-managed
- [x] 5.2 Verify this change did not add `sdd-*` Cursor commands, skills, rules, or agents, an installer, a custom OpenSpec schema, or application code
- [x] 5.3 Run `openspec validate --change "establish-sdd-framework-foundation"` and resolve any validation issues in the change artifacts
