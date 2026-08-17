## MODIFIED Requirements

### Requirement: Consuming project ownership
A consuming project SHALL retain ownership of its product requirements, application architecture, business domain, source code, OpenSpec lifecycle, OpenSpec specifications, project-specific Cursor extensions, and its `AGENTS.md` routing contract.

#### Scenario: Product specifications stay in the project
- **WHEN** a consuming project specifies product behavior
- **THEN** that behavior is recorded in the consuming project's own OpenSpec workspace
- **AND** it is not recorded in this repository's OpenSpec specifications

#### Scenario: Project-specific Cursor extensions are allowed
- **WHEN** a consuming project needs local Cursor assets beyond the framework baseline
- **THEN** those extensions remain owned by the consuming project
- **AND** they do not become part of the SDD Framework unless promoted through this repository's OpenSpec lifecycle

#### Scenario: Project AGENTS.md is not a framework copy
- **WHEN** a consuming project adopts the SDD Framework
- **THEN** that project's `AGENTS.md` remains a project-owned routing contract for that repository
- **AND** documentation forbids copying this repository's `AGENTS.md` verbatim into the consuming project

### Requirement: Versioned Cursor-context adoption
The framework SHALL define an adoption contract in which consuming projects take a versioned baseline by copying and pinning a controlled subset of framework assets into the consuming project's Cursor context and reserved documentation path. The adopted unit SHALL be that published subset, not this repository as a whole. The contract SHALL be architectural in this change and SHALL NOT require an installer or synchronization mechanism to exist yet. Adoption SHALL NOT use a git submodule, git subtree, package distribution, or runtime dependency as the Cursor-asset distribution model.

#### Scenario: Adoption contract is documented
- **WHEN** a team reads the adoption documentation
- **THEN** they are told that consuming projects copy and pin a versioned framework baseline subset into Cursor context
- **AND** they are told that the adopted unit is a controlled subset, not the entire framework repository
- **AND** they are told that the installer or synchronization mechanism is a future change

#### Scenario: Rejected distribution models are documented
- **WHEN** a team reads the adoption documentation
- **THEN** git submodule, git subtree, package distribution, and runtime dependency are described as non-models for consuming the framework
- **AND** an OpenSpec store is not described as the Cursor-asset distribution model

#### Scenario: No installer is required for this change
- **WHEN** this change is applied
- **THEN** no bootstrap CLI, installer, or automated sync tool is required to exist
- **AND** the documented contract remains the source of truth for later implementation

### Requirement: Runtime and production decoupling
The SDD Framework SHALL NOT be coupled to a consuming project's runtime application or production deployment. Adoption SHALL affect engineering workflow assets and documentation, not production executables, services, or runtime configuration. Production deployments SHALL NOT depend on `.cursor/` assets, OpenSpec artifacts, framework documentation snapshots, or `sdd-manifest.yaml`.

#### Scenario: Framework is not a runtime dependency
- **WHEN** a reader consults the adoption contract
- **THEN** the framework is described as an engineering baseline for specification and Cursor-assisted development
- **AND** it is not described as a library, service, or production dependency of consuming applications

#### Scenario: Development-time artifacts are excluded from production
- **WHEN** a reader consults the adoption contract for production boundaries
- **THEN** `.cursor/`, OpenSpec artifacts, the framework documentation snapshot, and the version-pin manifest are described as development-time only
- **AND** they are described as must-not-depend-on for production deployments

## ADDED Requirements

### Requirement: Published baseline inventory
The adoption contract SHALL name the assets that MAY be copied from this repository into a consuming project, the assets that MUST be obtained locally in the consuming project, and the assets that MUST NOT be transferred. An empty `sdd-*` catalog in this repository SHALL remain valid; absence of those files SHALL NOT require inventing stubs in order to adopt.

#### Scenario: Copyable framework-owned assets are listed
- **WHEN** a team reads the baseline inventory
- **THEN** documentation lists `.cursor/rules/sdd-*`, `.cursor/skills/sdd-*`, `.cursor/agents/sdd-*`, `.cursor/commands/sdd-*` when those assets exist, and `docs/sdd-framework/` as the methodology snapshot destination
- **AND** it does not require those `sdd-*` files to exist in this repository yet

#### Scenario: Never-transferred assets are listed
- **WHEN** a team reads the baseline inventory
- **THEN** documentation forbids transferring this repository's `openspec/specs/`, OpenSpec change history, `AGENTS.md`, `README.md`, and git metadata into a consuming project as adopted baseline

### Requirement: Vendor OpenSpec assets are not distributed
OpenSpec vendor Cursor assets whose names use the `opsx-*` or `openspec-*` prefixes SHALL NOT be distributed by the SDD Framework. A consuming project SHALL obtain those assets from OpenSpec in that project's own workspace. The adoption contract SHALL require the vendor surface to be present in a consuming project that uses OpenSpec, and SHALL NOT treat this repository as the distribution channel for those files.

