# documentation-architecture Specification

## Purpose

Defines the documentation tree, human and AI entrypoints, and navigation rules that make the SDD Framework understandable without duplicating governance into every file.

## Requirements

### Requirement: Documentation tree
The repository SHALL provide a `docs/` directory as the canonical location for framework methodology documentation, with an index that links to architecture, adoption, lifecycle, and governance material.

#### Scenario: Documentation index exists
- **WHEN** a reader opens `docs/README.md`
- **THEN** the page identifies itself as the documentation index
- **AND** it links to architecture, adoption, lifecycle, and governance documents

#### Scenario: Foundational topics are present
- **WHEN** the foundation documentation is inspected
- **THEN** architecture documentation describes the four-layer relationship
- **AND** adoption documentation describes the project adoption contract
- **AND** lifecycle documentation describes the OpenSpec change workflow used by this repository
- **AND** governance documentation describes working agreements for changing the framework

### Requirement: Human entrypoint
`README.md` at the repository root SHALL be the primary human entrypoint and SHALL provide framework identity, purpose, core principles, an architecture overview, repository navigation, a documentation entrypoint, and project status. Detailed governance SHALL remain in `docs/` and SHALL NOT be duplicated in `README.md`.

#### Scenario: README covers the required overview
- **WHEN** a human opens `README.md`
- **THEN** the file states framework identity and purpose
- **AND** it lists core principles
- **AND** it summarizes the architecture
- **AND** it points to `docs/` for detailed documentation
- **AND** it states current project status as a foundational framework, not a complete skill or agent catalog

#### Scenario: README does not replace governance docs
- **WHEN** a human looks for detailed working agreements or quality rules
- **THEN** `README.md` directs them to `docs/` rather than containing the full governance text

### Requirement: Agent entrypoint
`AGENTS.md` at the repository root SHALL be the primary AI-agent entrypoint. It SHALL act as a concise operational contract and routing document. It SHALL tell an agent what the repository is, where authoritative documentation lives, how OpenSpec is used, what governance applies, what boundaries must be respected, and how to locate deeper instructions. It SHALL NOT duplicate the full framework documentation.

#### Scenario: Agent can operate from AGENTS.md
- **WHEN** an AI development agent reads `AGENTS.md`
- **THEN** it can determine that this is the SDD Framework repository
- **AND** it can locate `docs/` as the documentation source of truth
- **AND** it can determine that framework changes MUST follow the native OpenSpec lifecycle
- **AND** it can determine that vendor OpenSpec assets MUST NOT be redefined
- **AND** it can determine that consuming-project product specifications MUST NOT be written here

#### Scenario: AGENTS.md stays a router
- **WHEN** `AGENTS.md` is compared with `docs/`
- **THEN** `AGENTS.md` links to deeper documents for architecture, adoption, lifecycle, and governance
- **AND** it does not reproduce those documents in full

### Requirement: Documentation non-duplication
Framework documentation SHALL assign a single authoritative location for each topic and SHALL use links from entrypoints instead of copying the same contract into multiple files.

#### Scenario: Architecture has one home
- **WHEN** a reader needs the four-layer relationship
- **THEN** the authoritative explanation lives under `docs/`
- **AND** `README.md` and `AGENTS.md` summarize or link rather than owning a second full copy

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
