## MODIFIED Requirements

### Requirement: Future agent files match the project subagent contract
When a later change creates a framework-owned agent, that file SHALL be authored at `assets/cursor/agents/sdd-<role>.md` in this repository's source tree. After copy/pin, the installed file SHALL live at `.cursor/agents/sdd-<role>.md` in the consuming project's Cursor tree. It SHALL NOT be distributed as a user-level agent. It SHALL be configured so it cannot edit files or run state-changing shell commands unless a later OpenSpec change justifies write access. It SHALL use the parent agent's model unless a later OpenSpec change specifies otherwise. The file body SHALL encode specialist stance and forbidden ownership and SHALL point at authoritative `docs/` rather than republishing methodology.

#### Scenario: Planned agent has a source path and sdd name
- **WHEN** a contributor plans a framework-owned agent
- **THEN** documentation requires the source path `assets/cursor/agents/sdd-<role>.md`
- **AND** it requires the installed path `.cursor/agents/sdd-<role>.md` after copy/pin
- **AND** it forbids placing that agent in a user-level agent directory or in a non-`.cursor/` compatibility directory as the installed home

#### Scenario: Review agents do not write by default
- **WHEN** documentation describes the default write policy for framework agents
- **THEN** it requires that framework agents cannot edit files or run state-changing shell commands unless a later change justifies writes

#### Scenario: Agent body is stance not playbook
- **WHEN** a contributor drafts a framework-owned agent file in a later change
- **THEN** documentation requires the body to state specialist stance and forbidden ownership
- **AND** it forbids copying a methodology page from `docs/` into the agent file

### Requirement: Operating model without catalog implementation
This capability SHALL define the agent operating model without requiring any framework-owned `sdd-*` agent file to exist.

#### Scenario: Architecture change adds no agents
- **WHEN** this operating model is applied without a per-asset agent change
- **THEN** no `assets/cursor/agents/` directory or `sdd-*` agent file is required to exist
- **AND** the documented operating model is sufficient for later changes to add agents
- **AND** empty placeholder agent directories are not required
