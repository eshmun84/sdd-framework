# openspec-governance Specification

## Purpose

Defines how this repository uses OpenSpec as its specification lifecycle, including schema choice, repository context, artifact rules, and isolation of framework specifications from consuming-project specifications.

## Requirements

### Requirement: Native spec-driven lifecycle
This repository SHALL use the native OpenSpec `spec-driven` schema and native OpenSpec change lifecycle. The framework SHALL NOT fork a custom schema in this change and SHALL NOT redefine OpenSpec command semantics.

#### Scenario: Schema remains stock spec-driven
- **WHEN** the repository OpenSpec configuration is inspected
- **THEN** the configured schema is `spec-driven`
- **AND** no project-local custom schema is required for the foundation

#### Scenario: Framework changes use OpenSpec
- **WHEN** a contributor introduces a framework change
- **THEN** the change is created and tracked through the native OpenSpec lifecycle
- **AND** implementation of that change does not bypass proposal, specification, and task artifacts required by the schema

### Requirement: Repository OpenSpec context
`openspec/config.yaml` SHALL provide repository context that identifies this repository as the SDD Framework methodology source of truth, states that implementation artifacts are documentation and tooling assets rather than application code, and states that consuming-project product specifications do not live here.

#### Scenario: Later artifact authors receive identity
- **WHEN** an agent creates a later OpenSpec artifact in this repository
- **THEN** the configured context identifies the repository as an independent SDD methodology framework
- **AND** the context constrains work away from product, domain, language, or application-stack specifics unless a future change explicitly expands that scope

### Requirement: Artifact rules
`openspec/config.yaml` SHALL define artifact rules that keep proposals scoped, keep specifications behavioral, keep designs focused on decisions, and keep tasks implementation-oriented without expanding into out-of-scope framework capabilities.

#### Scenario: Rules constrain later changes
- **WHEN** an agent writes proposal, spec, design, or task artifacts in this repository
- **THEN** configured rules require the work to stay within the SDD Framework's methodology, governance, and tooling scope
- **AND** the rules forbid introducing consuming-project product requirements into this repository

### Requirement: Framework-only specifications in this repository
This repository's OpenSpec specifications SHALL contain only SDD Framework requirements. They SHALL NOT contain consuming-project product requirements, business-domain behavior, or application-feature specifications.

#### Scenario: Specification workspace is framework-scoped
- **WHEN** `openspec/specs/` in this repository is inspected after archive of a framework change
- **THEN** each capability describes framework methodology, governance, documentation, Cursor assets, adoption, or repository contract
- **AND** no capability describes a consuming product's features

### Requirement: Lifecycle documentation defers command semantics
Lifecycle documentation SHALL describe OpenSpec phase intent (analysis, clarification, specification, implementation, synchronization, archival) and SHALL NOT restate command-level allow or forbid rules. Command behavior SHALL remain defined by vendor OpenSpec assets.

#### Scenario: Explore purpose describes intent
- **WHEN** a reader opens the lifecycle documentation purpose table
- **THEN** the Explore row describes clarification of ideas, problems, requirements, and constraints
- **AND** it states that command behavior is defined by OpenSpec
- **AND** it does not contain an absolute prohibition such as "Do not implement"

#### Scenario: Explore command surface describes intent
- **WHEN** a reader opens the installed Cursor surface table
- **THEN** the `/opsx-explore` use description is limited to discovery and clarification
- **AND** it does not contain an absolute prohibition such as "no implementation"

#### Scenario: Command permissions stay with OpenSpec
- **WHEN** a reader needs the allow or forbid rules for an OpenSpec command
- **THEN** the lifecycle page points to vendor-managed OpenSpec Cursor assets as the authority
- **AND** the page does not function as a replacement command specification

### Requirement: Lifecycle order is orientation not sequence
When lifecycle documentation presents `explore → propose → apply → sync → archive`, it SHALL identify that order as a typical orientation and SHALL NOT present it as a mandatory OpenSpec execution sequence.

#### Scenario: Typical order is qualified
- **WHEN** a reader sees the lifecycle flow diagram or equivalent list
- **THEN** the documentation identifies it as a typical orientation
- **AND** it does not require that OpenSpec commands be invoked only in that sequence
