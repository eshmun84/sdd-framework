# sdd-agent-architecture Specification

## Purpose

Defines the SDD Framework agent operating model — when an agent is justified, what it must not own, how specialists relate to the parent Cursor Agent, and how agent assets are evolved — without creating agents or restating the Cursor component constitution.

## Requirements

### Requirement: Agent identity is an isolated specialist stance
The documented agent operating model SHALL describe an SDD agent as an isolated specialist that returns independent analysis to the parent Cursor Agent. It SHALL distinguish that operating unit from `AGENTS.md` (routing contract), rules (operational constraints), skills (procedures in the current conversation), and commands (optional human triggers), without redefining those primitives. An SDD agent SHALL NOT be described as an orchestrator, a workflow engine, an OpenSpec wrapper, or a product owner.

#### Scenario: Operating model distinguishes agents from other primitives
- **WHEN** a reader consults the agent-system architecture documentation
- **THEN** an SDD agent is described as an isolated specialist that returns analysis to the parent
- **AND** it is distinguished from `AGENTS.md`, rules, skills, and commands without restating the Cursor component constitution in full

#### Scenario: Agent is not an orchestrator or lifecycle owner
- **WHEN** documentation describes what an SDD agent is not
- **THEN** it states that an SDD agent is not an orchestrator, workflow engine, OpenSpec wrapper, or product owner
- **AND** it states that the parent Cursor Agent remains the session orchestrator

### Requirement: Agent creation requires stance and isolation
A framework-owned agent SHALL be justified only when the need includes a specialized stance, independent reasoning, and context isolation. A reusable procedure that can run in the current conversation SHALL be classified as a skill, not as an agent.

#### Scenario: Procedural work is rejected as an agent
- **WHEN** a contributor plans a framework-owned asset that is a repeatable procedure and does not need isolated context
- **THEN** the documented model classifies that asset as a skill
- **AND** it does not classify it as an agent

#### Scenario: Specialist review meets the bar
- **WHEN** a contributor plans a framework-owned asset that needs a distinct specialist stance, independent judgment, and a separate context from the implementation conversation
- **THEN** the documented model allows that asset to be an agent
- **AND** it requires the isolation justification to be recorded in the OpenSpec change that would create it

### Requirement: Agents do not own lifecycle, git, implementation, or orchestration
Framework-owned agents SHALL NOT own the OpenSpec change lifecycle, git operations, product implementation decisions, or global orchestration. Those concerns SHALL remain with the parent Cursor Agent, vendor OpenSpec assets, humans, and consuming-project specifications as already assigned by the four-layer model.

#### Scenario: Forbidden ownership is documented
- **WHEN** a reader consults the agent-system architecture documentation
- **THEN** it states that SDD agents must not own OpenSpec lifecycle, git operations, product implementation decisions, or global orchestration

#### Scenario: Planned agent cannot wrap OpenSpec
- **WHEN** a contributor plans a framework-owned agent whose purpose is explore, propose, apply, update, sync, or archive
- **THEN** documentation forbids creating that agent
- **AND** it directs the contributor to the vendor `opsx-*` / `openspec-*` surface

### Requirement: SDD agents do not spawn other SDD agents
A framework-owned agent SHALL be a leaf specialist. It SHALL NOT spawn, supervise, or orchestrate another SDD agent. The framework SHALL NOT define a hierarchy of framework agents. The parent Cursor Agent SHALL remain the only orchestrator of SDD agents.

#### Scenario: Leaf constraint is documented
- **WHEN** documentation describes agent hierarchy
- **THEN** it shows the parent Cursor Agent delegating to SDD specialist agents
- **AND** it forbids an SDD agent from spawning another SDD agent
- **AND** it forbids a framework agent hierarchy or supervisor agent

### Requirement: Multi-agent work is parent-orchestrated
The documented model SHALL allow the parent Cursor Agent to launch multiple specialist agents for parallel reviews, independent analysis, or specialist validation. Specialists SHALL return results to the parent and SHALL NOT communicate with one another through a framework-defined channel. The framework SHALL NOT introduce an orchestration runtime, message bus, or supervisor agent.

