## ADDED Requirements

### Requirement: An approved change bounds allowed implementation work
The documented workflow SHALL describe an approved OpenSpec change in the current repository's workspace as the bound on allowed implementation work. That bound SHALL be the change's proposal, including its scope and non-goals, its specifications, its design when present, and its tasks. The workflow SHALL NOT define that bound as a file allowlist, path inventory, CODEOWNERS map, or project-management backlog. The workflow SHALL keep OpenSpec as the requirement contract for that bound.

#### Scenario: Contract artifacts are the bound
- **WHEN** a reader consults what implementation may do for an approved change
- **THEN** documentation describes allowed work as that change's proposal, specifications, design when present, tasks, and non-goals
- **AND** it refers to the current repository's OpenSpec workspace
- **AND** it states that OpenSpec remains the requirement contract

#### Scenario: Filesystem and project-management fences are absent
- **WHEN** a reader looks for a file allowlist, path inventory, or backlog as the definition of Apply scope
- **THEN** documentation does not specify those practices
- **AND** it keeps the concern limited to the approved change's contract artifacts

### Requirement: Apply does not add requirements or tasks
During Apply, the documented workflow SHALL forbid adding requirements, design decisions, or task items that are not already in the approved change. Checking off existing tasks SHALL remain Apply. Adding new task items SHALL be classified as update or a new change, not Apply. The workflow SHALL forbid applying those additions from the implementation prompt alone.

#### Scenario: New requirements and tasks are not Apply
- **WHEN** implementation would add a requirement, design decision, or new task item that is not in the approved change
- **THEN** the documented workflow classifies that addition as incorrect for Apply
- **AND** it requires update or a new change instead of applying the addition from the implementation prompt

#### Scenario: Completing existing tasks remains Apply
- **WHEN** Apply marks an existing authorized task as complete
- **THEN** the documented workflow treats that completion as Apply
- **AND** it does not classify checking off an existing task as expanding the contract

### Requirement: Apply does not perform unsolicited improvements outside the contract
The documented workflow SHALL forbid implementation work that the approved change does not oblige, including adjacent improvements, cleanup, or refactors that are not required to fulfill the contract. Mechanical edits that the approved contract obliges SHALL remain allowed. When extra work should remain true after the conversation, the workflow SHALL require update or a new change rather than applying that work from Apply. The workflow SHALL prefer a new change when the in-flight change would expand past its non-goals.

#### Scenario: Unsolicited adjacent work is forbidden
- **WHEN** Apply would include an improvement, cleanup, or refactor that the approved contract does not oblige
- **THEN** the documented workflow classifies that work as incorrect for Apply
- **AND** it forbids applying that work from the implementation prompt

#### Scenario: Obligated mechanical edits remain allowed
- **WHEN** fulfilling the approved contract requires a mechanical edit
- **THEN** the documented workflow treats that edit as in-scope Apply work
- **AND** it does not classify obligated mechanical edits as unsolicited improvements

#### Scenario: Surviving extra work returns to the lifecycle
- **WHEN** extra work discovered during Apply should remain true and is not in the approved change
- **THEN** the documented workflow requires update or a new change
- **AND** it prefers a new change when the in-flight change would expand past its non-goals
