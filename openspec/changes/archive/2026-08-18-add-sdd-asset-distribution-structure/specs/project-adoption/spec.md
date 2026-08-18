## ADDED Requirements

### Requirement: Source assets are distinct from installed assets
The adoption contract SHALL distinguish framework **source** assets from **installed** assets. Source assets SHALL live under `assets/cursor/` in this repository. Installed assets SHALL live under project-root `.cursor/` in any repository where Cursor loads them. Copy/pin SHALL copy FROM the source tree TO the consuming project's installed tree. This repository SHALL be documented as the framework source, not as an installed consuming project. This repository SHALL NOT install its published `sdd-*` subset into its own `.cursor/` tree.

#### Scenario: Copy has a FROM and a TO
- **WHEN** a team reads the adoption documentation
- **THEN** they are told that published Cursor assets are copied from `assets/cursor/`
- **AND** they are told that those files land in the consuming project's project-root `.cursor/` tree

#### Scenario: Framework repo is not an installed consuming project
- **WHEN** a reader consults whether this repository is a Cursor installation of the published subset
- **THEN** documentation states that this repository is the source of the published subset
- **AND** it states that this repository does not keep published `sdd-*` files under `.cursor/`

### Requirement: Source primitive directories exist only with files
A primitive directory under `assets/cursor/` SHALL exist only when at least one published framework-owned file of that primitive exists. The adoption contract SHALL NOT require empty `assets/cursor/` placeholder directories for rules, skills, agents, or commands.

#### Scenario: Empty placeholder directories are forbidden
- **WHEN** a contributor would add `assets/cursor/skills/`, `assets/cursor/agents/`, or `assets/cursor/commands/` with no published file
- **THEN** documentation forbids those empty directories
- **AND** it treats absence of that primitive's directory as a valid complete source state

## MODIFIED Requirements

### Requirement: Published baseline inventory
The adoption contract SHALL name the assets that MAY be copied from this repository into a consuming project, the assets that MUST be obtained locally in the consuming project, and the assets that MUST NOT be transferred. Copyable framework-owned Cursor assets SHALL be listed from the source tree: `assets/cursor/rules/sdd-*`, `assets/cursor/skills/sdd-*`, `assets/cursor/agents/sdd-*`, and `assets/cursor/commands/sdd-*` when those assets exist. An empty `sdd-*` Cursor subset in this repository SHALL remain a complete published baseline. Absence of those files SHALL NOT require inventing stubs in order to adopt and SHALL NOT be described as an incomplete implementation. Copy/pin, landing paths, never-transfer inventory, vendor OpenSpec exclusion, and installer deferral SHALL remain as already specified except that the copy FROM path is the source tree.

#### Scenario: Copyable framework-owned assets are listed
- **WHEN** a team reads the baseline inventory
- **THEN** documentation lists `assets/cursor/rules/sdd-*`, `assets/cursor/skills/sdd-*`, `assets/cursor/agents/sdd-*`, `assets/cursor/commands/sdd-*` when those assets exist, and `docs/sdd-framework/` as the methodology snapshot destination
- **AND** it does not require those `sdd-*` files to exist for the baseline to be complete
- **AND** it does not list this repository's `.cursor/**/sdd-*` as the copy FROM inventory

#### Scenario: Never-transferred assets are listed
- **WHEN** a team reads the baseline inventory
- **THEN** documentation forbids transferring this repository's `openspec/specs/`, OpenSpec change history, `AGENTS.md`, `README.md`, and git metadata into a consuming project as adopted baseline

#### Scenario: Zero Cursor assets remain a complete subset
- **WHEN** a consuming project copies the published subset and this repository contains no `sdd-*` Cursor files
- **THEN** documentation treats the methodology snapshot as a complete copy/pin baseline
- **AND** it does not treat missing `sdd-*` files as a defect or incomplete adoption

### Requirement: Cursor landing paths
Copied framework-owned Cursor assets SHALL land in the consuming project's project-root `.cursor/` tree under the primitive-matched paths already reserved for `sdd-*`. That landing tree SHALL be the installed Cursor load path. It SHALL NOT be described as the framework source tree. The methodology snapshot SHALL land at `docs/sdd-framework/` in the consuming project. Canonical methodology in this repository SHALL remain under `docs/`. Copied `sdd-*` assets SHALL remain framework-owned after copy. A consuming project SHALL NOT overwrite them in place with product-specific behavior.

#### Scenario: Cursor assets land where Cursor loads them
- **WHEN** a consuming project adopts framework-owned Cursor assets
- **THEN** documentation requires those files to be placed under the consuming project's project-root `.cursor/` tree
- **AND** it does not treat a nested vendor directory as a valid Cursor load path for those assets
- **AND** it does not treat `assets/cursor/` in the consuming project as a valid Cursor load path

#### Scenario: Methodology snapshot has a reserved path
- **WHEN** a consuming project takes a methodology snapshot
- **THEN** documentation requires the snapshot at `docs/sdd-framework/`
- **AND** it forbids merging that snapshot into the consuming project's product documentation root as if it were product architecture

#### Scenario: Copied namespace stays framework-owned
- **WHEN** a consuming project has received framework `sdd-*` assets
- **THEN** those names remain framework-owned
- **AND** the project is not permitted to overwrite them with project-specific behavior under the same names
