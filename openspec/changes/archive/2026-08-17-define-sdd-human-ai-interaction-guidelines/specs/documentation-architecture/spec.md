## ADDED Requirements

### Requirement: Human-AI interaction practice documentation
The documentation tree SHALL include a practices area whose authoritative human-AI interaction page is `docs/practices/human-ai-interaction.md`. The documentation index SHALL link to that page. `docs/architecture/overview.md` SHALL remain the four-layer relationship summary, SHALL point to the practice page, and SHALL NOT contain the full human-AI interaction practice or add a fifth architecture layer. `docs/lifecycle/openspec-workflow.md` SHALL state that prompts initiate lifecycle work and are not specifications, and SHALL point to the practice page. `README.md` and `AGENTS.md` SHALL summarize or link to the practice page and SHALL NOT own a second full copy.

#### Scenario: Practice page exists
- **WHEN** the methodology documentation is inspected
- **THEN** a human-AI interaction page exists at `docs/practices/human-ai-interaction.md`
- **AND** that page describes prompt identity, intent flow, conceptual prompt stages, adaptive structure, context management, planning-assistant versus Cursor versus OpenSpec boundaries, quality guidelines, and storage and reuse

#### Scenario: Documentation index links to the practice
- **WHEN** a reader opens `docs/README.md`
- **THEN** the index links to the human-AI interaction practice page

#### Scenario: Overview stays the four-layer summary
- **WHEN** a reader opens `docs/architecture/overview.md`
- **THEN** the page remains the four-layer relationship summary
- **AND** it points to the human-AI interaction practice page
- **AND** it does not add a fifth architecture layer
- **AND** it does not reproduce that practice in full

#### Scenario: Lifecycle page does not treat prompts as specs
- **WHEN** a reader opens `docs/lifecycle/openspec-workflow.md`
- **THEN** the page states that prompts initiate lifecycle work and are not specifications
- **AND** it points to the human-AI interaction practice page

#### Scenario: Entrypoints do not copy the practice
- **WHEN** a human or agent looks for human-AI interaction guidelines
- **THEN** `README.md` and `AGENTS.md` summarize or link to the practice page
- **AND** they do not own a second full copy of the practice
