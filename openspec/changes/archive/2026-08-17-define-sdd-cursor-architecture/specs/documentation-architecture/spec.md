## ADDED Requirements

### Requirement: Cursor integration documentation
The documentation tree SHALL include an architecture page that is the authoritative description of the Cursor component model, covering `AGENTS.md`, rules, skills, commands, and agents. The documentation index SHALL link to that page. `docs/architecture/overview.md` SHALL remain the four-layer relationship summary and SHALL NOT contain the full Cursor component constitution.

#### Scenario: Cursor integration page exists
- **WHEN** the architecture documentation is inspected
- **THEN** a Cursor integration page exists under `docs/architecture/`
- **AND** that page describes responsibilities for `AGENTS.md`, rules, skills, commands, and agents

#### Scenario: Documentation index links to Cursor integration
- **WHEN** a reader opens `docs/README.md`
- **THEN** the index links to the Cursor integration architecture page

#### Scenario: Overview stays the four-layer summary
- **WHEN** a reader opens `docs/architecture/overview.md`
- **THEN** the page remains the four-layer relationship summary
- **AND** it points to the Cursor integration page for the component constitution
- **AND** it does not reproduce that constitution in full

#### Scenario: Entrypoints do not copy the constitution
- **WHEN** a human or agent looks for Cursor component responsibilities
- **THEN** `README.md` and `AGENTS.md` summarize or link to the Cursor integration page
- **AND** they do not own a second full copy of the component model
