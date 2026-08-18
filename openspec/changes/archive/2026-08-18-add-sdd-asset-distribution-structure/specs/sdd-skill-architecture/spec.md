## MODIFIED Requirements

### Requirement: Future skill files match the project skill contract
When a later change creates a framework-owned skill, that asset SHALL be authored at `assets/cursor/skills/sdd-<procedure>/SKILL.md` in this repository's source tree. After copy/pin, the installed file SHALL live at `.cursor/skills/sdd-<procedure>/SKILL.md` in the consuming project's Cursor tree. It SHALL NOT be distributed as a user-level skill. Optional supporting reference files SHALL remain one level deep from `SKILL.md`. `SKILL.md` SHALL encode purpose, trigger conditions, instructions, skill-local constraints, references to authoritative `docs/`, and named outputs, and SHALL NOT republish methodology pages. This architecture SHALL NOT require executable scripts inside skills.

#### Scenario: Planned skill has a source path and sdd procedure name
- **WHEN** a contributor plans a framework-owned skill
- **THEN** documentation requires the source path `assets/cursor/skills/sdd-<procedure>/SKILL.md`
- **AND** it requires the installed path `.cursor/skills/sdd-<procedure>/SKILL.md` after copy/pin
- **AND** it forbids placing that skill in a user-level skill directory as the framework home

#### Scenario: SKILL.md carries the procedure contract
- **WHEN** a contributor drafts a framework-owned skill file in a later change
- **THEN** documentation requires `SKILL.md` to include purpose, trigger conditions, instructions, constraints, references, and outputs
- **AND** it forbids copying a methodology page from `docs/` into the skill file

#### Scenario: Scripts are not part of this architecture
- **WHEN** a contributor looks for a framework requirement to ship executable scripts inside a skill
- **THEN** documentation states that scripts are out of scope for this operating model
- **AND** it does not require a `scripts/` directory for a valid skill

### Requirement: Operating model without catalog implementation
This capability SHALL define the skill operating model without requiring any framework-owned `sdd-*` skill file to exist.

#### Scenario: Architecture change adds no skills
- **WHEN** this operating model is applied without a per-asset skill change
- **THEN** no `assets/cursor/skills/sdd-*` directory or skill file is required to exist
- **AND** the documented operating model is sufficient for later changes to add skills
- **AND** empty placeholder skill directories are not required
