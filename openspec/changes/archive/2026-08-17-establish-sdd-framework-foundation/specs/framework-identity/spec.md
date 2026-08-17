## Purpose

Defines what the SDD Framework repository is, what it is not, and how its responsibilities stay separated from OpenSpec, Cursor, and consuming projects.

## ADDED Requirements

### Requirement: Independent methodology repository
The repository SHALL identify itself as an independent, reusable Spec-Driven Development framework that is not associated with a specific product, business domain, programming language, or application framework.

#### Scenario: Human reader identifies the repository
- **WHEN** a reader opens the repository human entrypoint
- **THEN** the repository is described as a reusable SDD methodology baseline for multiple professional software projects
- **AND** it is not described as an application, product, or domain-specific system

#### Scenario: Agent reader identifies the repository
- **WHEN** an AI development agent opens the repository agent entrypoint
- **THEN** the agent is told that this repository is the SDD Framework methodology source of truth
- **AND** the agent is told that it must not treat the repository as a product codebase

### Requirement: Four-layer responsibility model
The framework SHALL document distinct responsibilities for the SDD Framework, OpenSpec, Cursor, and consuming project repositories, and SHALL NOT assign one layer's responsibilities to another.

#### Scenario: OpenSpec ownership is documented
- **WHEN** a reader consults the architecture documentation
- **THEN** OpenSpec is described as owning the change lifecycle, specification artifacts, delta specifications, archival lifecycle, and specification synchronization
- **AND** the framework is not described as redefining OpenSpec command semantics

#### Scenario: Cursor ownership is documented
- **WHEN** a reader consults the architecture documentation
- **THEN** Cursor is described as the development execution environment for commands, skills, rules, and agents

#### Scenario: Framework ownership is documented
- **WHEN** a reader consults the architecture documentation
- **THEN** the SDD Framework is described as owning reusable methodology, governance, documentation standards, agent architecture, skill architecture, reusable rules, reusable templates, and adoption contracts

#### Scenario: Consuming project ownership is documented
- **WHEN** a reader consults the architecture documentation
- **THEN** consuming projects are described as owning their product requirements, application architecture, business domain, source code, their own OpenSpec lifecycle and specifications, and project-specific Cursor extensions

### Requirement: Dual identity without mixed universes
The repository SHALL present itself both as the product being evolved in this repository and as a distribution baseline for other repositories, and SHALL keep those roles from mixing specification universes.

#### Scenario: Framework is evolved here
- **WHEN** a contributor changes the SDD Framework
- **THEN** those changes are specified and tracked in this repository's OpenSpec workspace as framework requirements

#### Scenario: Product work stays in consuming projects
- **WHEN** a consuming project specifies a product feature
- **THEN** that specification is owned by the consuming project's OpenSpec workspace
- **AND** it is not added to this repository's OpenSpec specifications
