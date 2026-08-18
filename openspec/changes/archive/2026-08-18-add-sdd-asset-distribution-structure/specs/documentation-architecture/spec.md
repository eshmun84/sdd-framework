## ADDED Requirements

### Requirement: Source versus installed Cursor asset paths are documented
The documentation tree SHALL distinguish the framework source tree `assets/cursor/` from the Cursor load tree `.cursor/`. Adoption documentation SHALL name copy FROM and copy TO. Architecture overview, Cursor integration, asset lifecycle, and type operating models SHALL use that distinction and SHALL NOT describe this repository's `.cursor/` as the published `sdd-*` home. README navigation SHALL identify `assets/cursor/` as the published Cursor-asset source when describing repository layout. The documentation tree SHALL NOT add a second adoption page, a planned-name catalog, or empty placeholder directories in order to document the distinction.

#### Scenario: Adoption names FROM and TO
- **WHEN** a reader opens the adoption architecture page
- **THEN** the page names `assets/cursor/` as the copy FROM source
- **AND** it names the consuming project's project-root `.cursor/` as the copy TO installed path

#### Scenario: Entrypoints do not treat this repo as an installed baseline
- **WHEN** a human or agent reads `README.md` or architecture overview
- **THEN** those files describe this repository as the source of published Cursor assets
- **AND** they do not present this repository's `.cursor/` tree as the published `sdd-*` inventory

#### Scenario: No second adoption page or catalog
- **WHEN** this distribution-layout documentation is applied
- **THEN** `docs/architecture/adoption.md` remains the adoption contract home
- **AND** no catalog page or empty `assets/cursor/` placeholder directories are added as documentation
