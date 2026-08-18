## Purpose

Defines the mandatory operational behavior of the single framework-owned Spec First Cursor rule so the existing specification-before-implementation contract can bind the parent agent after copy/pin, without replacing OpenSpec, methodology documentation, or archived operating models.

## ADDED Requirements

### Requirement: Spec First rule encodes the existing implementation constraint
The framework SHALL provide one framework-owned Cursor rule at `.cursor/rules/sdd-spec-first.mdc`. That rule SHALL bind the parent Cursor Agent without requiring invocation. The rule SHALL constrain the agent not to implement repository work that is not specified by an approved OpenSpec change in the current repository's OpenSpec workspace. The rule SHALL state that a prompt and chat history are not the specification. The rule SHALL require behavior that would still matter after the conversation and that is not already specified to be recorded through the existing OpenSpec change lifecycle rather than applied from the prompt. The rule SHALL NOT block implementation of work that is already in an approved OpenSpec change.

#### Scenario: Rule file exists at the framework path
- **WHEN** this change is applied
- **THEN** `.cursor/rules/sdd-spec-first.mdc` exists
- **AND** no additional `sdd-*` rule, skill, agent, or command file is required to exist

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

### Requirement: Rule is a reminder not a hidden specification
The Spec First rule SHALL remind the agent of Spec First behavior already specified by existing OpenSpec capabilities. It SHALL NOT introduce Spec First methodology, workflow stages, or OpenSpec command semantics that are not already specified. The rule body SHALL state the operational constraint and point at authoritative methodology documentation. It SHALL NOT copy methodology pages into the rule file.

#### Scenario: Body is constraint plus pointer
- **WHEN** a contributor reads the Spec First rule body
- **THEN** the body states the operational must-or-must-not
- **AND** it points at existing methodology documentation for explanation
- **AND** it does not reprint workflow, human-AI, governance, or principles pages

#### Scenario: New Spec First semantics are rejected
- **WHEN** a draft of the Spec First rule would add framework behavior that is not already in archived OpenSpec specifications
- **THEN** that draft is not a valid implementation of this capability
- **AND** the existing specifications remain the requirement source of truth

### Requirement: Activation binds during product work
The Spec First rule SHALL use always-apply activation so the constraint binds during product work without invocation. The rule SHALL NOT use description-only activation. Manual `@mention` SHALL NOT be the distribution model for this rule. The rule SHALL NOT glob `openspec/**` or `docs/**`.

#### Scenario: Always-apply is recorded on the rule
- **WHEN** the Spec First rule frontmatter is inspected
- **THEN** always-apply activation is enabled
- **AND** the rule does not rely on description matching to activate

#### Scenario: Content-tree globs are absent
- **WHEN** the Spec First rule frontmatter is inspected
- **THEN** it does not glob `openspec/**`
- **AND** it does not glob `docs/**`

### Requirement: Rule remains valid after copy/pin
The Spec First rule SHALL remain true after copy/pin into a consuming project. It SHALL refer to the current repository's OpenSpec workspace, not to the SDD Framework repository's identity. It SHALL NOT encode constraints that are true only inside this framework repository. Methodology pointers SHALL remain usable after methodology lands at `docs/sdd-framework/` in a consuming project. If the current repository has no OpenSpec workspace yet, the rule SHALL still forbid treating the prompt as the specification and SHALL still forbid implementing unspecified work from the prompt.

#### Scenario: Constraint is host-repository scoped
- **WHEN** a consuming project has received the Spec First rule through the published baseline
- **THEN** the encoded constraint refers to that project's OpenSpec workspace
- **AND** it does not state that the repository is not a product
- **AND** it does not forbid writing product specifications in that project

#### Scenario: Pointers survive the adopted docs root
- **WHEN** the Spec First rule is used in a consuming project whose methodology snapshot is at `docs/sdd-framework/`
- **THEN** the rule's methodology pointers remain usable
- **AND** they do not assume the rule only ever runs inside the SDD Framework repository

#### Scenario: Missing OpenSpec workspace still forbids prompt-as-spec
- **WHEN** the current repository has not initialized an OpenSpec workspace
- **THEN** the rule still forbids treating the prompt or chat as the specification
- **AND** it still forbids implementing unspecified repository work from that prompt

### Requirement: Rule does not wrap vendor OpenSpec assets
The Spec First rule SHALL NOT wrap, rename, or redefine vendor `/opsx-*` commands or `openspec-*` skills. It SHALL NOT present explore, propose, apply, update, sync, or archive as a mandatory command sequence. It SHALL NOT encode how to author OpenSpec artifacts.

#### Scenario: Vendor lifecycle stays unwrapped
- **WHEN** the Spec First rule body is inspected
- **THEN** it does not replace or rename explore, propose, apply, update, sync, or archive
- **AND** it does not instruct the agent to run those stages in a fixed sequence

#### Scenario: Spec authoring procedure is absent
- **WHEN** the Spec First rule body is inspected
- **THEN** it does not contain steps, inputs, and outputs for writing proposal, spec, design, or task artifacts
- **AND** it does not present itself as a spec-authoring playbook
