## ADDED Requirements

### Requirement: Rule-system architecture documentation
The documentation tree SHALL include an architecture page that is the authoritative description of the SDD rule operating model. The documentation index SHALL link to that page. `docs/architecture/cursor-integration.md` SHALL remain the Cursor component constitution and SHALL NOT contain the full rule operating model. That constitution page SHALL point to the rule-system page for operating-model detail. `docs/architecture/overview.md` SHALL remain the four-layer relationship summary, SHALL point to the rule-system page, and SHALL NOT contain the full rule operating model.

#### Scenario: Rule-system page exists
- **WHEN** the architecture documentation is inspected
- **THEN** a rule-system page exists under `docs/architecture/`
- **AND** that page describes rule identity, creation criteria, decision model, activation policy, file contract, quality, lifecycle, ownership, naming, and copy-validity

#### Scenario: Documentation index links to rule-system
- **WHEN** a reader opens `docs/README.md`
- **THEN** the index links to the rule-system architecture page

#### Scenario: Cursor integration stays the component constitution
- **WHEN** a reader opens `docs/architecture/cursor-integration.md`
- **THEN** the page remains the Cursor component constitution
- **AND** it points to the rule-system page for the rule operating model
- **AND** it does not reproduce that operating model in full

#### Scenario: Overview stays the four-layer summary
- **WHEN** a reader opens `docs/architecture/overview.md`
- **THEN** the page remains the four-layer relationship summary
- **AND** it points to the rule-system page for the rule operating model
- **AND** it does not reproduce that operating model in full

#### Scenario: Entrypoints do not copy the operating model
- **WHEN** a human or agent looks for SDD rule operating rules
- **THEN** `README.md` and `AGENTS.md` summarize or link to the rule-system page
- **AND** they do not own a second full copy of the operating model
