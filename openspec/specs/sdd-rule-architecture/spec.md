# sdd-rule-architecture Specification

## Purpose

Defines the SDD Framework rule operating model — when a rule is justified, how it differs from other Cursor primitives, how future rule files are activated and structured, and how rule assets are evolved — without creating rules or restating the Cursor component constitution.

## Requirements

### Requirement: Rule identity is a persistent operational constraint
The documented rule operating model SHALL describe an SDD rule as a persistent operational constraint that binds the parent Cursor Agent when relevant work is in play, without requiring invocation. It SHALL distinguish that operating unit from `AGENTS.md` (routing contract), skills (reusable procedures), commands (optional human triggers), agents (isolated specialists), OpenSpec specifications (requirement contracts), documentation (explanation), and prompts (session instructions), without redefining those primitives. An SDD rule SHALL NOT be described as documentation, a specification, a procedure, a persona, a prompt, an OpenSpec wrapper, or a consuming-project convention.

#### Scenario: Operating model distinguishes rules from other primitives
- **WHEN** a reader consults the rule-system architecture documentation
- **THEN** an SDD rule is described as a persistent operational constraint that binds without invocation
- **AND** it is distinguished from `AGENTS.md`, skills, commands, agents, specifications, documentation, and prompts without restating the Cursor component constitution in full

#### Scenario: Rule is not a document, spec, playbook, or persona
- **WHEN** documentation describes what an SDD rule is not
- **THEN** it states that an SDD rule is not documentation, a specification, a procedure, a persona, a prompt, an OpenSpec wrapper, or a project-specific convention

### Requirement: Rule creation requires a copy-valid operational constraint
A framework-owned rule SHALL be justified only when the need is a persistent operational constraint, the constraint applies repeatedly, the wording is operational, the constraint remains valid after copy/pin into a consuming project, and no cheaper primitive fits. Identity or navigation SHALL remain in `AGENTS.md`. A requirement SHALL remain an OpenSpec specification. Explanation SHALL remain in `docs/`. A reusable procedure SHALL be classified as a skill. Isolated judgment SHALL be classified as an agent. Session-only instruction SHALL remain a prompt. OpenSpec change lifecycle work SHALL remain on the vendor `opsx-*` / `openspec-*` surface. Constraints that are true only in this repository SHALL NOT be named as `sdd-*` rules.

#### Scenario: Copy-valid operational constraint meets the bar
- **WHEN** a contributor plans a framework-owned asset that is a persistent operational must-or-must-not, applies repeatedly, stays true after adoption, and is not identity, a requirement, a procedure, or isolated judgment
- **THEN** the documented model classifies that asset as a rule
- **AND** it does not classify it as a skill, an agent, or documentation

#### Scenario: Procedure is rejected as a rule
- **WHEN** a contributor plans a framework-owned asset whose value is a repeatable method with steps, inputs, and outputs
- **THEN** the documented model classifies that asset as a skill
- **AND** it does not classify it as a rule

#### Scenario: Isolated judgment is rejected as a rule
- **WHEN** a contributor plans a framework-owned asset whose value is a specialist stance or isolation from the implementation conversation
- **THEN** the documented model classifies that asset as an agent
- **AND** it does not classify it as a rule

#### Scenario: Identity, requirements, and documentation are rejected as rules
- **WHEN** a contributor plans a framework-owned asset whose value is repository identity, navigation, a framework requirement, or methodology prose
- **THEN** the documented model directs that content to `AGENTS.md`, an OpenSpec specification, or `docs/`
- **AND** it does not classify that content as a rule

#### Scenario: Dogfood-only constraint is rejected as an sdd rule
- **WHEN** a contributor plans a framework-owned `sdd-*` rule that is true only inside this repository
- **THEN** documentation forbids naming that constraint as an `sdd-*` rule
- **AND** it directs that constraint to this repository's `AGENTS.md` or to a project-named rule outside reserved prefixes

#### Scenario: OpenSpec lifecycle is rejected as a rule
- **WHEN** a contributor plans a framework-owned rule whose purpose is explore, propose, apply, update, sync, or archive
- **THEN** documentation forbids creating that rule
- **AND** it directs the contributor to the vendor `opsx-*` / `openspec-*` surface

### Requirement: Rules remain distinct from other primitives
The documented model SHALL treat a rule as a persistent constraint, `AGENTS.md` as the routing contract, a skill as an invoked procedure, a command as an optional thin trigger, an agent as an isolated specialist, an OpenSpec specification as the requirement contract, documentation as explanation, and a prompt as session-scoped instruction. A rule SHALL NOT introduce a requirement that is not already owned by an OpenSpec specification. A rule SHALL NOT accumulate into a procedure or a specialist persona.

