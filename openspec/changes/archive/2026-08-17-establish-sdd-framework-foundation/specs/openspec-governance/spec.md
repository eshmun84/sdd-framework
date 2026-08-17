## Purpose

Defines how this repository uses OpenSpec as its specification lifecycle, including schema choice, repository context, artifact rules, and isolation of framework specifications from consuming-project specifications.

## ADDED Requirements

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
