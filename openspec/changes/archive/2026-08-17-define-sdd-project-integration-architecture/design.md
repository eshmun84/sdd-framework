## Context

See `proposal.md` for why. Foundation `project-adoption` already requires a versioned Cursor-context baseline, consuming-project ownership, runtime decoupling, and no installer. `docs/architecture/adoption.md` is that contract, but it still describes “install or synchronize” and includes vendor OpenSpec Cursor assets in the baseline. Foundation design Decision 4 chose copy/pin and deferred the mechanism; it did not publish an inventory, pin, or update policy.

`cursor-asset-model` already reserves `sdd-*` and forbids in-place product overwrite after copy. `openspec-governance` already keeps this repository’s specs framework-only. This change does not reopen those contracts. It makes adoption precise enough that a later installer can only automate what the docs already specify.

Implementation is documentation and specs. It does not copy files into other repositories.

## Goals / Non-Goals

**Goals:**
- Expand `docs/architecture/adoption.md` into the integration contract specs can be validated against.
- Record copy/pin of a defined subset, transfer inventories, vendor separation, OpenSpec isolation, version pin, update overwrite policy, lifecycle, and production exclusion so later catalog and installer changes do not re-decide them.
- Correct entrypoints that still describe vendor OpenSpec files as part of the copied baseline.
- Leave vendor `.cursor/` files, the `sdd-*` catalog, and consuming-project repositories untouched.

**Non-Goals:**
- Exact sentence-by-sentence wording of `adoption.md` (prose is apply work; contracts are in the specs).
- A second adoption or “integration” documentation page.
- A new OpenSpec capability alongside `project-adoption`.
- Creating `sdd-manifest.yaml`, git tags, releases, templates, or any `sdd-*` Cursor files.
- Designing installer packaging, changelog format, or semver numbering rules beyond “tag is the primary identifier.”

## Decisions

### Decision 1: Extend `project-adoption`; keep one docs home

**Choice:** Modify `project-adoption`. Do not add `sdd-project-integration` or another capability. Expand `docs/architecture/adoption.md`. Do not create `docs/architecture/integration.md`. `docs/architecture/overview.md`, `docs/README.md`, `README.md`, and `AGENTS.md` summarize or link.

**Why:** Adoption is already the named contract. A second capability would split inventory from ownership. Documentation architecture already forbids a second copy of a topic.

**Alternatives considered:**
- New capability plus new page: clearer name, duplicate homes, drift.
- Fold inventory into `cursor-asset-model`: that spec owns naming and paths, not how other repos consume them.

### Decision 2: Copy/pin a published subset, not the repository

**Choice:** The official model is versioned baseline copy/pin of a controlled subset that lands at project-root `.cursor/` and `docs/sdd-framework/`. Reject git submodule, git subtree, package distribution, and runtime dependency. OpenSpec stores remain out of scope as a Cursor-asset channel (unchanged from foundation).

**Why:** Cursor loads `.cursor/` from the project root. A nested submodule is invisible to Cursor; a root submodule would overwrite the product repo. A language package implies a runtime library. Subtree typically drags `openspec/` and git history. Copy/pin of a subset is the only model that matches Cursor paths and spec-universe isolation. Manual copy is valid until a later installer automates the same inventory.

**Alternatives considered:**
- Whole-repo clone or submodule: mixes spec universes and fails Cursor loading.
- External reference only: humans can read GitHub; skills and rules will not load.
- Implement the copier now: forbidden by this change’s non-goals.

### Decision 3: Vendor OpenSpec is obtained in the consuming project

**Choice:** Do not copy `opsx-*` commands or `openspec-*` skills from this repository. Consuming projects obtain them from OpenSpec. The adoption contract requires that vendor surface to be present when the project uses OpenSpec. This refines foundation Decision 4, which listed vendor files inside the baseline.

**Why:** OpenSpec CLI already regenerates those files. Distributing a snapshot from `sdd-framework` forks vendor assets and creates unmergeable drift. The namespace split (vendor vs `sdd-*`) is already the Cursor constitution; distribution should follow it.

**Alternatives considered:**
- Copy vendor files for a known-good surface: pins an OpenSpec version through the wrong channel.
- Optional copy *or* generate: two adoption shapes, later installer ambiguity.

### Decision 4: Methodology snapshot at `docs/sdd-framework/`

**Choice:** Canonical methodology stays at this repository’s `docs/`. Consuming projects, when they take a snapshot, place it at `docs/sdd-framework/`. Product docs remain under that project’s `docs/` outside that reserved subtree. Do not use `.sdd/docs/`.

**Why:** Agents in a consuming project need methodology files in the workspace once `sdd-*` skills point at docs. A reserved subtree is discoverable and does not claim to be product architecture. A hidden `.sdd/` tree is easier to miss in reviews.

**Alternatives considered:**
- `.sdd/docs/`: cleaner product `docs/`, worse discoverability.
- No snapshot, GitHub-only pointers: breaks offline agent context.
- Merge into product `docs/architecture/`: mixes universes.

### Decision 5: `sdd-manifest.yaml` is a named pin, not a file this change creates