#### Scenario: Rule versus AGENTS.md is documented
- **WHEN** documentation compares rules and `AGENTS.md`
- **THEN** `AGENTS.md` is described as identity and navigation
- **AND** a rule is described as an operational constraint that is not the always-on router

#### Scenario: Rule versus skill is documented
- **WHEN** documentation compares rules and skills
- **THEN** a rule is described as a persistent constraint that binds without invocation
- **AND** a skill is described as an invoked procedure

#### Scenario: Rule versus specification is documented
- **WHEN** documentation compares rules and OpenSpec specifications
- **THEN** a specification is described as the requirement contract
- **AND** a rule is described as a runtime reminder that points at that contract rather than replacing it

#### Scenario: Hidden specification is rejected
- **WHEN** a contributor plans a framework-owned rule that would add framework behavior not already specified
- **THEN** the documented model forbids that rule
- **AND** it requires the behavior to be specified in OpenSpec before any later rule may remind the agent of it

### Requirement: Activation is glob-scoped by default
A framework-owned rule SHALL default to glob-scoped activation, and those globs SHALL match paths whose meaning is identical after copy/pin into a consuming project. Always-apply activation SHALL be exceptional and SHALL be limited to short adoption or namespace invariants that must bind even during product work and cannot remain one short line in `AGENTS.md`. Description-only activation SHALL be forbidden for framework-owned rules. Manual `@mention` SHALL NOT be the framework distribution model for rules. A later change that implements a rule SHALL record the activation mode and why it was chosen. Framework-owned rules SHALL NOT glob to `openspec/**` or `docs/**`.

#### Scenario: Default activation is glob-scoped and copy-safe
- **WHEN** a later change creates a framework-owned rule and does not justify always-apply
- **THEN** documentation requires that rule to use glob-scoped activation
- **AND** it requires those globs to remain correct after the rule is copied into a consuming project

#### Scenario: Content-tree globs are forbidden
- **WHEN** a contributor plans a framework-owned rule globbed to `openspec/**` or `docs/**`
- **THEN** documentation forbids that glob
- **AND** it states that those paths do not mean the same thing in this repository and in a consuming project

#### Scenario: Always-apply remains exceptional
- **WHEN** documentation describes how framework rules are applied
- **THEN** it states that always-apply rules are exceptional
- **AND** it limits them to adoption or namespace invariants that must bind during product work
- **AND** it states that `AGENTS.md` remains the default always-on router

#### Scenario: Description-only activation is forbidden
- **WHEN** a contributor plans a framework-owned rule that activates only from description matching
- **THEN** documentation forbids that rule
- **AND** it directs optional discovery of a procedure to the skill operating model

#### Scenario: Manual mention is not distribution
- **WHEN** a contributor plans to distribute a framework-owned rule by requiring humans to mention it
- **THEN** documentation forbids that as the framework distribution model
- **AND** it directs named human triggers to skills or optional commands

### Requirement: Future rule files match the project rule contract
When a later change creates a framework-owned rule, that asset SHALL live at `.cursor/rules/sdd-<concern>.mdc` in the project Cursor tree. The name SHALL identify one operational concern, SHALL NOT be a procedure verb, SHALL NOT be a specialist role, and SHALL NOT use an `sdd-rule-*` prefix. The file SHALL NOT be distributed as a user-level rule. The body SHALL encode the constraint and pointers to authoritative methodology documentation, SHALL remain valid after that documentation lands at the adopted snapshot path, and SHALL NOT republish methodology pages. Rules SHALL accumulate independently and SHALL NOT invoke other rules as procedures.

#### Scenario: Planned rule has a project path and sdd concern name
- **WHEN** a contributor plans a framework-owned rule
- **THEN** documentation requires the path `.cursor/rules/sdd-<concern>.mdc`
- **AND** it forbids placing that rule in a user-level rule directory as the framework home

#### Scenario: Filename is a concern not a procedure or role
- **WHEN** a contributor chooses a framework-owned rule name
- **THEN** documentation requires `sdd-<concern>`
- **AND** it forbids procedure-verb names, specialist-role names, and `sdd-rule-*` names

#### Scenario: Rule body is constraint plus pointer
- **WHEN** a contributor drafts a framework-owned rule file in a later change
- **THEN** documentation requires the body to state an operational constraint and point at authoritative methodology
- **AND** it forbids copying a methodology page from `docs/` into the rule file

