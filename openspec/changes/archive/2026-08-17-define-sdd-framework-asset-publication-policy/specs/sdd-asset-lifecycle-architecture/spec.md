## ADDED Requirements

### Requirement: Published baseline may contain zero Cursor assets
The documented asset lifecycle SHALL state that a published framework baseline MAY contain zero framework-owned `sdd-*` Cursor files. Publication of a baseline SHALL NOT require any `sdd-*` rule, skill, command, or agent to exist. The methodology, architecture, and OpenSpec governance SHALL remain sufficient as the published baseline when those Cursor files are absent.

#### Scenario: Empty Cursor subset is a published baseline
- **WHEN** a reader consults how a framework baseline is published
- **THEN** documentation states that the published baseline may contain zero `sdd-*` Cursor files
- **AND** it does not require Cursor assets to exist in order to publish

#### Scenario: Methodology-only baseline is sufficient
- **WHEN** the repository has complete methodology, architecture, and OpenSpec governance and no `sdd-*` Cursor files
- **THEN** documentation describes that state as a valid published baseline
- **AND** it does not describe Cursor assets as missing pieces of that baseline

### Requirement: Absence of Cursor assets is not incompleteness
The documented asset lifecycle SHALL state that absence of framework-owned `sdd-*` files is not an incomplete implementation of the framework. A contributor SHALL NOT treat empty `.cursor/` `sdd-*` paths as unfinished foundation work.

#### Scenario: Empty sdd paths are not a defect
- **WHEN** a contributor inspects the repository and finds no `sdd-*` Cursor files
- **THEN** documentation classifies that absence as a valid complete state
- **AND** it forbids treating that absence as an implementation gap that must be filled to complete the framework

### Requirement: No planned asset catalog
The documented asset lifecycle SHALL forbid a planned-name catalog, future-asset inventory, or catalog document that lists `sdd-*` assets to create. The published inventory SHALL remain the path patterns of files that exist. This capability SHALL NOT introduce a catalog page, a backlog of asset names, or empty stubs so that a catalog appears populated.

#### Scenario: Planned-name inventory is rejected
- **WHEN** a contributor plans a document or change whose purpose is to list future `sdd-*` names to implement
- **THEN** documentation forbids that inventory
- **AND** it states that no planned asset catalog exists

#### Scenario: Existing files remain the inventory
- **WHEN** a reader looks for the current set of framework-owned Cursor assets
- **THEN** documentation directs them to existing `.cursor/**/sdd-*` files and the adoption path patterns
- **AND** it does not provide a separate catalog of intended names

### Requirement: Example names are not creation intent
When architecture documentation uses `sdd-*` names as examples, those names SHALL be non-normative illustrations of naming shape. They SHALL NOT be described as assets to create, as a backlog, or as publication intent.

#### Scenario: Example name is not a work item
- **WHEN** a reader encounters an example such as a sample `sdd-*` skill, rule, or agent name in architecture documentation
- **THEN** documentation labels that name as a non-normative example
- **AND** it does not present that name as an asset the framework intends to create

### Requirement: Future assets are individual OpenSpec changes
Each framework-owned Cursor asset that is later created SHALL be justified by its own OpenSpec change that follows this lifecycle, including classification, evidence of repetition, and human acceptance. One change MAY create a skill and its optional command. A change SHALL NOT create a catalog of assets. This capability SHALL NOT change classification order, creation criteria, stages, ownership, validation, versioning, deprecation, or retirement already specified by this architecture.

#### Scenario: First asset is a per-asset change
- **WHEN** a contributor wants the first `sdd-*` Cursor file to exist
- **THEN** documentation requires a dedicated OpenSpec change for that asset that follows this lifecycle
- **AND** it forbids bundling a catalog of unrelated assets into that change

#### Scenario: Lifecycle model stays unchanged
- **WHEN** this publication policy is applied
- **THEN** classification, creation evidence, conceptual stages, ownership, validation, versioning, deprecation, and retirement remain as already specified
- **AND** documentation does not introduce a new lifecycle stage for catalogs

## MODIFIED Requirements

### Requirement: Operating model without catalog implementation
This capability SHALL define the asset lifecycle without requiring any framework-owned `sdd-*` rule, skill, command, or agent file to exist. It SHALL NOT introduce an installer, synchronization tool, manifest file, release automation, workflow engine, asset-management runtime, MCP integration, hook, plugin, template catalog, example assets, or a planned-name catalog. Empty stubs SHALL NOT be a catalog. Later creation of framework-owned Cursor assets SHALL use per-asset OpenSpec changes that follow this lifecycle. This capability SHALL NOT require a catalog change.

#### Scenario: Architecture change adds no Cursor catalog
- **WHEN** this change is applied
- **THEN** no `sdd-*` Cursor rules, skills, commands, or agents are required to exist
- **AND** the documented lifecycle is sufficient for later per-asset OpenSpec changes to add them
- **AND** it does not require a catalog document or planned-name inventory

#### Scenario: No tooling or engine is specified
- **WHEN** a contributor looks for an installer, manifest, release tool, workflow engine, or asset-management runtime in this change
- **THEN** documentation states that those are out of scope
- **AND** it states that humans invoke OpenSpec stages and Cursor executes assets
