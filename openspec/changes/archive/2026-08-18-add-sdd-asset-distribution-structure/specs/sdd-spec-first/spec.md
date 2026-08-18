## MODIFIED Requirements

### Requirement: Spec First rule encodes the existing implementation constraint
The framework SHALL provide one framework-owned Cursor rule whose canonical source file is `assets/cursor/rules/sdd-spec-first.mdc`. After copy/pin, the installed file SHALL be `.cursor/rules/sdd-spec-first.mdc` in the consuming project. This repository SHALL NOT keep a published copy of that rule under `.cursor/`. That rule SHALL bind the parent Cursor Agent without requiring invocation once installed. The rule SHALL constrain the agent not to implement repository work that is not specified by an approved OpenSpec change in the current repository's OpenSpec workspace. The rule SHALL state that a prompt and chat history are not the specification. The rule SHALL require behavior that would still matter after the conversation and that is not already specified to be recorded through the existing OpenSpec change lifecycle rather than applied from the prompt. The rule SHALL NOT block implementation of work that is already in an approved OpenSpec change. The rule's functional content, activation, and copy-valid pointers SHALL remain unchanged by the source-path migration.

#### Scenario: Rule file exists at the framework source path
- **WHEN** this change is applied
- **THEN** `assets/cursor/rules/sdd-spec-first.mdc` exists
- **AND** this repository does not contain `.cursor/rules/sdd-spec-first.mdc` as a published copy
- **AND** no additional `sdd-*` rule, skill, agent, or command file is required to exist

#### Scenario: Installed path remains the Cursor load path
- **WHEN** a consuming project has received the Spec First rule through copy/pin
- **THEN** the installed file is `.cursor/rules/sdd-spec-first.mdc` in that project
- **AND** Cursor loads that installed file rather than an `assets/cursor/` path in the consuming project

#### Scenario: Implementation without an approved change is not authorized
- **WHEN** the Spec First rule file is inspected
- **THEN** it encodes that implementing repository work with no approved OpenSpec change in the current project's workspace is not authorized
- **AND** it states that a prompt or chat history is not the specification

#### Scenario: Unspecified surviving behavior is not applied from the prompt
- **WHEN** the Spec First rule file is inspected
- **THEN** it requires unspecified behavior that would still matter after the conversation to be recorded through the existing OpenSpec change lifecycle
- **AND** it forbids applying that behavior from the prompt alone

#### Scenario: Approved contract work is not blocked
- **WHEN** the Spec First rule file is inspected
- **THEN** it does not forbid implementing work that is already specified by an approved OpenSpec change in the current project's workspace

#### Scenario: Functional content is unchanged by the move
- **WHEN** the migrated Spec First rule body and frontmatter are compared with the pre-migration file
- **THEN** the operational constraint, activation, and copy-valid methodology pointers are unchanged
- **AND** the migration changes only the source location
