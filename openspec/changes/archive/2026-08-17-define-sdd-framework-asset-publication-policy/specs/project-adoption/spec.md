## MODIFIED Requirements

### Requirement: Published baseline inventory
The adoption contract SHALL name the assets that MAY be copied from this repository into a consuming project, the assets that MUST be obtained locally in the consuming project, and the assets that MUST NOT be transferred. An empty `sdd-*` Cursor subset in this repository SHALL remain a complete published baseline. Absence of those files SHALL NOT require inventing stubs in order to adopt and SHALL NOT be described as an incomplete implementation. Copy/pin, landing paths, never-transfer inventory, vendor OpenSpec exclusion, and installer deferral SHALL remain as already specified.

#### Scenario: Copyable framework-owned assets are listed
- **WHEN** a team reads the baseline inventory
- **THEN** documentation lists `.cursor/rules/sdd-*`, `.cursor/skills/sdd-*`, `.cursor/agents/sdd-*`, `.cursor/commands/sdd-*` when those assets exist, and `docs/sdd-framework/` as the methodology snapshot destination
- **AND** it does not require those `sdd-*` files to exist for the baseline to be complete

#### Scenario: Never-transferred assets are listed
- **WHEN** a team reads the baseline inventory
- **THEN** documentation forbids transferring this repository's `openspec/specs/`, OpenSpec change history, `AGENTS.md`, `README.md`, and git metadata into a consuming project as adopted baseline

#### Scenario: Zero Cursor assets remain a complete subset
- **WHEN** a consuming project copies the published subset and this repository contains no `sdd-*` Cursor files
- **THEN** documentation treats the methodology snapshot as a complete copy/pin baseline
- **AND** it does not treat missing `sdd-*` files as a defect or incomplete adoption
