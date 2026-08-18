# sdd-skill-architecture Specification

## Purpose

Defines the SDD Framework skill operating model — when a skill is justified, how it differs from rules, agents, and commands, how future skill files are structured and invoked, and how skill assets are evolved — without creating skills or restating the Cursor component constitution.

## Requirements

### Requirement: Skill identity is a reusable procedure in the current conversation
The documented skill operating model SHALL describe an SDD skill as a reusable procedure that runs in the current conversation. It SHALL distinguish that operating unit from `AGENTS.md` (routing contract), rules (operational constraints), commands (optional human triggers), and agents (isolated specialists), without redefining those primitives. An SDD skill SHALL NOT be described as an independent reasoning entity, a documentation container, an orchestrator, or an OpenSpec wrapper.

#### Scenario: Operating model distinguishes skills from other primitives
- **WHEN** a reader consults the skill-system architecture documentation
- **THEN** an SDD skill is described as a reusable procedure that runs in the current conversation
- **AND** it is distinguished from `AGENTS.md`, rules, commands, and agents without restating the Cursor component constitution in full

#### Scenario: Skill is not a mind or a book
- **WHEN** documentation describes what an SDD skill is not
- **THEN** it states that an SDD skill is not an independent reasoning entity, a documentation container, an orchestrator, or an OpenSpec wrapper

### Requirement: Skill creation requires a repeatable known methodology procedure
A framework-owned skill SHALL be justified only when the need is a repeatable procedure, a known workflow, reusable methodology, and predictable inputs and outputs. Independent judgment SHALL be classified as an agent. A persistent constraint SHALL be classified as a rule. Identity or navigation SHALL remain in `AGENTS.md`. Pure documentation SHALL remain in `docs/`. OpenSpec change lifecycle work SHALL remain on the vendor `opsx-*` / `openspec-*` surface.

#### Scenario: Repeatable methodology procedure meets the bar
- **WHEN** a contributor plans a framework-owned asset that is a repeatable known procedure with predictable inputs and outputs and does not need isolated context
- **THEN** the documented model classifies that asset as a skill
- **AND** it does not classify it as an agent, a rule, or documentation

#### Scenario: Independent judgment is rejected as a skill
- **WHEN** a contributor plans a framework-owned asset whose value is independent judgment, a specialist perspective, or isolation from the implementation conversation
- **THEN** the documented model classifies that asset as an agent
- **AND** it does not classify it as a skill

#### Scenario: Persistent constraint is rejected as a skill
- **WHEN** a contributor plans a framework-owned asset whose value is an operational restriction the agent should already know
- **THEN** the documented model classifies that asset as a rule
- **AND** it does not classify it as a skill

#### Scenario: Identity and documentation are rejected as skills
- **WHEN** a contributor plans a framework-owned asset whose value is repository identity, navigation, or methodology prose
- **THEN** the documented model directs that content to `AGENTS.md` or `docs/`
- **AND** it does not classify that content as a skill

#### Scenario: OpenSpec lifecycle is rejected as a skill
- **WHEN** a contributor plans a framework-owned skill whose purpose is explore, propose, apply, update, sync, or archive
- **THEN** documentation forbids creating that skill
- **AND** it directs the contributor to the vendor `opsx-*` / `openspec-*` surface

### Requirement: Skills remain distinct from agents, rules, and commands
The documented model SHALL treat a skill as an invoked procedure in the current conversation, a rule as a persistent constraint, a command as an optional thin trigger that does not own procedure text, and an agent as an isolated specialist. The framework SHALL NOT replicate the vendor OpenSpec pattern of duplicated command-plus-skill procedure text.

#### Scenario: Skill versus agent is documented
- **WHEN** documentation compares skills and agents
- **THEN** a skill is described as a procedure that uses the current conversation
- **AND** an agent is described as requiring isolated context and independent judgment

#### Scenario: Skill versus rule is documented
- **WHEN** documentation compares skills and rules
- **THEN** a skill is described as an invoked procedure
- **AND** a rule is described as a persistent constraint

#### Scenario: Skill versus command is documented
- **WHEN** documentation compares skills and commands
- **THEN** the skill remains the canonical procedure
- **AND** a command, if it exists, is described as an optional thin trigger that shares the same `sdd-*` name
- **AND** it forbids duplicating procedure text into a command file in the OpenSpec vendor pattern

### Requirement: Invocation is explicit by default
A framework-owned skill SHALL default to explicit invocation. Description-based discovery SHALL be allowed only when the OpenSpec change that creates the skill records why ambient discovery is still a procedure and not a rule. Always-on skill behavior SHALL be forbidden; always-on behavior SHALL remain in `AGENTS.md` or rules.

#### Scenario: Default invocation is explicit
- **WHEN** a later change creates a framework-owned skill and does not justify ambient discovery
- **THEN** documentation requires that skill to be invoked explicitly
- **AND** it does not treat description matching as the default

#### Scenario: Ambient discovery needs recorded justification
- **WHEN** a later change wants a framework-owned skill to be discoverable from description without an explicit trigger
- **THEN** documentation requires that creating change to record why the asset is still a procedure and not a rule

#### Scenario: Always-on skill is forbidden
- **WHEN** a contributor plans a skill whose purpose is to be present in every session without invocation
- **THEN** documentation forbids that skill
- **AND** it directs always-on identity to `AGENTS.md` and always-on constraints to rules

