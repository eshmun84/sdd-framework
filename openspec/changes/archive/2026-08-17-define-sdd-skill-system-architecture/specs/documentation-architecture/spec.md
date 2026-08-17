## ADDED Requirements

### Requirement: Skill-system architecture documentation
The documentation tree SHALL include an architecture page that is the authoritative description of the SDD skill operating model. The documentation index SHALL link to that page. `docs/architecture/cursor-integration.md` SHALL remain the Cursor component constitution and SHALL NOT contain the full skill operating model. That constitution page SHALL point to the skill-system page for operating-model detail.

#### Scenario: Skill-system page exists
- **WHEN** the architecture documentation is inspected
- **THEN** a skill-system page exists under `docs/architecture/`
- **AND** that page describes skill identity, creation criteria, skill versus agent, rule, and command, invocation policy, file contract, lifecycle, ownership, and naming

#### Scenario: Documentation index links to skill-system
- **WHEN** a reader opens `docs/README.md`
- **THEN** the index links to the skill-system architecture page

#### Scenario: Cursor integration stays the component constitution
- **WHEN** a reader opens `docs/architecture/cursor-integration.md`
- **THEN** the page remains the Cursor component constitution
- **AND** it points to the skill-system page for the skill operating model
- **AND** it does not reproduce that operating model in full

#### Scenario: Entrypoints do not copy the operating model
- **WHEN** a human or agent looks for SDD skill operating rules
- **THEN** `README.md` and `AGENTS.md` summarize or link to the skill-system page
- **AND** they do not own a second full copy of the operating model
