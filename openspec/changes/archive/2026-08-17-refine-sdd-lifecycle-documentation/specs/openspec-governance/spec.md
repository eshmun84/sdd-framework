## ADDED Requirements

### Requirement: Lifecycle documentation defers command semantics
Lifecycle documentation SHALL describe OpenSpec phase intent (analysis, clarification, specification, implementation, synchronization, archival) and SHALL NOT restate command-level allow or forbid rules. Command behavior SHALL remain defined by vendor OpenSpec assets.

#### Scenario: Explore purpose describes intent
- **WHEN** a reader opens the lifecycle documentation purpose table
- **THEN** the Explore row describes clarification of ideas, problems, requirements, and constraints
- **AND** it states that command behavior is defined by OpenSpec
- **AND** it does not contain an absolute prohibition such as "Do not implement"

#### Scenario: Explore command surface describes intent
- **WHEN** a reader opens the installed Cursor surface table
- **THEN** the `/opsx-explore` use description is limited to discovery and clarification
- **AND** it does not contain an absolute prohibition such as "no implementation"

#### Scenario: Command permissions stay with OpenSpec
- **WHEN** a reader needs the allow or forbid rules for an OpenSpec command
- **THEN** the lifecycle page points to vendor-managed OpenSpec Cursor assets as the authority
- **AND** the page does not function as a replacement command specification

### Requirement: Lifecycle order is orientation not sequence
When lifecycle documentation presents `explore → propose → apply → sync → archive`, it SHALL identify that order as a typical orientation and SHALL NOT present it as a mandatory OpenSpec execution sequence.

#### Scenario: Typical order is qualified
- **WHEN** a reader sees the lifecycle flow diagram or equivalent list
- **THEN** the documentation identifies it as a typical orientation
- **AND** it does not require that OpenSpec commands be invoked only in that sequence
