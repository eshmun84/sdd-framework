## ADDED Requirements

### Requirement: Workflow-system architecture documentation
The documentation tree SHALL include an architecture page that is the authoritative description of the SDD workflow operating model. The documentation index SHALL link to that page. `docs/architecture/overview.md` SHALL remain the four-layer relationship summary, SHALL point to the workflow-system page, and SHALL NOT contain the full workflow operating model or add a fifth architecture layer. `docs/lifecycle/openspec-workflow.md` SHALL remain the vendor OpenSpec surface, SHALL point to the workflow-system page for the collaboration model, and SHALL NOT own a second copy of that model. `docs/practices/human-ai-interaction.md` SHALL remain the prompting practice, SHALL point to the workflow-system page for collaboration stages, and SHALL NOT own a second copy of that model. `docs/governance/working-agreements.md` SHALL remain this-repository governance, SHALL point to the workflow-system page for the shared collaboration model, and SHALL NOT own a second full copy. `README.md` and `AGENTS.md` SHALL summarize or link to the workflow-system page and SHALL NOT own a second full copy.

#### Scenario: Workflow-system page exists
- **WHEN** the architecture documentation is inspected
- **THEN** a workflow-system page exists under `docs/architecture/`
- **AND** that page describes workflow identity, lifecycle stages and boundaries, participant responsibilities, durable versus temporary information, human approval gates, review without a vendor command, incomplete and rejected work, and applicability to framework and consuming-project OpenSpec universes

#### Scenario: Documentation index links to workflow-system
- **WHEN** a reader opens `docs/README.md`
- **THEN** the index links to the workflow-system architecture page

#### Scenario: Overview stays the four-layer summary
- **WHEN** a reader opens `docs/architecture/overview.md`
- **THEN** the page remains the four-layer relationship summary
- **AND** it points to the workflow-system page for the collaboration operating model
- **AND** it does not add a fifth architecture layer
- **AND** it does not reproduce that operating model in full

#### Scenario: Lifecycle page stays the vendor OpenSpec surface
- **WHEN** a reader opens `docs/lifecycle/openspec-workflow.md`
- **THEN** the page remains the description of the installed OpenSpec command surface
- **AND** it points to the workflow-system page for the SDD collaboration model
- **AND** it does not reproduce that collaboration model in full

#### Scenario: Practice and governance pages do not copy the workflow
- **WHEN** a reader opens `docs/practices/human-ai-interaction.md` or `docs/governance/working-agreements.md`
- **THEN** those pages point to the workflow-system page for the shared collaboration model
- **AND** they do not own a second full copy of that model

#### Scenario: Entrypoints do not copy the operating model
- **WHEN** a human or agent looks for SDD workflow operating rules
- **THEN** `README.md` and `AGENTS.md` summarize or link to the workflow-system page
- **AND** they do not own a second full copy of the operating model