#### Scenario: Parallel specialists report to the parent
- **WHEN** documentation describes multi-agent work
- **THEN** it allows the parent to launch multiple SDD specialists, including in parallel
- **AND** it states that specialists return findings to the parent
- **AND** it does not define specialist-to-specialist communication

#### Scenario: No orchestration runtime is specified
- **WHEN** a contributor looks for a framework multi-agent runtime, message bus, or supervisor agent
- **THEN** documentation states that those are out of scope
- **AND** it states that Cursor parent delegation is sufficient

### Requirement: Agent assets follow the OpenSpec lifecycle
Creating, changing, or deprecating a framework-owned agent SHALL require an OpenSpec change in this repository. A later change that implements an agent SHALL record isolation justification, the specialist stance, and forbidden ownership. Silent addition, in-place product overwrite, or undocumented deletion of a framework agent SHALL NOT be permitted.

#### Scenario: New agent needs a change
- **WHEN** a contributor wants to add a framework-owned agent
- **THEN** documentation requires an OpenSpec change that proposes, designs, and tasks that agent
- **AND** it does not permit creating the agent file outside that lifecycle

#### Scenario: Deprecation needs a change
- **WHEN** a framework-owned agent is withdrawn or replaced
- **THEN** documentation requires an OpenSpec change
- **AND** it does not permit silent deletion as the deprecation path

### Requirement: Future agent files match the project subagent contract
When a later change creates a framework-owned agent, that file SHALL live at `.cursor/agents/sdd-<role>.md` in the project Cursor tree. It SHALL NOT be distributed as a user-level agent. It SHALL be configured so it cannot edit files or run state-changing shell commands unless a later OpenSpec change justifies write access. It SHALL use the parent agent's model unless a later OpenSpec change specifies otherwise. The file body SHALL encode specialist stance and forbidden ownership and SHALL point at authoritative `docs/` rather than republishing methodology.

#### Scenario: Planned agent has a project path and sdd name
- **WHEN** a contributor plans a framework-owned agent
- **THEN** documentation requires the path `.cursor/agents/sdd-<role>.md`
- **AND** it forbids placing that agent in a user-level agent directory or in a non-`.cursor/` compatibility directory as the framework home

#### Scenario: Review agents do not write by default
- **WHEN** documentation describes the default write policy for framework agents
- **THEN** it requires that framework agents cannot edit files or run state-changing shell commands unless a later change justifies writes

#### Scenario: Agent body is stance not playbook
- **WHEN** a contributor drafts a framework-owned agent file in a later change
- **THEN** documentation requires the body to state specialist stance and forbidden ownership
- **AND** it forbids copying a methodology page from `docs/` into the agent file

### Requirement: Project agents coexist outside reserved prefixes
Consuming-project agents SHALL use names outside `opsx-*`, `openspec-*`, and `sdd-*`. They SHALL NOT overwrite framework `sdd-*` agents in place. Domain or product agents SHALL remain consuming-project Cursor extensions. Promotion into the framework SHALL require this repository's OpenSpec lifecycle.

#### Scenario: Project cannot claim sdd names
- **WHEN** a consuming project adds a local agent
- **THEN** documentation forbids naming that agent with an `opsx-*`, `openspec-*`, or `sdd-*` prefix
- **AND** it forbids overwriting a framework `sdd-*` agent with project-specific behavior under the same name

#### Scenario: Domain agents stay in the project
- **WHEN** a consuming project needs a product-domain agent
- **THEN** that agent remains a consuming-project Cursor extension
- **AND** it is not specified as an SDD Framework agent in this repository

### Requirement: Operating model without catalog implementation
This capability SHALL define the agent operating model without requiring any framework-owned `sdd-*` agent file to exist.

#### Scenario: Architecture change adds no agents
- **WHEN** this change is applied
- **THEN** no `.cursor/agents/` directory or `sdd-*` agent file is required to exist
- **AND** the documented operating model is sufficient for later changes to add agents
