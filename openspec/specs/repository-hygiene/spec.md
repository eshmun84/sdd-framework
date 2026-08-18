# repository-hygiene Specification

## Purpose

Defines technology-neutral repository hygiene so operating-system, editor, temporary, environment, and generated noise is excluded without assuming an application stack.

## Requirements

### Requirement: Technology-neutral ignore file
The repository SHALL include a root `.gitignore` appropriate for a documentation and tooling framework. It SHALL ignore common operating-system files, editor and IDE user state, temporary files, local environment files, and generated noise. It SHALL NOT assume a specific application language, runtime, or framework.

#### Scenario: Common noise is ignored
- **WHEN** the root `.gitignore` is inspected
- **THEN** it ignores operating-system metadata such as `.DS_Store`
- **AND** it ignores editor or IDE user-specific state that is not part of the framework
- **AND** it ignores local environment files such as `.env`
- **AND** it ignores temporary and log files

#### Scenario: No application stack is assumed
- **WHEN** the root `.gitignore` is inspected
- **THEN** it does not encode a single application language or runtime as the repository's stack
- **AND** it remains valid for a documentation and Cursor/OpenSpec tooling repository

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