### Requirement: Future skill files match the project skill contract
When a later change creates a framework-owned skill, that asset SHALL be authored at `assets/cursor/skills/sdd-<procedure>/SKILL.md` in this repository's source tree. After copy/pin, the installed file SHALL live at `.cursor/skills/sdd-<procedure>/SKILL.md` in the consuming project's Cursor tree. It SHALL NOT be distributed as a user-level skill. Optional supporting reference files SHALL remain one level deep from `SKILL.md`. `SKILL.md` SHALL encode purpose, trigger conditions, instructions, skill-local constraints, references to authoritative `docs/`, and named outputs, and SHALL NOT republish methodology pages. This architecture SHALL NOT require executable scripts inside skills.

#### Scenario: Planned skill has a source path and sdd procedure name
- **WHEN** a contributor plans a framework-owned skill
- **THEN** documentation requires the source path `assets/cursor/skills/sdd-<procedure>/SKILL.md`
- **AND** it requires the installed path `.cursor/skills/sdd-<procedure>/SKILL.md` after copy/pin
- **AND** it forbids placing that skill in a user-level skill directory as the framework home

#### Scenario: SKILL.md carries the procedure contract
- **WHEN** a contributor drafts a framework-owned skill file in a later change
- **THEN** documentation requires `SKILL.md` to include purpose, trigger conditions, instructions, constraints, references, and outputs
- **AND** it forbids copying a methodology page from `docs/` into the skill file

#### Scenario: Scripts are not part of this architecture
- **WHEN** a contributor looks for a framework requirement to ship executable scripts inside a skill
- **THEN** documentation states that scripts are out of scope for this operating model
- **AND** it does not require a `scripts/` directory for a valid skill

### Requirement: Skills do not impersonate agents or become workflow engines
A framework-owned skill SHALL NOT impersonate an agent by encoding a specialist persona without a procedure. A skill MAY name another framework skill as a step in the same conversation. A skill MAY instruct the parent Cursor Agent to delegate to a specialist when a step requires isolation. A skill SHALL NOT own agents, SHALL NOT supervise `sdd-*` agents, and SHALL NOT become a workflow engine.

#### Scenario: Persona skill is rejected
- **WHEN** a contributor plans a framework-owned skill whose body is a persona or stance without a repeatable procedure
- **THEN** the documented model rejects that asset as a skill
- **AND** it directs specialist stance with isolation to the agent operating model

#### Scenario: Skill chaining stays in the current conversation
- **WHEN** documentation describes composition of framework skills
- **THEN** it allows a skill to name another `sdd-*` skill as a step in the same conversation
- **AND** it forbids a skill from becoming a workflow engine or from supervising `sdd-*` agents

#### Scenario: Isolation steps remain parent-orchestrated
- **WHEN** a skill step requires independent judgment or isolated context
- **THEN** documentation allows the skill to instruct the parent Cursor Agent to delegate
- **AND** it states that the parent remains the orchestrator

### Requirement: Skill assets follow the OpenSpec lifecycle
Creating, changing, or deprecating a framework-owned skill SHALL require an OpenSpec change in this repository. A later change that implements a skill SHALL record why the asset is a skill rather than a rule, agent, documentation page, or vendor OpenSpec asset. Silent addition, in-place product overwrite, or undocumented deletion of a framework skill SHALL NOT be permitted.

#### Scenario: New skill needs a change
- **WHEN** a contributor wants to add a framework-owned skill
- **THEN** documentation requires an OpenSpec change that proposes, designs, and tasks that skill
- **AND** it does not permit creating the skill file outside that lifecycle

#### Scenario: Deprecation needs a change
- **WHEN** a framework-owned skill is withdrawn or replaced
- **THEN** documentation requires an OpenSpec change
- **AND** it does not permit silent deletion as the deprecation path

### Requirement: Project skills coexist outside reserved prefixes
Consuming-project skills SHALL use names outside `opsx-*`, `openspec-*`, and `sdd-*`. They SHALL NOT overwrite framework `sdd-*` skills in place. Domain or product skills SHALL remain consuming-project Cursor extensions. Promotion into the framework SHALL require this repository's OpenSpec lifecycle.

#### Scenario: Project cannot claim sdd names
- **WHEN** a consuming project adds a local skill
- **THEN** documentation forbids naming that skill with an `opsx-*`, `openspec-*`, or `sdd-*` prefix
- **AND** it forbids overwriting a framework `sdd-*` skill with project-specific behavior under the same name

#### Scenario: Product skills stay in the project
- **WHEN** a consuming project needs a product-domain or stack-specific skill
- **THEN** that skill remains a consuming-project Cursor extension
- **AND** it is not specified as an SDD Framework skill in this repository

### Requirement: Operating model without catalog implementation
This capability SHALL define the skill operating model without requiring any framework-owned `sdd-*` skill file to exist.

#### Scenario: Architecture change adds no skills
- **WHEN** this operating model is applied without a per-asset skill change
- **THEN** no `assets/cursor/skills/sdd-*` directory or skill file is required to exist
- **AND** the documented operating model is sufficient for later changes to add skills
- **AND** empty placeholder skill directories are not required
