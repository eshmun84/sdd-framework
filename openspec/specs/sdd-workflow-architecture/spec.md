# sdd-workflow-architecture Specification

## Purpose

Defines the SDD Framework workflow operating model — how humans, optional planning assistants, Cursor, OpenSpec, and implementation work collaborate through a change from intent to archived contract — without creating automation or restating existing primitive operating models.

## Requirements

### Requirement: Workflow identity is a collaboration operating model
The documented workflow SHALL describe the SDD workflow as the operating model for how participants collaborate through one change. It SHALL distinguish that model from the four architecture layers, from Cursor primitives, from prompting practice, from vendor OpenSpec command behavior, and from project adoption, without restating those models in full. The workflow SHALL NOT be described as a fifth architecture layer, a workflow engine, an OpenSpec wrapper, a prompt catalog, or a stored artifact type.

#### Scenario: Operating model is distinct from existing homes
- **WHEN** a reader consults the workflow-system architecture documentation
- **THEN** the SDD workflow is described as a collaboration operating model for a change
- **AND** it is distinguished from the four-layer architecture, Cursor primitives, human-AI prompting practice, vendor OpenSpec command behavior, and adoption without copying those pages in full

#### Scenario: Workflow is not a layer or engine
- **WHEN** documentation describes what the SDD workflow is not
- **THEN** it states that the workflow is not a fifth architecture layer, a workflow engine, an OpenSpec wrapper, a prompt catalog, or a stored artifact type

### Requirement: Canonical change lifecycle is conceptual not a vendor sequence
The documented workflow SHALL describe a canonical change lifecycle whose primary stages are intake, explore, propose, apply, review, and archive. Update and sync SHALL be described as loop-backs, not additional primary stages. Maintenance SHALL be described as a new change after archive, not as a vendor command. Those stages SHALL be identified as conceptual collaboration stages. The documented workflow SHALL NOT present them as a mandatory OpenSpec command sequence. Vendor `/opsx-*` command behavior SHALL remain defined by OpenSpec.

#### Scenario: Primary stages are named
- **WHEN** a reader consults the workflow lifecycle
- **THEN** intake, explore, propose, apply, review, and archive are named as primary stages
- **AND** update and sync are described as loop-backs
- **AND** maintenance is described as starting a new change rather than mutating an archived change

#### Scenario: Stages are not a mandatory command sequence
- **WHEN** documentation presents the change lifecycle
- **THEN** it identifies the stages as conceptual collaboration stages
- **AND** it does not require that OpenSpec commands be invoked only in that sequence
- **AND** it states that command behavior remains defined by vendor OpenSpec assets

#### Scenario: Explore may be skipped when intent is already bounded
- **WHEN** a change's problem, scope, and non-goals are already clear
- **THEN** the documented workflow allows proposing without a prior explore invocation
- **AND** it does not require every change to run explore

### Requirement: Participants have distinct responsibilities
The documented workflow SHALL assign intent, universe selection, stage gates, approval, and rejection to the human. It SHALL assign repository inspection, OpenSpec execution, edits, and local validation to Cursor. It SHALL assign the requirement contract and lifecycle artifacts to OpenSpec. It SHALL assign implementation of an approved change to the implementation environment, which this model names as Cursor applying that change. An external planning assistant SHALL be optional and, when used, SHALL be limited to analysis, alternatives, and disposable execution briefs. The planning assistant SHALL NOT inspect the repository, implement a change, or create OpenSpec artifacts. Later `sdd-*` skills, rules, and agents SHALL remain reusable execution assets and SHALL NOT own the lifecycle.

#### Scenario: Human owns gates
- **WHEN** a reader consults participant responsibilities
- **THEN** the human is described as owning intent, universe selection, approval, and rejection
- **AND** Cursor is not described as the owner of the requirement contract

#### Scenario: Planning assistant is optional and non-authoritative
- **WHEN** documentation describes an external planning assistant
- **THEN** that participant is described as optional
- **AND** it is limited to analysis, alternatives, and disposable execution briefs
- **AND** it is forbidden from inspecting the repository, implementing a change, or creating OpenSpec artifacts

