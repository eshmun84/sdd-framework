## Why

Lifecycle documentation currently compresses OpenSpec Explore into absolute rules (“Do not implement.” / “no implementation”). That wording can be read as SDD replacing OpenSpec command authority, including forbidding Explore from producing OpenSpec artifacts. The ownership boundary must be restored before the foundation is treated as durable methodology.

## What Changes

- Reword the Explore purpose cell in `docs/lifecycle/openspec-workflow.md` to describe analysis and clarification intent, and to state that command behavior is defined by OpenSpec.
- Reword the `/opsx-explore` Use cell from “Discovery; no implementation” to intent-focused “Discovery and clarification.”
- Clarify that `explore → propose → apply → sync → archive` is a typical orientation, not a mandatory OpenSpec execution sequence.
- Add a durable requirement that lifecycle documentation describes phase purpose and defers command-level permissions to vendor OpenSpec assets.

## Non-goals

- Do not modify vendor OpenSpec commands or skills (`opsx-*`, `openspec-*`).
- Do not redefine OpenSpec lifecycle or command semantics.
- Do not introduce new lifecycle phases or change the SDD workflow.
- Do not edit unrelated documentation (`README.md`, `AGENTS.md`, governance, principles, adoption, architecture overview).
- Do not change SDD governance principles, including the working-agreement that framework behavior is not implemented without OpenSpec change artifacts.
- Do not expand into agents, skills, installers, or automation.

## Capabilities

### New Capabilities

- None.

### Modified Capabilities

- `openspec-governance`: Lifecycle documentation SHALL describe OpenSpec phase intent and SHALL NOT restate command-level allow/forbid rules. Command behavior remains defined by vendor OpenSpec assets. *(Capability introduced by `establish-sdd-framework-foundation`; main spec not yet archived.)*

## Impact

- Documentation only: `docs/lifecycle/openspec-workflow.md`.
- Spec delta under this change for `openspec-governance`.
- No Cursor vendor assets, no application code, no schema change, no consuming-project impact.
