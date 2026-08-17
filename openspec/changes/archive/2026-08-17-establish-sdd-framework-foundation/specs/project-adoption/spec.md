## Purpose

Defines how consuming software projects adopt the SDD Framework as a versioned Cursor-context baseline without mixing product specifications or coupling runtime systems to the framework.

## ADDED Requirements

### Requirement: Consuming project ownership
A consuming project SHALL retain ownership of its product requirements, application architecture, business domain, source code, OpenSpec lifecycle, OpenSpec specifications, and project-specific Cursor extensions.

#### Scenario: Product specifications stay in the project
- **WHEN** a consuming project specifies product behavior
- **THEN** that behavior is recorded in the consuming project's own OpenSpec workspace
- **AND** it is not recorded in this repository's OpenSpec specifications

#### Scenario: Project-specific Cursor extensions are allowed
- **WHEN** a consuming project needs local Cursor assets beyond the framework baseline
- **THEN** those extensions remain owned by the consuming project
- **AND** they do not become part of the SDD Framework unless promoted through this repository's OpenSpec lifecycle

### Requirement: Versioned Cursor-context adoption
The framework SHALL define an adoption contract in which consuming projects eventually install or synchronize a versioned set of framework assets into their Cursor project context. The contract SHALL be architectural in this change and SHALL NOT require an installer or synchronization mechanism to exist yet.

#### Scenario: Adoption contract is documented
- **WHEN** a team reads the adoption documentation
- **THEN** they are told that consuming projects will take a versioned framework baseline into Cursor context
- **AND** they are told that the installer or synchronization mechanism is a future change

#### Scenario: No installer is required for the foundation
- **WHEN** the foundation change is applied
- **THEN** no bootstrap CLI, installer, or automated sync tool is required to exist
- **AND** the documented contract remains the source of truth for later implementation

### Requirement: Runtime and production decoupling
The SDD Framework SHALL NOT be coupled to a consuming project's runtime application or production deployment. Adoption SHALL affect engineering workflow assets and documentation, not production executables, services, or runtime configuration.

#### Scenario: Framework is not a runtime dependency
- **WHEN** a reader consults the adoption contract
- **THEN** the framework is described as an engineering baseline for specification and Cursor-assisted development
- **AND** it is not described as a library, service, or production dependency of consuming applications
