## ADDED Requirements

### Requirement: Source tree is distinct from vendor Cursor installation
Framework-owned `sdd-*` source assets SHALL live under `assets/cursor/`. Vendor OpenSpec Cursor assets SHALL remain under this repository's `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*`. This repository's `.cursor/` tree SHALL NOT be the published source of `sdd-*` files.

#### Scenario: Vendor files stay in the load tree
- **WHEN** the repository's `.cursor/commands/` and `.cursor/skills/` directories are inspected
- **THEN** OpenSpec-generated `opsx-*` commands and `openspec-*` skills remain present under their generated names
- **AND** they are documented as vendor-managed, not as framework source assets

#### Scenario: Published sdd files are not sourced from this .cursor tree
- **WHEN** a contributor locates the published `sdd-*` source
- **THEN** documentation directs them to `assets/cursor/`
- **AND** it does not treat this repository's `.cursor/**/sdd-*` as the source inventory

## MODIFIED Requirements

### Requirement: Primitive-matched Cursor paths
When a later change creates a framework-owned Cursor asset, that asset SHALL be authored in the source tree under `assets/cursor/` in the path that matches its primitive: rules under `assets/cursor/rules/`, skills under `assets/cursor/skills/`, commands under `assets/cursor/commands/`, and agents under `assets/cursor/agents/`. After copy/pin, the installed asset SHALL live in the consuming project's matching `.cursor/` path: rules under `.cursor/rules/`, skills under `.cursor/skills/`, commands under `.cursor/commands/`, and agents under `.cursor/agents/`. A framework-owned asset SHALL NOT be placed under a path belonging to a different primitive in either tree.

#### Scenario: Planned asset has a matching source path
- **WHEN** a contributor plans a framework-owned Cursor asset of a given primitive
- **THEN** documentation requires the corresponding `assets/cursor/` path for that primitive
- **AND** it does not allow placing that source asset under a path belonging to a different primitive

#### Scenario: Installed asset has a matching load path
- **WHEN** a consuming project has received a framework-owned Cursor asset through copy/pin
- **THEN** documentation requires the corresponding project-root `.cursor/` path for that primitive
- **AND** it does not allow placing that installed asset under a path belonging to a different primitive
