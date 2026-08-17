## ADDED Requirements

### Requirement: Reserved prefixes are exclusive
Cursor asset names that use the `opsx-*`, `openspec-*`, or `sdd-*` prefixes SHALL be reserved. Consuming-project Cursor assets SHALL NOT use those prefixes. Project-specific Cursor extensions SHALL use names outside the reserved set.

#### Scenario: Project assets cannot claim reserved prefixes
- **WHEN** a consuming project adds a local Cursor rule, skill, command, or agent
- **THEN** documentation forbids naming that asset with an `opsx-*`, `openspec-*`, or `sdd-*` prefix
- **AND** it requires a project-specific name outside the reserved set

#### Scenario: Framework namespace stays framework-owned
- **WHEN** a consuming project has received framework `sdd-*` assets into its Cursor context
- **THEN** those names remain framework-owned
- **AND** the project is not permitted to overwrite them with project-specific behavior under the same names

### Requirement: Primitive-matched Cursor paths
When a later change creates a framework-owned Cursor asset, that asset SHALL live in the Cursor path that matches its primitive: rules under `.cursor/rules/`, skills under `.cursor/skills/`, commands under `.cursor/commands/`, and agents under `.cursor/agents/`.

#### Scenario: Planned asset has a matching path
- **WHEN** a contributor plans a framework-owned Cursor asset of a given primitive
- **THEN** documentation requires the corresponding `.cursor/` path for that primitive
- **AND** it does not allow placing that asset under a path belonging to a different primitive
