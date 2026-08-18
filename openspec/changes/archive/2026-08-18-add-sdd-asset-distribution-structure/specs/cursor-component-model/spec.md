## ADDED Requirements

### Requirement: Source location is distinct from Cursor load location
The documented Cursor component model SHALL distinguish the framework source location of `sdd-*` assets from the Cursor load location. Source assets SHALL be described as living under `assets/cursor/` in this repository. Cursor SHALL be described as loading installed assets from project-root `.cursor/` after copy/pin. The constitution SHALL NOT describe this repository's `.cursor/` tree as the published home of framework-owned `sdd-*` assets. Primitive meaning, cheapest-fitting primitive, and the prohibition on wrapping OpenSpec SHALL remain unchanged.

#### Scenario: Constitution names both locations
- **WHEN** a reader consults Cursor integration documentation for where framework-owned assets live
- **THEN** documentation names `assets/cursor/` as the source location
- **AND** it names project-root `.cursor/` as the installed load location

#### Scenario: Primitive meaning is not reopened
- **WHEN** this distribution-layout clarification is applied
- **THEN** rules, skills, commands, and agents keep their existing constitution meaning
- **AND** documentation does not treat the path split as a new primitive or a fifth architecture layer