#### Scenario: OpenSpec owns the contract
- **WHEN** documentation assigns lifecycle artifact ownership
- **THEN** OpenSpec is described as owning requirements, design decisions, and change artifacts
- **AND** Cursor is described as executing vendor OpenSpec commands rather than replacing specifications

### Requirement: Stage boundaries define start, end, and durable output
The documented workflow SHALL state when each primary stage begins and ends and what durable output, if any, that stage produces. Intake SHALL begin with human intent and SHALL end when the idea is discarded, exploration is warranted, or the work is ready to propose. Explore SHALL produce understanding and MAY produce no durable artifacts. Propose SHALL produce the OpenSpec change artifacts that constitute the contract. Apply SHALL implement only an approved change. Review SHALL judge work against that contract. Archive SHALL finalize the change so main specifications remain the durable requirement source.

#### Scenario: Intake precedes an OpenSpec change
- **WHEN** a reader consults what happens before an OpenSpec change exists
- **THEN** documentation describes an intake phase with no required durable artifacts
- **AND** it states that the phase ends by discarding the idea, exploring, or proposing

#### Scenario: Propose creates the contract
- **WHEN** documentation describes the propose stage
- **THEN** it states that propose begins when a human asks to create a change
- **AND** it states that propose ends when proposal, specifications, tasks, and design when needed exist and a human has accepted them as the contract

#### Scenario: Apply follows an approved contract
- **WHEN** a prompt asks to implement repository work that has no approved OpenSpec change
- **THEN** the documented workflow classifies that request as incorrect
- **AND** it directs the work to propose or update rather than treating the prompt as the contract

### Requirement: Durable information leaves the session; temporary information does not
The documented workflow SHALL require that behavior, decisions, and constraints that would still matter after the conversation ends be recorded in the OpenSpec artifact that owns that kind of truth. Session-only instruction, discarded alternatives after a design records the choice, and this-turn constraints SHALL remain temporary. Chat history SHALL NOT be treated as specification. The workflow SHALL use the existing prompt-versus-specification meanings and SHALL NOT restate the human-AI interaction practice in full.

#### Scenario: Surviving requirements enter OpenSpec
- **WHEN** conversation produces system behavior that would still matter after the chat ends and that behavior is not already specified
- **THEN** the documented workflow requires that behavior to be recorded as an OpenSpec requirement or design decision
- **AND** it forbids leaving that behavior only in a prompt or chat history

#### Scenario: Session instruction stays temporary
- **WHEN** documentation distinguishes durable from temporary information
- **THEN** this-turn constraints, prompt wording, and discarded alternatives after a recorded choice are described as temporary
- **AND** proposal, specifications, design decisions, and tasks are described as durable change artifacts

### Requirement: Human approval controls contract creation and lifecycle progression
The documented workflow SHALL require human approval before an OpenSpec change is treated as the contract, before implementation of that contract proceeds as approved work, and before archive. Cursor MAY recommend that a stage is ready. Cursor SHALL NOT treat its own recommendation as approval. Universe selection — framework OpenSpec, consuming-project OpenSpec, or adoption update — SHALL be a human decision recorded during intake or propose.

#### Scenario: Artifacts are not the contract until accepted
- **WHEN** OpenSpec planning artifacts have been generated but a human has not accepted them
- **THEN** the documented workflow does not treat those artifacts as an approved contract
- **AND** it does not treat apply as authorized by artifact existence alone

#### Scenario: Universe selection is explicit
- **WHEN** new work is taken in
- **THEN** documentation requires selecting whether the work belongs in this repository's framework OpenSpec, a consuming project's product OpenSpec, or the adoption update path
- **AND** it forbids recording product requirements in this repository's OpenSpec workspace

