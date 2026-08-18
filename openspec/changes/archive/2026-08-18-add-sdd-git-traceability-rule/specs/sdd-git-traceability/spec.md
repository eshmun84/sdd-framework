## Purpose

Defines the mandatory operational behavior of the single framework-owned Git traceability Cursor rule so Git ↔ OpenSpec attribution can bind the parent agent after copy/pin, without replacing the workflow operating model, Spec First, or vendor OpenSpec.

## ADDED Requirements

### Requirement: Git traceability rule encodes the attribution constraint
The framework SHALL provide one framework-owned Cursor rule whose canonical source file is `assets/cursor/rules/sdd-git-traceability.mdc`. After copy/pin, the installed file SHALL be `.cursor/rules/sdd-git-traceability.mdc` in the consuming project. This repository SHALL NOT keep a published copy of that rule under `.cursor/`. That rule SHALL bind the parent Cursor Agent without requiring invocation once installed. The rule SHALL constrain the agent so that Git work associated with an OpenSpec change in the current repository's OpenSpec workspace is attributable to that change. The rule SHALL forbid a single commit from containing work that belongs to more than one OpenSpec change. The rule SHALL state that Git history is not the specification. The rule SHALL NOT require every commit in a repository to reference an OpenSpec change. The rule SHALL NOT forbid committing propose, apply, sync, or archive work for a change when that commit is attributable to that change. The rule SHALL NOT encode a commit-message grammar.

#### Scenario: Rule file exists at the framework source path
- **WHEN** this change is applied
- **THEN** `assets/cursor/rules/sdd-git-traceability.mdc` exists
- **AND** this repository does not contain `.cursor/rules/sdd-git-traceability.mdc` as a published copy
- **AND** no additional `sdd-*` rule, skill, agent, or command file is required to exist

#### Scenario: Installed path remains the Cursor load path
- **WHEN** a consuming project has received the Git traceability rule through copy/pin
- **THEN** the installed file is `.cursor/rules/sdd-git-traceability.mdc` in that project
- **AND** Cursor loads that installed file rather than an `assets/cursor/` path in the consuming project

#### Scenario: Change-related Git work is attributable
- **WHEN** the Git traceability rule file is inspected
- **THEN** it encodes that Git work associated with an OpenSpec change in the current project's workspace must be attributable to that change
- **AND** it forbids a single commit from containing work that belongs to more than one OpenSpec change
- **AND** it states that Git history is not the specification

#### Scenario: Non-change commits and change-stage commits are not over-constrained
- **WHEN** the Git traceability rule file is inspected
- **THEN** it does not require every commit in the repository to reference an OpenSpec change
- **AND** it does not forbid committing propose, apply, sync, or archive work when the commit is attributable to that change
- **AND** it does not encode a commit-message grammar

### Requirement: Rule is a reminder not a hidden specification
The Git traceability rule SHALL remind the agent of Git ↔ OpenSpec traceability specified by `sdd-workflow-architecture`. It SHALL NOT introduce Git procedure, commit-message grammar, branching, Git tooling, workflow stages, or Spec First semantics that are not already specified. The rule body SHALL state the operational constraint and point at authoritative methodology documentation. It SHALL NOT copy methodology pages into the rule file. It SHALL NOT invoke other rules as steps.

#### Scenario: Body is constraint plus pointer
- **WHEN** a contributor reads the Git traceability rule body
- **THEN** the body states the operational must-or-must-not
- **AND** it points at existing methodology documentation for explanation
- **AND** it does not reprint the workflow page or Spec First methodology

#### Scenario: Hidden Git conventions are rejected
- **WHEN** a draft of the Git traceability rule would add Conventional Commits, commit types, branching strategy, hooks, or Git procedure
- **THEN** that draft is not a valid implementation of this capability
- **AND** `sdd-workflow-architecture` remains the requirement source of truth for traceability methodology

### Requirement: Activation binds during product work
The Git traceability rule SHALL use always-apply activation so the constraint binds during product work without invocation. The rule SHALL NOT use description-only activation. Manual `@mention` SHALL NOT be the distribution model for this rule. The rule SHALL NOT glob `openspec/**` or `docs/**`.

#### Scenario: Always-apply is recorded on the rule
- **WHEN** the Git traceability rule frontmatter is inspected
- **THEN** always-apply activation is enabled
- **AND** the rule does not rely on description matching to activate

#### Scenario: Content-tree globs are absent
- **WHEN** the Git traceability rule frontmatter is inspected
- **THEN** it does not glob `openspec/**`
- **AND** it does not glob `docs/**`

### Requirement: Rule remains valid after copy/pin
The Git traceability rule SHALL remain true after copy/pin into a consuming project. It SHALL refer to the current repository's OpenSpec workspace and Git history, not to the SDD Framework repository's identity. It SHALL NOT encode constraints that are true only inside this framework repository. Methodology pointers SHALL remain usable after methodology lands at `docs/sdd-framework/` in a consuming project. If the current repository has no OpenSpec workspace yet, the rule SHALL still forbid treating Git history as the specification.

#### Scenario: Constraint is host-repository scoped
- **WHEN** a consuming project has received the Git traceability rule through the published baseline
- **THEN** the encoded constraint refers to that project's OpenSpec workspace and Git history
- **AND** it does not state that the repository is not a product
- **AND** it does not forbid writing product specifications in that project

#### Scenario: Pointers survive the adopted docs root
- **WHEN** the Git traceability rule is used in a consuming project whose methodology snapshot is at `docs/sdd-framework/`
- **THEN** the rule's methodology pointers remain usable
- **AND** they do not assume the rule only ever runs inside the SDD Framework repository

#### Scenario: Missing OpenSpec workspace still forbids Git-as-spec
- **WHEN** the current repository has not initialized an OpenSpec workspace
- **THEN** the rule still forbids treating Git history as the specification
- **AND** it does not invent a requirement contract from commit messages

### Requirement: Rule does not wrap vendor OpenSpec or encode Git procedure
The Git traceability rule SHALL NOT wrap, rename, or redefine vendor `/opsx-*` commands or `openspec-*` skills. It SHALL NOT present explore, propose, apply, update, sync, or archive as a mandatory command sequence. It SHALL NOT encode staging, rebase, squash, amend, push, pull-request workflow, or other Git procedure. It SHALL NOT present itself as a Git skill.

#### Scenario: Vendor lifecycle stays unwrapped
- **WHEN** the Git traceability rule body is inspected
- **THEN** it does not replace or rename explore, propose, apply, update, sync, or archive
- **AND** it does not instruct the agent to run those stages in a fixed sequence

#### Scenario: Git procedure is absent
- **WHEN** the Git traceability rule body is inspected
- **THEN** it does not contain steps, inputs, and outputs for staging, committing, rebasing, squashing, pushing, or opening a pull request
- **AND** it does not present itself as a Git-workflow playbook
