## ADDED Requirements

### Requirement: Git records landed change work and does not replace OpenSpec
The documented workflow SHALL describe Git as the history of change work that has landed in the repository. It SHALL keep OpenSpec as the durable requirement contract. Git history and commit messages SHALL NOT be described as specifications. The workflow SHALL NOT describe Git as a fifth architecture layer.

#### Scenario: Git is history not contract
- **WHEN** a reader consults how implemented work is recorded
- **THEN** documentation describes Git as the history of landed change work
- **AND** it states that OpenSpec remains the requirement contract
- **AND** it forbids treating Git history or commit messages as the specification

#### Scenario: Git is not a layer
- **WHEN** documentation describes Git in the collaboration model
- **THEN** it does not present Git as a fifth architecture layer
- **AND** it keeps Git inside the existing workflow operating model

### Requirement: Change-related Git work is attributable to one OpenSpec change
When repository Git work is associated with an OpenSpec change in the current repository's OpenSpec workspace, the documented workflow SHALL require that work to be attributable to that change. Propose, apply, sync, and archive artifacts for a change SHALL be treated as change-related work. Attribution SHALL refer to the current repository's OpenSpec workspace. The workflow SHALL NOT require every commit in a repository to reference an OpenSpec change. The workflow SHALL NOT specify a commit-message grammar.

#### Scenario: Change work can be attributed
- **WHEN** a commit records propose, apply, sync, or archive work for an OpenSpec change
- **THEN** the documented workflow requires that commit to be attributable to that change
- **AND** attribution is described against the current repository's OpenSpec workspace

#### Scenario: Unrelated commits are not forced onto a change
- **WHEN** a commit does not contain work associated with an OpenSpec change
- **THEN** the documented workflow does not require that commit to reference an OpenSpec change
- **AND** it still forbids treating that commit as a specification

### Requirement: A commit does not mix distinct OpenSpec changes
The documented workflow SHALL forbid a single Git commit from containing work that belongs to more than one OpenSpec change. It SHALL NOT specify atomic commits per file, one commit per task, branching strategy, or Git tooling.

#### Scenario: Mixing two changes in one commit is forbidden
- **WHEN** a commit would include work that belongs to two different OpenSpec changes
- **THEN** the documented workflow classifies that commit as incorrect
- **AND** it requires the work to be recorded in separate commits each attributable to one change

#### Scenario: Git procedure stays unspecified
- **WHEN** a reader looks for staging, rebase, squash, push, pull-request, or Conventional Commits rules in the workflow
- **THEN** documentation does not specify those practices
- **AND** it keeps the concern limited to attribution, non-mixing, and Git-is-not-spec
