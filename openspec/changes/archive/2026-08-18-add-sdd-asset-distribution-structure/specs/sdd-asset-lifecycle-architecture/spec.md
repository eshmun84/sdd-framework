## ADDED Requirements

### Requirement: Source tree is the published inventory home
Implement of a framework-owned Cursor asset SHALL write the file under `assets/cursor/` in the primitive-matched source path. Publish SHALL mean the archived asset is eligible for copy/pin from that source tree. This repository SHALL NOT install published `sdd-*` files into its own `.cursor/` tree. Cursor SHALL execute assets only after they are installed under `.cursor/` in a repository that adopted them. A primitive directory under `assets/cursor/` SHALL be created only when a published file of that primitive exists.

#### Scenario: Implement writes the source path
- **WHEN** documentation describes implementing a framework-owned Cursor asset
- **THEN** it requires the file to be written under `assets/cursor/` in the matching primitive path
- **AND** it forbids treating this repository's `.cursor/` as the published source

#### Scenario: This repository does not self-install the subset
- **WHEN** a published `sdd-*` asset exists in the source tree
- **THEN** documentation does not require a copy, symlink, or dual-commit of that asset under this repository's `.cursor/`
- **AND** it states that consuming projects receive the file through copy/pin into their `.cursor/` tree

## MODIFIED Requirements

### Requirement: Asset identity is a framework-owned Cursor primitive
The documented asset lifecycle SHALL describe an SDD Framework asset as a framework-owned Cursor reusable primitive in the `sdd-*` namespace. Supported categories SHALL be rules, skills, agents, and optional thin commands. Source paths SHALL be `assets/cursor/rules/sdd-*`, `assets/cursor/skills/sdd-*`, `assets/cursor/agents/sdd-*`, and `assets/cursor/commands/sdd-*`. Installed paths after copy/pin SHALL be `.cursor/rules/sdd-*`, `.cursor/skills/sdd-*`, `.cursor/agents/sdd-*`, and `.cursor/commands/sdd-*`. The lifecycle SHALL distinguish those assets from documentation, OpenSpec specifications, `AGENTS.md`, prompts, vendor OpenSpec Cursor files, and consuming-project Cursor extensions, without redefining those artifacts. The asset lifecycle SHALL NOT be described as a fifth architecture layer, a workflow engine, an asset-management runtime, a catalog, or a replacement for OpenSpec.

#### Scenario: Operating model names Cursor assets only
- **WHEN** a reader consults the asset-lifecycle architecture documentation
- **THEN** an SDD Framework asset is described as a framework-owned `sdd-*` Cursor primitive
- **AND** the supported categories are rules, skills, agents, and optional thin commands

#### Scenario: Source and installed paths are named
- **WHEN** documentation names where framework assets live
- **THEN** it names `assets/cursor/` as the source tree in this repository
- **AND** it names project-root `.cursor/` as the installed Cursor load path after copy/pin

#### Scenario: Non-assets are excluded
- **WHEN** documentation describes what is not an SDD Framework asset
- **THEN** it states that documentation, OpenSpec specifications, `AGENTS.md`, prompts, vendor `opsx-*` / `openspec-*` files, and consuming-project Cursor extensions are not framework assets

#### Scenario: Lifecycle is not a layer or engine
- **WHEN** documentation describes what the asset lifecycle is not
- **THEN** it states that the lifecycle is not a fifth architecture layer, a workflow engine, an asset-management runtime, a catalog, or a replacement for OpenSpec

### Requirement: Stage boundaries define start, end, and durable output
The documented lifecycle SHALL state when each conceptual stage begins and ends and what durable output, if any, that stage produces. Need SHALL begin with an observed pattern and MAY produce no durable artifacts. Classify SHALL end when a home is chosen or the need is discarded. Propose SHALL produce human-accepted OpenSpec artifacts that record type justification. Implement SHALL write the asset only for an approved change, and that durable output SHALL be the source file under `assets/cursor/`. Validate SHALL judge the implementation against that contract. Publish SHALL mean the archived asset is eligible for the published baseline subset from the source tree. Adopt and subsequent updates SHALL follow the existing copy/pin adoption contract from source to installed path. Maintain SHALL be a new OpenSpec change. Deprecate SHALL mark the asset while it remains available. Retire SHALL remove it from the published subset.