### Requirement: Review is a workflow stage without a vendor command
The documented workflow SHALL include review as a primary collaboration stage whose job is to judge implementation against the approved contract. Review SHALL NOT be specified as a new OpenSpec command, a wrapper around `/opsx-*`, or a required `sdd-*` skill or agent. Review findings SHALL refer to existing specifications or tasks and SHALL NOT invent a second acceptance list. A later change MAY encode review as a skill or specialist agent using the existing cheapest-fitting-primitive tests; this capability SHALL NOT require those assets to exist.

#### Scenario: Review has no vendor command
- **WHEN** a reader looks for a review command in the workflow
- **THEN** documentation describes review as an SDD collaboration stage
- **AND** it states that review is not an OpenSpec command
- **AND** it forbids creating an `sdd-*` command or skill whose purpose is to wrap or replace `/opsx-*`

#### Scenario: Review does not create a second spec
- **WHEN** review produces findings
- **THEN** those findings are described as judgments against the existing contract
- **AND** documentation forbids using review to add acceptance criteria that are not in OpenSpec

#### Scenario: Missing requirements return to propose or update
- **WHEN** review discovers behavior that should remain true and is not in the approved change
- **THEN** the documented workflow directs that behavior to propose or update
- **AND** it forbids applying the new behavior from the review prompt alone

### Requirement: Incomplete, rejected, and evolving work have defined handling
The documented workflow SHALL allow exploration that produces no artifacts. A rejected proposal SHALL NOT be applied and SHALL NOT survive as a prompt-only specification. Incomplete implementation SHALL be completed or explicitly accepted as incomplete before archive. When implementation reveals that the contract is wrong, the workflow SHALL require update of the open change or a new change, and SHALL prefer a new change over expanding an in-flight change past its non-goals. File deletion or archive mechanics for unused changes SHALL remain defined by OpenSpec.

#### Scenario: Dropped exploration is valid
- **WHEN** exploration ends without a decision to propose
- **THEN** the documented workflow allows that outcome
- **AND** it does not require durable artifacts from that exploration

#### Scenario: Rejected proposal is not applied
- **WHEN** a human rejects a proposed change
- **THEN** documentation forbids applying that change
- **AND** it forbids treating the originating prompt as the surviving specification

#### Scenario: Contract drift is not applied in place
- **WHEN** implementation work needs behavior that is not in the approved change
- **THEN** the documented workflow requires update or a new change
- **AND** it prefers a new change when the in-flight change would expand past its non-goals

### Requirement: Same workflow applies in independent OpenSpec universes
The documented workflow SHALL apply to this repository and to consuming projects that use OpenSpec. This repository's OpenSpec workspace SHALL remain the framework requirement universe. A consuming project's OpenSpec workspace SHALL remain that product's requirement universe. Consuming projects SHALL NOT import this repository's OpenSpec specifications as product specs. The workflow SHALL NOT define product-specific lifecycles. Adoption update of copied framework assets SHALL remain distinct from a product OpenSpec change.

#### Scenario: Framework and product follow the same stages
- **WHEN** a consuming project that uses OpenSpec specifies product work
- **THEN** documentation requires that project to use the same collaboration stages
- **AND** it requires that work to live in that project's OpenSpec workspace

#### Scenario: Universes stay isolated
- **WHEN** documentation describes workflow applicability
- **THEN** it forbids copying this repository's OpenSpec specifications into a consuming project as product requirements
- **AND** it forbids adding consuming-project product requirements to this repository's OpenSpec workspace

#### Scenario: Adoption update is not a product change
- **WHEN** a consuming project takes a newer framework baseline
- **THEN** documentation describes that work as the adoption update path
- **AND** it does not describe that update as a product OpenSpec change in this repository

### Requirement: Workflow is not an engine and does not require catalog assets
The framework SHALL NOT introduce a workflow engine, orchestrator runtime, hooks, MCP integration, plugin, or automation that runs the change lifecycle. The framework SHALL NOT wrap, rename, or redefine vendor `/opsx-*` commands or `openspec-*` skills. This capability SHALL define the operating model without requiring any `sdd-*` Cursor file, prompt library, or implementation environment beyond Cursor applying an approved change. Absence of those files SHALL remain valid.

