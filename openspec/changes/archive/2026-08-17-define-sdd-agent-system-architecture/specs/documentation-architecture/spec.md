## ADDED Requirements

### Requirement: Agent-system architecture documentation
The documentation tree SHALL include an architecture page that is the authoritative description of the SDD agent operating model. The documentation index SHALL link to that page. `docs/architecture/cursor-integration.md` SHALL remain the Cursor component constitution and SHALL NOT contain the full agent operating model. That constitution page SHALL point to the agent-system page for operating-model detail.

#### Scenario: Agent-system page exists
- **WHEN** the architecture documentation is inspected
- **THEN** an agent-system page exists under `docs/architecture/`
- **AND** that page describes agent identity, creation criteria, forbidden ownership, hierarchy, multi-agent principles, lifecycle, file contract, and naming

#### Scenario: Documentation index links to agent-system
- **WHEN** a reader opens `docs/README.md`
- **THEN** the index links to the agent-system architecture page

#### Scenario: Cursor integration stays the component constitution
- **WHEN** a reader opens `docs/architecture/cursor-integration.md`
- **THEN** the page remains the Cursor component constitution
- **AND** it points to the agent-system page for the agent operating model
- **AND** it does not reproduce that operating model in full

#### Scenario: Entrypoints do not copy the operating model
- **WHEN** a human or agent looks for SDD agent operating rules
- **THEN** `README.md` and `AGENTS.md` summarize or link to the agent-system page
- **AND** they do not own a second full copy of the operating model