#### Scenario: Vendor files are excluded from the copied baseline
- **WHEN** a team reads the adoption documentation
- **THEN** `opsx-*` commands and `openspec-*` skills are described as OpenSpec-managed
- **AND** they are described as not copied from this repository into consuming projects

### Requirement: Cursor landing paths
Copied framework-owned Cursor assets SHALL land in the consuming project's project-root `.cursor/` tree under the primitive-matched paths already reserved for `sdd-*`. The methodology snapshot SHALL land at `docs/sdd-framework/` in the consuming project. Canonical methodology in this repository SHALL remain under `docs/`. Copied `sdd-*` assets SHALL remain framework-owned after copy. A consuming project SHALL NOT overwrite them in place with product-specific behavior.

#### Scenario: Cursor assets land where Cursor loads them
- **WHEN** a consuming project adopts framework-owned Cursor assets
- **THEN** documentation requires those files to be placed under the consuming project's project-root `.cursor/` tree
- **AND** it does not treat a nested vendor directory as a valid Cursor load path for those assets

#### Scenario: Methodology snapshot has a reserved path
- **WHEN** a consuming project takes a methodology snapshot
- **THEN** documentation requires the snapshot at `docs/sdd-framework/`
- **AND** it forbids merging that snapshot into the consuming project's product documentation root as if it were product architecture

#### Scenario: Copied namespace stays framework-owned
- **WHEN** a consuming project has received framework `sdd-*` assets
- **THEN** those names remain framework-owned
- **AND** the project is not permitted to overwrite them with project-specific behavior under the same names

### Requirement: Independent OpenSpec universes
This repository's OpenSpec workspace SHALL contain framework requirements only. A consuming project's OpenSpec workspace SHALL contain that product's requirements only. Those workspaces SHALL be independent. The adoption contract SHALL forbid copying this repository's OpenSpec specifications or change history into a consuming project as product specifications, and SHALL forbid adding consuming-project product requirements to this repository.

#### Scenario: Framework OpenSpec is not transferred
- **WHEN** a consuming project adopts the SDD Framework
- **THEN** documentation forbids copying `sdd-framework/openspec/` into that project as adopted baseline
- **AND** it requires the consuming project to keep its own OpenSpec workspace for product requirements

#### Scenario: Product OpenSpec is initialized locally
- **WHEN** a consuming project uses OpenSpec for product work
- **THEN** documentation requires that workspace to be created and configured for the product in that repository
- **AND** it forbids reusing this repository's OpenSpec configuration as the product configuration

### Requirement: Version pin contract
A consuming project that has adopted the baseline SHALL be able to record which SDD Framework version it consumes. The primary version identifier SHALL be a git tag. A commit SHA SHALL be recorded for reproducibility. The project record SHALL be named `sdd-manifest.yaml`. This change SHALL define that contract and SHALL NOT require git tags, releases, or a manifest file to exist yet.

#### Scenario: Pin model is documented
- **WHEN** a team reads the versioning section of the adoption contract
- **THEN** they are told that a consuming project records a git tag as the primary identifier
- **AND** they are told that a commit SHA is recorded for reproducibility
- **AND** they are told that the project record is `sdd-manifest.yaml`

#### Scenario: Pin is not implemented in this change
- **WHEN** this change is applied
- **THEN** no git tag, GitHub Release, or `sdd-manifest.yaml` file is required to exist
- **AND** the documented pin remains the source of truth for later release and adoption implementation

### Requirement: Update replacement policy
When a consuming project updates to a newer framework baseline, the update SHALL be a reviewed replacement of framework-owned adopted assets only. The update SHALL replace copied `sdd-*` Cursor assets and `docs/sdd-framework/` when those paths are part of the adopted baseline, and SHALL update the version pin. The update SHALL NOT overwrite the consuming project's `AGENTS.md`, OpenSpec workspace, application code, or project-specific Cursor assets.

#### Scenario: Framework-owned paths are replaced
- **WHEN** a consuming project updates the adopted baseline
- **THEN** documentation describes replacement of framework-owned copied assets
- **AND** it describes a human-reviewed diff rather than silent overwrite of the whole project

#### Scenario: Project-owned paths are never overwritten
- **WHEN** a consuming project updates the adopted baseline
- **THEN** documentation forbids overwriting that project's `AGENTS.md`, OpenSpec workspace, application code, and project-named Cursor assets

### Requirement: Conceptual adoption lifecycle
The adoption contract SHALL describe a conceptual lifecycle of discover, adopt, configure, develop, and update. That lifecycle SHALL be orientation for humans and later tooling. It SHALL NOT require an installer, CLI, or synchronization script to exist.

#### Scenario: Lifecycle stages are documented
- **WHEN** a team reads the adoption documentation
- **THEN** the stages discover, adopt, configure, develop, and update are described
- **AND** they are described as a conceptual lifecycle, not as implemented tooling
