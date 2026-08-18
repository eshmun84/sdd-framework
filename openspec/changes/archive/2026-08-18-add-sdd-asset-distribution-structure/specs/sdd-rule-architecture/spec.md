## MODIFIED Requirements

### Requirement: Future rule files match the project rule contract
When a later change creates a framework-owned rule, that asset SHALL be authored at `assets/cursor/rules/sdd-<concern>.mdc` in this repository's source tree. After copy/pin, the installed file SHALL live at `.cursor/rules/sdd-<concern>.mdc` in the consuming project's Cursor tree. The name SHALL identify one operational concern, SHALL NOT be a procedure verb, SHALL NOT be a specialist role, and SHALL NOT use an `sdd-rule-*` prefix. The file SHALL NOT be distributed as a user-level rule. The body SHALL encode the constraint and pointers to authoritative methodology documentation, SHALL remain valid after that documentation lands at the adopted snapshot path, and SHALL NOT republish methodology pages. Rules SHALL accumulate independently and SHALL NOT invoke other rules as procedures.

#### Scenario: Planned rule has a source path and sdd concern name
- **WHEN** a contributor plans a framework-owned rule
- **THEN** documentation requires the source path `assets/cursor/rules/sdd-<concern>.mdc`
- **AND** it requires the installed path `.cursor/rules/sdd-<concern>.mdc` after copy/pin
- **AND** it forbids placing that rule in a user-level rule directory as the framework home

#### Scenario: Filename is a concern not a procedure or role
- **WHEN** a contributor chooses a framework-owned rule name
- **THEN** documentation requires `sdd-<concern>`
- **AND** it forbids procedure-verb names, specialist-role names, and `sdd-rule-*` names

#### Scenario: Rule body is constraint plus pointer
- **WHEN** a contributor drafts a framework-owned rule file in a later change
- **THEN** documentation requires the body to state an operational constraint and point at authoritative methodology
- **AND** it forbids copying a methodology page from `docs/` into the rule file

### Requirement: Operating model without catalog implementation
This capability SHALL define the rule operating model without requiring any framework-owned `sdd-*` rule file to exist beyond files already required by other capabilities.

#### Scenario: Architecture change adds no rules
- **WHEN** this operating model is applied without a per-asset rule change
- **THEN** no additional `sdd-*` rule file is required to exist
- **AND** the documented operating model is sufficient for later changes to add rules
- **AND** empty `assets/cursor/rules/` placeholder directories are not required