### Requirement: Rule quality is concise, scoped, and non-duplicative
A valid framework-owned rule SHALL be concise, operational, limited to one concern, and non-duplicative of `AGENTS.md`, other rules, specifications, or `docs/`. It SHALL NOT become a hidden specification, a skill procedure, or an agent persona. Quality SHALL be described behaviorally; this architecture SHALL NOT impose a numeric line-count limit as a requirement.

#### Scenario: Quality bar is documented
- **WHEN** a reader consults the rule-system architecture documentation
- **THEN** it requires rules to be concise, operational, one concern per file, and referential rather than duplicative
- **AND** it forbids rules that reprint documentation, encode procedures, or impersonate specialists

#### Scenario: Line count is not a specification
- **WHEN** a contributor looks for a required maximum line count for a framework rule
- **THEN** documentation treats concision as a quality expectation
- **AND** it does not make a numeric line limit a requirement

### Requirement: Rule assets follow the OpenSpec lifecycle
Creating, changing, or deprecating a framework-owned rule SHALL require an OpenSpec change in this repository. A later change that implements a rule SHALL record why the asset is a rule rather than `AGENTS.md`, a skill, an agent, a specification, a documentation page, or a vendor OpenSpec asset, and SHALL record activation mode and copy-validity. Silent addition, in-place product overwrite, or undocumented deletion of a framework rule SHALL NOT be permitted. After archive, adopted copies SHALL participate in the existing versioned baseline copy/pin model: they remain framework-owned, are replaced on update, and MUST NOT be customized in place.

#### Scenario: New rule needs a change
- **WHEN** a contributor wants to add a framework-owned rule
- **THEN** documentation requires an OpenSpec change that proposes, designs, and tasks that rule
- **AND** it does not permit creating the rule file outside that lifecycle

#### Scenario: Deprecation needs a change
- **WHEN** a framework-owned rule is withdrawn or replaced
- **THEN** documentation requires an OpenSpec change
- **AND** it does not permit silent deletion as the deprecation path

#### Scenario: Adopted copies are replaced not forked
- **WHEN** a consuming project has received a framework-owned rule through the baseline
- **THEN** documentation requires that file to remain framework-owned
- **AND** it forbids customizing that `sdd-*` rule in place
- **AND** it describes later updates as reviewed replacement of framework-owned copied assets

### Requirement: Project rules coexist outside reserved prefixes
Consuming-project rules SHALL use names outside `opsx-*`, `openspec-*`, and `sdd-*`. They SHALL NOT overwrite framework `sdd-*` rules in place. Domain, product, or stack rules SHALL remain consuming-project Cursor extensions. Promotion into the framework SHALL require this repository's OpenSpec lifecycle. This architecture SHALL NOT define a catalog of consuming-project rules.

#### Scenario: Project cannot claim sdd names
- **WHEN** a consuming project adds a local rule
- **THEN** documentation forbids naming that rule with an `opsx-*`, `openspec-*`, or `sdd-*` prefix
- **AND** it forbids overwriting a framework `sdd-*` rule with project-specific behavior under the same name

#### Scenario: Product rules stay in the project
- **WHEN** a consuming project needs a product-domain or stack-specific rule
- **THEN** that rule remains a consuming-project Cursor extension
- **AND** it is not specified as an SDD Framework rule in this repository

### Requirement: Rules bind the parent session
The documented model SHALL bind framework-owned rules to the parent Cursor Agent session. It SHALL NOT treat glob or always-apply inheritance into specialist subagents as a framework contract. Specialist constraints SHALL be encoded in the agent file by pointing at authoritative documentation rather than by duplicating rule bodies.

#### Scenario: Parent is the bound agent
- **WHEN** documentation describes which agent a framework rule binds
- **THEN** it states that framework rules bind the parent Cursor Agent
- **AND** it does not require specialist subagents to inherit those rules

#### Scenario: Specialists do not reprint rules
- **WHEN** a later change creates a framework-owned agent that must respect a methodology constraint
- **THEN** documentation requires that agent file to point at authoritative `docs/`
- **AND** it forbids copying a framework rule body into the agent file

### Requirement: Operating model without catalog implementation
This capability SHALL define the rule operating model without requiring any framework-owned `sdd-*` rule file to exist.

#### Scenario: Architecture change adds no rules
- **WHEN** this change is applied
- **THEN** no `.cursor/rules/` directory or `sdd-*` rule file is required to exist
- **AND** the documented operating model is sufficient for later changes to add rules