**Choice:** Document that a consuming project records git tag (primary), commit SHA (reproducibility), and `sdd-manifest.yaml` as the project record. Do not add that file here. Do not cut tags. Do not specify YAML schema fields beyond what the spec already requires. GitHub Releases stay a later release-management change.

**Why:** Projects need a declared pin, not folklore. Creating a sample manifest or a tag in this change would be implementation of release/adoption tooling.

**Alternatives considered:**
- Hidden `.sdd/manifest.yaml`: agents and humans would not find it as easily.
- Commit SHA only: reproducible, poor human interface.
- Ship a filled example file: template/non-goal.

### Decision 6: Project `AGENTS.md` is specified as a contract, not a template file

**Choice:** State that a consuming-project `AGENTS.md` is project-owned, must identify that product repository, and must not be a verbatim copy of this repository’s `AGENTS.md`. Do not add a template file.

**Why:** This repository’s `AGENTS.md` says “this is the SDD Framework.” Copying it would mis-route agents in AIRen or Nexus. A template file is installer-adjacent and listed as a non-goal.

**Alternatives considered:**
- Copy framework `AGENTS.md`: wrong identity.
- Ship `templates/AGENTS.md` now: out of scope.

### Decision 7: Update is reviewed replacement of framework-owned paths only

**Choice:** On update, replace copied `sdd-*` under `.cursor/` and `docs/sdd-framework/`, and update the pin. Never overwrite project `AGENTS.md`, product OpenSpec, application code, or project-named Cursor assets. Vendor `opsx-*` / `openspec-*` stay on the OpenSpec upgrade path in that repo. Human review of the diff is part of the contract.

**Why:** Reserved prefixes plus a reserved docs path make overwrite safe. Silent whole-tree copy would destroy product customizations. In-place edits of `sdd-*` in the product repo would create unmergeable drift.

**Alternatives considered:**
- Merge-by-hand every file: no durable baseline.
- Overwrite entire `.cursor/`: destroys project extensions.

### Decision 8: Later `sdd-*` assets must be consumer-safe

**Choice:** Record in adoption docs that future framework-owned Cursor assets must remain valid in a consuming project that has adopted the baseline, not only in this repository. Skills and rules MUST locate methodology through the adopted documentation root (`docs/` here, `docs/sdd-framework/` there) rather than assuming they always run inside `sdd-framework`. This change does not create those assets.

**Why:** Dogfooding and consumption share the same files after copy. Hard-coded `docs/architecture/...` paths will 404 in consumers if the snapshot lives at `docs/sdd-framework/`.

**Alternatives considered:**
- Duplicate skill text per repo: guaranteed drift.
- Ignore the path split until the first catalog: first skill would encode the wrong root.

### Decision 9: This apply writes documentation only

**Choice:** Apply expands `docs/architecture/adoption.md` and fixes pointers that still treat vendor files as copied baseline. It does not add `.cursor/` files, manifests, tags, scripts, or templates. Absence of a `sdd-*` catalog remains valid.

**Why:** Same as prior architecture changes: stubs and tooling freeze packaging before the catalog exists.

**Alternatives considered:**
- Empty `docs/sdd-framework/` in this repo: that path is a consuming-project destination, not this repository’s canonical tree.

## Risks / Trade-offs

- **[Risk] Teams still submodule the whole repo** → Mitigation: adoption page states rejected models and why Cursor loading fails; `AGENTS.md` keeps the adoption pointer.
- **[Risk] Foundation wording (“vendor assets in the baseline”) lingers in overview/README** → Mitigation: tasks include a pointer audit of those files.
- **[Risk] Empty `sdd-*` catalog makes copy/pin look vacuous** → Mitigation: specs make absence valid; the inventory is the contract those files will enter; methodology snapshot and pin are still defined.
- **[Risk] `docs/sdd-framework/` collides with a product folder of the same name** → Mitigation: the path is reserved in the contract; product docs stay outside it.
- **[Trade-off] Vendor-local generate vs copied known-good OpenSpec** → Generate-locally is locked; OpenSpec version drift across projects is accepted in exchange for not forking vendor files.
- **[Trade-off] Contract without an installer** → Manual copy is the interim DX; a later change automates the same inventory rather than inventing a new model.

## Migration Plan

Documentation-only. No consuming project is migrated in this change.

1. Apply rewrites `docs/architecture/adoption.md` to the integration contract (inventory, vendor separation, OpenSpec isolation, pin, update policy, lifecycle, production boundary).
2. Apply updates overview, docs index, `README.md`, and `AGENTS.md` only where they still describe vendor files as part of the copied baseline or “install or synchronize” without copy/pin.
3. Vendor `.cursor/` files stay unchanged. No `sdd-*`, manifest, or tag is added.
4. Archive merges the `project-adoption` delta into `openspec/specs/project-adoption/spec.md`.

Rollback is reverting the documentation and change artifacts.

## Open Questions

None that affect this change. Installer implementation, release management (how tags are cut), YAML schema beyond the named pin, and the first `sdd-*` catalog remain dedicated later changes.
