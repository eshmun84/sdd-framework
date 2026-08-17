## Purpose

Defines how humans communicate intent, context, constraints, and expected outcomes to AI-assisted development workflows so prompts initiate work without becoming a hidden specification system.

## ADDED Requirements

### Requirement: Prompt identity is a session-scoped instruction
The documented human-AI interaction practice SHALL describe a prompt as a session-scoped instruction that carries human intent and expected-output guidance for the current turn or handoff. A prompt SHALL NOT be described as a requirement, durable knowledge, methodology storage, a skill, a rule, an agent, `AGENTS.md`, or a replacement for OpenSpec. The practice SHALL distinguish a prompt from a specification (requirement contract), documentation (durable methodology or product explanation), a skill (reusable procedure), a rule (persistent constraint), and an agent (isolated specialist) without restating those operating models in full.

#### Scenario: Prompt is an instruction not a contract
- **WHEN** a reader consults the human-AI interaction practice documentation
- **THEN** a prompt is described as a session-scoped instruction of intent and expected output
- **AND** it is not described as a requirement, durable knowledge, methodology store, or OpenSpec replacement

#### Scenario: Prompt is distinguished from durable primitives
- **WHEN** documentation relates prompts to other SDD artifacts
- **THEN** it distinguishes a prompt from specifications, documentation, skills, rules, agents, and `AGENTS.md`
- **AND** it does not copy the Cursor component, agent, or skill operating models into the practice page

### Requirement: Prompts initiate work and specifications bind it
The documented practice SHALL state that a prompt initiates work, that OpenSpec specifications define the requirement contract, and that implementation follows the approved contract. Chat history SHALL NOT be treated as specification. The primary intent flow SHALL be documented as human intent to prompt to OpenSpec artifacts to implementation to validation. That flow SHALL be described as a typical orientation, not a mandatory sequence: an exploration prompt MAY produce no durable artifacts, and an implementation prompt MUST NOT introduce requirements that are not in the approved change.

#### Scenario: Contract ownership is documented
- **WHEN** a reader consults the human-AI interaction practice documentation
- **THEN** it states that the prompt initiates work
- **AND** it states that the specification defines the contract
- **AND** it states that implementation follows the approved contract
- **AND** it states that chat history is not a specification

#### Scenario: Implementation without specification is incorrect
- **WHEN** a prompt asks for repository implementation that has no approved OpenSpec change
- **THEN** the documented practice classifies that prompt as incorrect
- **AND** it directs the work to OpenSpec propose or update rather than treating the prompt as the contract

#### Scenario: Hidden requirements are incorrect
- **WHEN** a prompt states system behavior that would still matter after the conversation ends and that behavior is not already in a specification
- **THEN** the documented practice requires that behavior to be recorded as an OpenSpec requirement or design decision
- **AND** it forbids leaving that behavior only in the prompt or chat history

### Requirement: Prompts reference durable knowledge instead of copying it
Prompts SHALL reference existing project knowledge rather than pasting `AGENTS.md`, methodology documentation, or specification text. Knowledge that remains true after the conversation SHALL be recorded in documentation, OpenSpec specifications, rules, skills, or agents as already assigned by the framework. Permanent project knowledge SHALL NOT live only in prompts.

#### Scenario: Copying standing knowledge is incorrect
- **WHEN** documentation describes context management
- **THEN** it forbids pasting `AGENTS.md`, documentation chapters, or specification bodies into prompts as the normal practice
- **AND** it requires prompts to point at those sources instead

#### Scenario: Surviving knowledge is promoted out of the prompt
- **WHEN** information in a prompt would still be needed after the conversation ends
- **THEN** the documented practice requires that information to be recorded in docs, specs, rules, skills, or agents
- **AND** it does not treat the prompt as the durable store

### Requirement: Planning assistant, Cursor, and OpenSpec keep distinct responsibilities
The documented practice SHALL assign architecture discussion, analysis, alternatives, and generation of execution briefs to an external planning assistant. It SHALL assign repository inspection, OpenSpec execution, code and documentation changes, and validation to Cursor. It SHALL assign requirements, design decisions, and lifecycle artifacts to OpenSpec. The framework SHALL NOT define an AI integration layer, ChatGPT product integration, Cursor plugin, MCP integration, hook, or orchestration runtime as part of this practice. An execution brief SHALL remain a disposable prompt; it SHALL NOT be a stored framework artifact type. The practice MAY name a specific planning product as an example and SHALL use the term external planning assistant for the role.

