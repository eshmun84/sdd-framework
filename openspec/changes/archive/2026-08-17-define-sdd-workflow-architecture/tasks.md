## 1. Workflow-system architecture page

- [x] 1.1 Create `docs/architecture/workflow-system.md` covering workflow identity (collaboration operating model, not a fifth layer, not an engine, not an OpenSpec wrapper) and distinction from four-layer architecture, Cursor primitives, human-AI practice, vendor OpenSpec commands, and adoption — by pointer, not copy
- [x] 1.2 Document canonical stages (intake, explore, propose, apply, review, archive), loop-backs (update, sync), maintenance as a new change, conceptual-vs-sequence wording, stage boundaries, and durable outputs
- [x] 1.3 Document participant responsibilities (human gates, optional planning assistant, Cursor execution, OpenSpec contract, implementation as Cursor apply), durable versus temporary information, human approval gates, and universe selection
- [x] 1.4 Document review as an SDD stage without a vendor command, incomplete/rejected/evolving-work handling, same workflow in independent OpenSpec universes, and that this page creates no `sdd-*` assets, prompt libraries, or automation

## 2. Navigation and entrypoints

- [x] 2.1 Add a `docs/README.md` index link to the workflow-system architecture page
- [x] 2.2 Update `docs/architecture/overview.md` with a pointer to the workflow-system page while keeping it the four-layer summary and adding no fifth layer
- [x] 2.3 Update `docs/lifecycle/openspec-workflow.md` so it points to the workflow-system page for the collaboration model and remains the vendor OpenSpec surface
- [x] 2.4 Update `docs/practices/human-ai-interaction.md` so it points to the workflow-system page for collaboration stages and remains the prompting practice
- [x] 2.5 Update `docs/governance/working-agreements.md` so it points to the workflow-system page for the shared collaboration model and keeps this-repository specify/apply/archive constraints
- [x] 2.6 Update `AGENTS.md` to link the workflow-system page, keep it a short router, and require OpenSpec artifacts rather than a mandatory `explore → propose → apply → sync → archive` command sequence
- [x] 2.7 Update root `README.md` so it points at the workflow operating model without copying it, and status reflects that the model exists while a skill/agent/rule catalog still does not

## 3. Boundary verification

- [x] 3.1 Verify this change did not add `.cursor/` files, `sdd-*` assets, a `prompts/` directory, templates, scripts, an installer, MCP/plugin/hook config, a custom OpenSpec schema, application code, or a workflow engine
- [x] 3.2 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged
- [x] 3.3 Run `openspec validate --change "define-sdd-workflow-architecture"` and resolve any validation issues in the change artifacts
