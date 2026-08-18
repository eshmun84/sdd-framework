## MODIFIED Requirements

### Requirement: Framework assets remain trackable
The ignore file SHALL NOT exclude the framework's methodology assets that belong in version control, including `docs/`, `AGENTS.md`, `README.md`, `openspec/`, the published Cursor source tree under `assets/cursor/` when those files exist, and the vendor OpenSpec Cursor commands and skills under this repository's `.cursor/`. Published `sdd-*` files SHALL NOT be required to exist under this repository's `.cursor/` in order to be trackable.

#### Scenario: OpenSpec and Cursor baseline are not ignored
- **WHEN** a contributor stages framework files
- **THEN** `openspec/` configuration, specifications, and changes can be tracked
- **AND** `.cursor/commands/` and `.cursor/skills/` vendor OpenSpec assets can be tracked
- **AND** `assets/cursor/` source assets can be tracked when those files exist
- **AND** `docs/`, `README.md`, and `AGENTS.md` can be tracked

### Requirement: Cursor agent baseline remains trackable
The ignore file SHALL NOT exclude shared Cursor agents that constitute the framework baseline when those files exist under `assets/cursor/agents/`.

#### Scenario: Agent files can be staged
- **WHEN** a contributor stages framework files and agent files exist under `assets/cursor/agents/`
- **THEN** those agent files can be tracked
- **AND** the ignore file does not exclude `assets/cursor/agents/` as a class of framework baseline
