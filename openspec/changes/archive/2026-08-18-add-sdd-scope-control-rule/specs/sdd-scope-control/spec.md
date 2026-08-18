## Purpose

Defines the mandatory operational behavior of the single framework-owned Scope control Cursor rule so the Apply-time change bound can bind the parent agent after copy/pin, without replacing the workflow operating model, Spec First, Git traceability, or vendor OpenSpec.

## ADDED Requirements

### Requirement: Scope control rule encodes the Apply-time bound
The framework SHALL provide one framework-owned Cursor rule whose canonical source file is `assets/cursor/rules/sdd-scope-control.mdc`. After copy/pin, the installed file SHALL be `.cursor/rules/sdd-scope-control.mdc` in the consuming project. This repository SHALL NOT keep a published copy of that rule under `.cursor/`. That rule SHALL bind the parent Cursor Agent without requiring invocation once installed. The rule SHALL constrain the agent so that implementation of an approved OpenSpec change in the current repository's OpenSpec workspace stays inside that change's proposal, specifications, design when present, tasks, and non-goals. The rule SHALL forbid adding requirements that are not in the approved change. The rule SHALL forbid adding new tasks during Apply. The rule SHALL forbid unsolicited improvements that the approved contract does not oblige. The rule SHALL NOT forbid checking off existing tasks during Apply. The rule SHALL NOT forbid mechanical edits that the approved contract obliges. The rule SHALL NOT encode a file allowlist. The rule SHALL require work that would leave that bound to be recorded through the existing OpenSpec change lifecycle rather than applied from the implementation prompt.

#### Scenario: Rule file exists at the framework source path
- **WHEN** this change is applied
- **THEN** `assets/cursor/rules/sdd-scope-control.mdc` exists
- **AND** this repository does not contain `.cursor/rules/sdd-scope-control.mdc` as a published copy
- **AND** no additional `sdd-*` rule, skill, agent, or command file is required to exist

#### Scenario: Installed path remains the Cursor load path
- **WHEN** a consuming project has received the Scope control rule through copy/pin
- **THEN** the installed file is `.cursor/rules/sdd-scope-control.mdc` in that project
- **AND** Cursor loads that installed file rather than an `assets/cursor/` path in the consuming project

#### Scenario: Approved-change work stays inside the contract
- **WHEN** the Scope control rule file is inspected
- **THEN** it encodes that implementation of an approved OpenSpec change in the current project's workspace must stay inside that change's proposal, specifications, design when present, tasks, and non-goals
- **AND** it forbids adding requirements that are not in the approved change
- **AND** it forbids adding new tasks during Apply
- **AND** it forbids unsolicited improvements that the approved contract does not oblige

#### Scenario: Authorized Apply work is not over-constrained
- **WHEN** the Scope control rule file is inspected
- **THEN** it does not forbid checking off existing tasks during Apply
- **AND** it does not forbid mechanical edits that the approved contract obliges
- **AND** it does not encode a file allowlist

### Requirement: Rule is a reminder not a hidden specification
The Scope control rule SHALL remind the agent of Apply-time scope control specified by `sdd-workflow-architecture`. It SHALL NOT introduce project-management methodology, file allowlists, Git policy, workflow stages, Spec First semantics, or Git traceability semantics that are not already specified. The rule body SHALL state the operational constraint and point at authoritative methodology documentation. It SHALL NOT copy methodology pages into the rule file. It SHALL NOT invoke other rules as steps.

#### Scenario: Body is constraint plus pointer
- **WHEN** a contributor reads the Scope control rule body
- **THEN** the body states the operational must-or-must-not
- **AND** it points at existing methodology documentation for explanation
- **AND** it does not reprint the workflow page, Spec First methodology, or Git traceability methodology

#### Scenario: Hidden methodology is rejected
- **WHEN** a draft of the Scope control rule would add backlogs, tickets, estimation, sprints, file allowlists, Git procedure, or Apply playbook steps
- **THEN** that draft is not a valid implementation of this capability
- **AND** `sdd-workflow-architecture` remains the requirement source of truth for Apply-scope methodology

### Requirement: Activation binds during product work
The Scope control rule SHALL use always-apply activation so the constraint binds during product work without invocation. The rule SHALL NOT use description-only activation. Manual `@mention` SHALL NOT be the distribution model for this rule. The rule SHALL NOT glob `openspec/**` or `docs/**`.

#### Scenario: Always-apply is recorded on the rule
- **WHEN** the Scope control rule frontmatter is inspected
- **THEN** always-apply activation is enabled
- **AND** the rule does not rely on description matching to activate

#### Scenario: Content-tree globs are absent
- **WHEN** the Scope control rule frontmatter is inspected
- **THEN** it does not glob `openspec/**`
- **AND** it does not glob `docs/**`

### Requirement: Rule remains valid after copy/pin
The Scope control rule SHALL remain true after copy/pin into a consuming project. It SHALL refer to the current repository's OpenSpec workspace, not to the SDD Framework repository's identity. It SHALL NOT encode constraints that are true only inside this framework repository. Methodology pointers SHALL remain usable after methodology lands at `docs/sdd-framework/` in a consuming project. If the current repository has no OpenSpec workspace yet, the rule SHALL still forbid treating the prompt as authorization to expand implementation beyond an approved change.

#### Scenario: Constraint is host-repository scoped
- **WHEN** a consuming project has received the Scope control rule through the published baseline
- **THEN** the encoded constraint refers to that project's OpenSpec workspace
- **AND** it does not state that the repository is not a product
- **AND** it does not forbid writing product specifications in that project

#### Scenario: Pointers survive the adopted docs root
- **WHEN** the Scope control rule is used in a consuming project whose methodology snapshot is at `docs/sdd-framework/`
- **THEN** the rule's methodology pointers remain usable
- **AND** they do not assume the rule only ever runs inside the SDD Framework repository

#### Scenario: Missing OpenSpec workspace still forbids prompt-as-expansion
- **WHEN** the current repository has not initialized an OpenSpec workspace
- **THEN** the rule still forbids treating the prompt as authorization to expand implementation beyond an approved change
- **AND** it does not invent a requirement contract from the prompt

### Requirement: Rule does not wrap vendor OpenSpec or encode Apply procedure
The Scope control rule SHALL NOT wrap, rename, or redefine vendor `/opsx-*` commands or `openspec-*` skills. It SHALL NOT present explore, propose, apply, update, sync, or archive as a mandatory command sequence. It SHALL NOT encode steps, inputs, and outputs for selecting a change, reading artifacts, or implementing tasks. It SHALL NOT present itself as an Apply skill.

#### Scenario: Vendor lifecycle stays unwrapped
- **WHEN** the Scope control rule body is inspected
- **THEN** it does not replace or rename explore, propose, apply, update, sync, or archive
- **AND** it does not instruct the agent to run those stages in a fixed sequence

#### Scenario: Apply procedure is absent
- **WHEN** the Scope control rule body is inspected
- **THEN** it does not contain steps, inputs, and outputs for selecting a change, reading planning artifacts, or implementing tasks
- **AND** it does not present itself as an Apply playbook
