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
The ignore file SHALL NOT exclude the framework's methodology assets that belong in version control, including `docs/`, `AGENTS.md`, `README.md`, `openspec/`, and the shared Cursor commands, skills, and rules that constitute the vendor or framework baseline.

#### Scenario: OpenSpec and Cursor baseline are not ignored
- **WHEN** a contributor stages framework files
- **THEN** `openspec/` configuration, specifications, and changes can be tracked
- **AND** `.cursor/commands/` and `.cursor/skills/` baseline assets can be tracked
- **AND** `docs/`, `README.md`, and `AGENTS.md` can be tracked
