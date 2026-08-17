## Purpose

Defines how the SDD Framework uses Cursor primitives — `AGENTS.md`, rules, skills, commands, and subagents — so later framework-owned assets have a single constitution for responsibility, interaction, and lifecycle without replacing OpenSpec.

## ADDED Requirements

### Requirement: AGENTS.md remains the routing contract
`AGENTS.md` SHALL remain the primary AI-agent entrypoint. It SHALL provide repository identity, navigation, and document discovery. It SHALL NOT replace methodology documentation in `docs/` and SHALL NOT replace Cursor rules as the place for operational, file-scoped constraints.

#### Scenario: Agent locates Cursor integration architecture
- **WHEN** an AI development agent needs the Cursor component model
- **THEN** `AGENTS.md` points to the Cursor integration architecture documentation
- **AND** `AGENTS.md` does not reproduce that constitution in full

#### Scenario: Router is not a rule catalog
- **WHEN** `AGENTS.md` is compared with the documented rule model
- **THEN** `AGENTS.md` is described as a routing contract
- **AND** it is not described as the home for glob-scoped or always-apply Cursor rules

### Requirement: Rules encode operational constraints
Framework-owned Cursor rules, when later created, SHALL encode operational constraints and conventions. They SHALL NOT duplicate methodology prose from `docs/`. They SHALL point to the authoritative documentation rather than republishing it. Always-apply rules SHALL be exceptional; `AGENTS.md` SHALL remain the default always-on identity surface.

#### Scenario: Planned rule is constrained
- **WHEN** a contributor plans a framework-owned Cursor rule
- **THEN** documentation requires the rule to state an operational constraint
- **AND** it forbids copying the corresponding `docs/` methodology page into the rule

#### Scenario: Always-apply is not the default
- **WHEN** documentation describes how framework rules are applied
- **THEN** it states that always-apply rules are exceptional
- **AND** it states that `AGENTS.md` remains the default always-on router

### Requirement: Skills are canonical procedures
Framework-owned reusable procedures SHALL be defined as Cursor skills. A command SHALL NOT be the canonical copy of a procedure. A skill SHALL NOT be treated as a subagent.

#### Scenario: Procedure lives in a skill
- **WHEN** a contributor plans a framework-owned reusable procedure
- **THEN** documentation requires that procedure to be a skill
- **AND** it does not require a duplicated command file to hold the same procedure text

#### Scenario: Skill is not an agent
- **WHEN** documentation distinguishes skills from agents
- **THEN** a skill is described as a procedure that runs in the current conversation
- **AND** an agent is described as a specialist with isolated context

### Requirement: Commands are optional human triggers
A framework-owned Cursor command SHALL exist only when a human needs an explicit named trigger that MUST NOT fire merely because an agent judged it relevant. If a command exists for a framework procedure, it SHALL be a thin trigger for the canonical skill and SHALL share the same `sdd-*` name as that skill.

#### Scenario: Command requires a human trigger need
- **WHEN** a contributor asks whether to add a framework-owned command
- **THEN** documentation requires a human-named explicit trigger as the justification
- **AND** it does not treat a procedure alone as sufficient reason to add a command

#### Scenario: Command does not own the procedure
- **WHEN** a framework-owned command and skill represent the same action
- **THEN** they share the same `sdd-*` name
- **AND** the skill remains the canonical procedure

### Requirement: Agents are specialist subagents
An SDD Framework agent SHALL be a Cursor custom subagent. The parent Cursor Agent SHALL remain the orchestrator. Framework agents SHALL be leaf specialists. They SHALL NOT be product-domain experts, SHALL NOT be hierarchical managers of other SDD agents, and SHALL NOT own the OpenSpec change lifecycle.

#### Scenario: Agent maps to a Cursor subagent
- **WHEN** a reader consults the Cursor component model
- **THEN** an SDD Framework agent is described as a Cursor subagent
- **AND** it is not described as `AGENTS.md` or as the default Cursor Agent

#### Scenario: Parent orchestrates specialists
- **WHEN** documentation describes multi-agent structure
- **THEN** the parent Cursor Agent is the orchestrator
- **AND** framework agents are leaf specialists that return results to the parent

#### Scenario: Product agents stay out of this repository
- **WHEN** a consuming project needs a product-domain agent
- **THEN** that agent remains a consuming-project Cursor extension
- **AND** it is not specified as an SDD Framework agent in this repository

### Requirement: OpenSpec lifecycle is not wrapped
The framework SHALL NOT introduce `sdd-*` commands or skills whose purpose is to replace, wrap, or redefine the OpenSpec change lifecycle or vendor `opsx-*` / `openspec-*` assets.

#### Scenario: No parallel lifecycle surface
- **WHEN** a contributor plans a framework-owned command or skill for explore, propose, apply, update, sync, or archive
- **THEN** documentation forbids creating that asset as an OpenSpec wrapper
- **AND** it directs the contributor to the vendor `opsx-*` / `openspec-*` surface

### Requirement: Cheapest fitting primitive
The documented model SHALL require choosing the cheapest Cursor primitive that fits the need: routing or persistent identity in `AGENTS.md`; operational constraints in rules; reusable procedures in skills; explicit human triggers in commands; isolated specialist work in agents.

#### Scenario: Single-purpose work is not an agent
- **WHEN** a planned framework asset is a single-purpose repeatable procedure that does not need isolated context
- **THEN** the documented model classifies it as a skill
- **AND** it does not classify it as an agent

### Requirement: Constitution without catalog implementation
This capability SHALL define the Cursor component model without requiring any framework-owned `sdd-*` rule, skill, command, or agent file to exist.

#### Scenario: Architecture change adds no Cursor catalog
- **WHEN** this change is applied
- **THEN** no `sdd-*` Cursor rules, skills, commands, or agents are required to exist
- **AND** the documented component model is sufficient for later changes to add them