#### Scenario: Responsibilities are separated
- **WHEN** a reader consults the human-AI interaction practice documentation
- **THEN** an external planning assistant is described as responsible for architecture discussion, analysis, alternatives, and execution briefs
- **AND** Cursor is described as responsible for repository inspection, OpenSpec execution, edits, and validation
- **AND** OpenSpec is described as responsible for requirements, design decisions, and lifecycle artifacts

#### Scenario: Planning assistant does not inspect the repository
- **WHEN** documentation describes an external planning assistant
- **THEN** it states that the assistant does not inspect the repository
- **AND** it forbids treating the assistant's output as if it had read the project files

#### Scenario: No integration layer is specified
- **WHEN** a contributor looks for ChatGPT integration, a Cursor plugin, MCP, hooks, or an orchestration runtime in this practice
- **THEN** documentation states that those are out of scope
- **AND** it does not add a fifth architecture layer beside OpenSpec, Cursor, the SDD Framework, and consuming projects

#### Scenario: Execution brief is still a prompt
- **WHEN** documentation describes an execution brief produced by a planning assistant
- **THEN** the brief is described as a disposable Cursor-oriented prompt
- **AND** it is not described as a stored artifact type, template catalog entry, or specification

### Requirement: Prompt structure is adaptive
The documented practice SHALL recommend prompt sections covering objective, scope, context, constraints, non-goals, expected output, and validation expectations. It SHALL NOT require every section in every prompt. Structure SHALL adapt to the target: an external planning assistant receives a short brief because it cannot read the repository; a Cursor prompt stays thin when `AGENTS.md`, documentation, specifications, or an `/opsx-*` command already supply the procedure and contract. Validation expectations in a prompt SHALL point at existing specifications or tasks and SHALL NOT introduce a second acceptance list.

#### Scenario: Recommended sections are not a mandatory template
- **WHEN** a reader consults prompt structure guidelines
- **THEN** the listed sections are described as recommended vocabulary
- **AND** documentation states that not every section is required in every prompt

#### Scenario: Cursor prompts do not reprint standing context
- **WHEN** documentation describes a prompt used in Cursor and durable artifacts already exist for the work
- **THEN** it requires the prompt to name the change, paths, or this-turn constraints rather than pasting standing documentation
- **AND** it allows the `/opsx-*` command to supply expected output when that command already defines it

#### Scenario: Validation expectations do not create a second spec
- **WHEN** a prompt includes validation expectations
- **THEN** the documented practice requires those expectations to refer to existing specifications or tasks
- **AND** it forbids using the prompt to add acceptance criteria that are not in OpenSpec

### Requirement: Prompts are not framework assets
The framework SHALL NOT store prompts as repository assets. It SHALL NOT create prompt folders, prompt catalogs, or prompt libraries. Repeated prompt patterns SHALL be promoted to documentation, rules, skills, or agents using the existing cheapest-fitting-primitive tests. This capability SHALL NOT require any `sdd-*` Cursor file to exist. Conceptual prompt stages (exploration, specification, implementation, review, debugging, documentation) MAY be described in the practice document and SHALL NOT be specified as a template catalog.

#### Scenario: Prompt storage is forbidden
- **WHEN** a contributor plans a `prompts/` directory, prompt catalog, or prompt library in this repository
- **THEN** documentation forbids creating that store
- **AND** it states that prompts are not framework assets

#### Scenario: Repeated patterns are promoted
- **WHEN** the same prompt pattern is reused because it encodes standing method or constraint
- **THEN** the documented practice requires promotion into documentation, a rule, a skill, or an agent as already classified by the framework
- **AND** it does not treat saving the prompt file as the reuse model

#### Scenario: Absence of prompt and catalog files is valid
- **WHEN** this change is implemented
- **THEN** documentation states that prompt files and `sdd-*` prompting assets are not created
- **AND** it states that conceptual prompt stages are not a catalog of templates to implement
