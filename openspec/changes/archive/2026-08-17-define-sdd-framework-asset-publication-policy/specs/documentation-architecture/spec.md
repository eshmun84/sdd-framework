## ADDED Requirements

### Requirement: Catalog-status wording is not a backlog
Architecture documentation, `README.md`, and `AGENTS.md` SHALL NOT present a planned `sdd-*` catalog, planned-name inventory, or future catalog change as remaining foundation work. Example `sdd-*` names used as naming illustrations SHALL be labeled non-normative and SHALL NOT be described as assets to create or as a backlog. `AGENTS.md` SHALL forbid inventing a catalog and SHALL NOT imply that a later OpenSpec change is expected to specify one.

#### Scenario: Entrypoints do not promise a catalog
- **WHEN** a human or agent reads `README.md` or `AGENTS.md`
- **THEN** those files do not describe a skill, agent, command, or rule catalog as remaining work
- **AND** `AGENTS.md` does not say that a later OpenSpec change should specify a catalog

#### Scenario: Overview does not treat catalog as later required work
- **WHEN** a reader opens `docs/architecture/overview.md`
- **THEN** the page does not describe a custom `sdd-*` catalog as a later required change
- **AND** it still points to the asset-lifecycle page for how framework Cursor assets evolve

#### Scenario: Example names stay illustrations
- **WHEN** architecture documentation shows an example `sdd-*` name
- **THEN** the name is labeled as a non-normative illustration of naming shape
- **AND** it is not presented as an item to implement

## MODIFIED Requirements

### Requirement: Human entrypoint
`README.md` at the repository root SHALL be the primary human entrypoint and SHALL provide framework identity, purpose, core principles, an architecture overview, repository navigation, a documentation entrypoint, and project status. Detailed governance SHALL remain in `docs/` and SHALL NOT be duplicated in `README.md`. Project status SHALL describe methodology, architecture, and OpenSpec governance as in place without requiring published `sdd-*` Cursor assets. Status SHALL NOT present a future `sdd-*` catalog as remaining foundation work.

#### Scenario: README covers the required overview
- **WHEN** a human opens `README.md`
- **THEN** the file states framework identity and purpose
- **AND** it lists core principles
- **AND** it summarizes the architecture
- **AND** it points to `docs/` for detailed documentation
- **AND** it states current project status as a foundational framework whose published Cursor subset may be empty
- **AND** it does not present a skill, agent, command, or rule catalog as remaining work this repository must still complete

#### Scenario: README does not replace governance docs
- **WHEN** a human looks for detailed working agreements or quality rules
- **THEN** `README.md` directs them to `docs/` rather than containing the full governance text

### Requirement: Asset-lifecycle architecture documentation
The documentation tree SHALL include an architecture page that is the authoritative description of the SDD asset lifecycle operating model. The documentation index SHALL link to that page. `docs/architecture/overview.md` SHALL remain the four-layer relationship summary, SHALL point to the asset-lifecycle page, and SHALL NOT contain the full asset lifecycle or add a fifth architecture layer. `docs/architecture/cursor-integration.md` SHALL remain the Cursor component constitution, SHALL point to the asset-lifecycle page for how assets are created and retired, and SHALL NOT own a second copy of that lifecycle. `docs/architecture/agent-system.md`, `docs/architecture/skill-system.md`, and `docs/architecture/rule-system.md` SHALL remain their type operating models, SHALL point to the asset-lifecycle page for shared creation, publication, and retirement, and SHALL NOT own a second copy of that lifecycle. `docs/architecture/adoption.md` SHALL remain the copy/pin adoption contract, SHALL point to the asset-lifecycle page for how assets become eligible to copy, and SHALL NOT own a second copy of that lifecycle. `docs/architecture/workflow-system.md` SHALL remain the change collaboration operating model, SHALL point to the asset-lifecycle page for how Cursor assets evolve, and SHALL NOT own a second copy of that lifecycle. `README.md` and `AGENTS.md` SHALL summarize or link to the asset-lifecycle page and SHALL NOT own a second full copy. The asset-lifecycle page SHALL document the publication policy that a published baseline MAY contain zero `sdd-*` files, that this absence is not incompleteness, that no planned asset catalog exists, and that each future asset requires its own OpenSpec change.

#### Scenario: Asset-lifecycle page exists
- **WHEN** the architecture documentation is inspected
- **THEN** an asset-lifecycle page exists under `docs/architecture/`
- **AND** that page describes asset identity, classification before creation, creation and evidence criteria, conceptual lifecycle stages, ownership, validation, publication, adoption relationship, maintenance, deprecation, and retirement
- **AND** that page documents the publication policy for a baseline with zero Cursor assets

#### Scenario: Documentation index links to asset-lifecycle
- **WHEN** a reader opens `docs/README.md`
- **THEN** the index links to the asset-lifecycle architecture page

#### Scenario: Overview stays the four-layer summary
- **WHEN** a reader opens `docs/architecture/overview.md`
- **THEN** the page remains the four-layer relationship summary
- **AND** it points to the asset-lifecycle page for how framework Cursor assets evolve
- **AND** it does not add a fifth architecture layer
- **AND** it does not reproduce that operating model in full

#### Scenario: Primitive and adoption pages do not copy the lifecycle
- **WHEN** a reader opens the Cursor integration, agent-system, skill-system, rule-system, adoption, or workflow-system pages
- **THEN** those pages point to the asset-lifecycle page for shared asset evolution
- **AND** they do not own a second full copy of that lifecycle

#### Scenario: Entrypoints do not copy the operating model
- **WHEN** a human or agent looks for SDD asset lifecycle operating rules
- **THEN** `README.md` and `AGENTS.md` summarize or link to the asset-lifecycle page
- **AND** they do not own a second full copy of the operating model
