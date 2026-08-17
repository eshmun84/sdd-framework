## ADDED Requirements

### Requirement: Cursor agent baseline remains trackable
The ignore file SHALL NOT exclude shared Cursor agents that constitute the vendor or framework baseline when those files exist.

#### Scenario: Agent files can be staged
- **WHEN** a contributor stages framework files and agent files exist under `.cursor/agents/`
- **THEN** those agent files can be tracked
- **AND** the ignore file does not exclude `.cursor/agents/` as a class of framework baseline