#### Scenario: No engine or integration is specified
- **WHEN** a contributor looks for a workflow engine, hooks, MCP integration, plugin, or orchestrator runtime in this change
- **THEN** documentation states that those are out of scope
- **AND** it states that humans invoke stages and Cursor executes the named vendor command

#### Scenario: Vendor OpenSpec surface stays unwrapped
- **WHEN** a contributor plans a framework-owned command or skill whose purpose is explore, propose, apply, update, sync, or archive
- **THEN** documentation forbids creating that asset
- **AND** it directs the contributor to the vendor `opsx-*` / `openspec-*` surface

#### Scenario: Architecture change adds no catalog or automation
- **WHEN** this change is applied
- **THEN** no `.cursor/` asset, `sdd-*` catalog file, prompt library, or workflow script is required to exist
- **AND** the documented operating model is sufficient for later changes to add skills, agents, or rules that operate inside a stage

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

### Requirement: An approved change bounds allowed implementation work
The documented workflow SHALL describe an approved OpenSpec change in the current repository's workspace as the bound on allowed implementation work. That bound SHALL be the change's proposal, including its scope and non-goals, its specifications, its design when present, and its tasks. The workflow SHALL NOT define that bound as a file allowlist, path inventory, CODEOWNERS map, or project-management backlog. The workflow SHALL keep OpenSpec as the requirement contract for that bound.

#### Scenario: Contract artifacts are the bound
- **WHEN** a reader consults what implementation may do for an approved change
- **THEN** documentation describes allowed work as that change's proposal, specifications, design when present, tasks, and non-goals
- **AND** it refers to the current repository's OpenSpec workspace
- **AND** it states that OpenSpec remains the requirement contract

#### Scenario: Filesystem and project-management fences are absent
- **WHEN** a reader looks for a file allowlist, path inventory, or backlog as the definition of Apply scope
- **THEN** documentation does not specify those practices
- **AND** it keeps the concern limited to the approved change's contract artifacts

### Requirement: Apply does not add requirements or tasks
During Apply, the documented workflow SHALL forbid adding requirements, design decisions, or task items that are not already in the approved change. Checking off existing tasks SHALL remain Apply. Adding new task items SHALL be classified as update or a new change, not Apply. The workflow SHALL forbid applying those additions from the implementation prompt alone.

#### Scenario: New requirements and tasks are not Apply
- **WHEN** implementation would add a requirement, design decision, or new task item that is not in the approved change
- **THEN** the documented workflow classifies that addition as incorrect for Apply
- **AND** it requires update or a new change instead of applying the addition from the implementation prompt

#### Scenario: Completing existing tasks remains Apply
- **WHEN** Apply marks an existing authorized task as complete
- **THEN** the documented workflow treats that completion as Apply
- **AND** it does not classify checking off an existing task as expanding the contract

### Requirement: Apply does not perform unsolicited improvements outside the contract
The documented workflow SHALL forbid implementation work that the approved change does not oblige, including adjacent improvements, cleanup, or refactors that are not required to fulfill the contract. Mechanical edits that the approved contract obliges SHALL remain allowed. When extra work should remain true after the conversation, the workflow SHALL require update or a new change rather than applying that work from Apply. The workflow SHALL prefer a new change when the in-flight change would expand past its non-goals.

#### Scenario: Unsolicited adjacent work is forbidden
- **WHEN** Apply would include an improvement, cleanup, or refactor that the approved contract does not oblige
- **THEN** the documented workflow classifies that work as incorrect for Apply
- **AND** it forbids applying that work from the implementation prompt

#### Scenario: Obligated mechanical edits remain allowed
- **WHEN** fulfilling the approved contract requires a mechanical edit
- **THEN** the documented workflow treats that edit as in-scope Apply work
- **AND** it does not classify obligated mechanical edits as unsolicited improvements

#### Scenario: Surviving extra work returns to the lifecycle
- **WHEN** extra work discovered during Apply should remain true and is not in the approved change
- **THEN** the documented workflow requires update or a new change
- **AND** it prefers a new change when the in-flight change would expand past its non-goals