#### Scenario: Need may produce nothing durable
- **WHEN** a repeated pattern is observed but not yet classified as framework asset work
- **THEN** documentation allows that observation to remain session-only
- **AND** it does not require an OpenSpec change from observation alone

#### Scenario: Implement follows an approved contract
- **WHEN** documentation describes implementing a framework asset
- **THEN** it states that implement begins only after a human has accepted the OpenSpec change as the contract
- **AND** it forbids writing the Cursor file from classification or chat history alone
- **AND** it states that the durable implement output is the source file under `assets/cursor/`

#### Scenario: Publish is eligibility after archive
- **WHEN** documentation describes publication
- **THEN** it states that an archived asset in the published inventory paths under `assets/cursor/` is eligible for copy/pin
- **AND** it does not require git tags, releases, or publication tooling to exist for this capability

### Requirement: Adoption distributes published assets without changing copy/pin
After publication, consuming projects SHALL receive framework assets through the existing versioned copy/pin adoption contract. Copy/pin SHALL copy FROM `assets/cursor/**/sdd-*` TO the consuming project's project-root `.cursor/**/sdd-*`. Copied `sdd-*` assets SHALL remain framework-owned. The asset lifecycle SHALL use that contract and SHALL NOT restate landing paths, never-transfer inventory, vendor OpenSpec exclusion, or installer deferral. A project-named Cursor extension that encodes reusable methodology MAY be proposed as a framework asset in this repository; that local file SHALL be evidence, not an in-place rename to `sdd-*`.

#### Scenario: Adoption path is unchanged
- **WHEN** documentation describes how a consuming project receives a new framework asset
- **THEN** it describes copy/pin of the published subset from the source tree into the consuming project's Cursor load path
- **AND** it does not introduce a new distribution model such as submodule, package, installer, or OpenSpec store

#### Scenario: Project extension is evidence for promotion
- **WHEN** a consuming project has a useful non-`sdd-*` Cursor asset that is reusable methodology
- **THEN** documentation allows proposing a framework `sdd-*` asset in this repository using that project file as evidence
- **AND** it forbids renaming the project file in place to an `sdd-*` name

### Requirement: Absence of Cursor assets is not incompleteness
The documented asset lifecycle SHALL state that absence of framework-owned `sdd-*` files is not an incomplete implementation of the framework. A contributor SHALL NOT treat empty `assets/cursor/` `sdd-*` paths as unfinished foundation work.

#### Scenario: Empty sdd paths are not a defect
- **WHEN** a contributor inspects the repository and finds no `sdd-*` Cursor files in the source tree
- **THEN** documentation classifies that absence as a valid complete state
- **AND** it forbids treating that absence as an implementation gap that must be filled to complete the framework

### Requirement: No planned asset catalog
The documented asset lifecycle SHALL forbid a planned-name catalog, future-asset inventory, or catalog document that lists `sdd-*` assets to create. The published inventory SHALL remain the path patterns of files that exist under `assets/cursor/` plus the adoption path patterns. This capability SHALL NOT introduce a catalog page, a backlog of asset names, or empty stubs so that a catalog appears populated.

#### Scenario: Planned-name inventory is rejected
- **WHEN** a contributor plans a document or change whose purpose is to list future `sdd-*` names to implement
- **THEN** documentation forbids that inventory
- **AND** it states that no planned asset catalog exists

#### Scenario: Existing files remain the inventory
- **WHEN** a reader looks for the current set of framework-owned Cursor assets
- **THEN** documentation directs them to existing `assets/cursor/**/sdd-*` files and the adoption path patterns
- **AND** it does not provide a separate catalog of intended names
- **AND** it does not direct them to this repository's `.cursor/**/sdd-*` as the published inventory
