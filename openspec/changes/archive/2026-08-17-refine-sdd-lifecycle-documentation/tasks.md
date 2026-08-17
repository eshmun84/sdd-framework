## 1. Lifecycle documentation wording

- [x] 1.1 In `docs/lifecycle/openspec-workflow.md`, replace the Explore purpose cell so it describes clarifying ideas, problems, requirements, and constraints, and states that command behavior is defined by OpenSpec
- [x] 1.2 Replace the `/opsx-explore` Use cell with "Discovery and clarification."
- [x] 1.3 Qualify `explore → propose → apply → sync → archive` as a typical orientation, not a mandatory OpenSpec execution sequence

## 2. Validation

- [x] 2.1 Confirm the lifecycle page no longer contains absolute Explore prohibitions such as "Do not implement" or "no implementation"
- [x] 2.2 Confirm vendor `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged
- [x] 2.3 Confirm `README.md`, `AGENTS.md`, governance, principles, adoption, and architecture overview were not edited
- [x] 2.4 Run `openspec validate refine-sdd-lifecycle-documentation --type change --strict` and resolve any validation issues in this change's artifacts
