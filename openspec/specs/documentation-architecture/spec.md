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
