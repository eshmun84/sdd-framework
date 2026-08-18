## ADDED Requirements

### Requirement: Asset-lifecycle architecture documentation
The documentation tree SHALL include an architecture page that is the authoritative description of the SDD asset lifecycle operating model. The documentation index SHALL link to that page. `docs/architecture/overview.md` SHALL remain the four-layer relationship summary, SHALL point to the asset-lifecycle page, and SHALL NOT contain the full asset lifecycle or add a fifth architecture layer. `docs/architecture/cursor-integration.md` SHALL remain the Cursor component constitution, SHALL point to the asset-lifecycle page for how assets are created and retired, and SHALL NOT own a second copy of that lifecycle. `docs/architecture/agent-system.md`, `docs/architecture/skill-system.md`, and `docs/architecture/rule-system.md` SHALL remain their type operating models, SHALL point to the asset-lifecycle page for shared creation, publication, and retirement, and SHALL NOT own a second copy of that lifecycle. `docs/architecture/adoption.md` SHALL remain the copy/pin adoption contract, SHALL point to the asset-lifecycle page for how assets become eligible to copy, and SHALL NOT own a second copy of that lifecycle. `docs/architecture/workflow-system.md` SHALL remain the change collaboration operating model, SHALL point to the asset-lifecycle page for how Cursor assets evolve, and SHALL NOT own a second copy of that lifecycle. `README.md` and `AGENTS.md` SHALL summarize or link to the asset-lifecycle page and SHALL NOT own a second full copy.

#### Scenario: Asset-lifecycle page exists
- **WHEN** the architecture documentation is inspected
- **THEN** an asset-lifecycle page exists under `docs/architecture/`
- **AND** that page describes asset identity, classification before creation, creation and evidence criteria, conceptual lifecycle stages, ownership, validation, publication, adoption relationship, maintenance, deprecation, and retirement

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
