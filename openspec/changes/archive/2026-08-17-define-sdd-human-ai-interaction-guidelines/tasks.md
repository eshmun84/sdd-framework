## 1. Human-AI interaction practice page

- [x] 1.1 Create `docs/practices/human-ai-interaction.md` covering prompt identity (session-scoped instruction vs requirement, docs, skill, rule, agent, and `AGENTS.md`) and the typical intent flow (prompt initiates, spec binds, implementation follows the approved contract; explore may produce nothing durable)
- [x] 1.2 Document conceptual prompt stages (exploration, specification, implementation, review, debugging, documentation) as categories only, plus adaptive structure (recommended sections, not a mandatory template; planning assistant vs Cursor; validation expectations point at specs/tasks)
- [x] 1.3 Document context management (reference, do not paste), external planning assistant vs Cursor vs OpenSpec boundaries (execution brief remains a disposable prompt; ChatGPT may be an example), quality guidelines, and storage/reuse (prompts are not assets; repeated patterns promote to docs, rules, skills, or agents)
- [x] 1.4 State that this page does not create prompt files, template catalogs, or `sdd-*` assets, and that conceptual stages are not templates to implement

## 2. Navigation and entrypoints

- [x] 2.1 Add a Practices link in `docs/README.md` to the human-AI interaction page
- [x] 2.2 Add a one-line pointer on `docs/architecture/overview.md` to the practice page without adding a fifth architecture layer or copying the practice
- [x] 2.3 Update `docs/lifecycle/openspec-workflow.md` so it states that prompts initiate lifecycle work and are not specifications, and points to the practice page
- [x] 2.4 Update `AGENTS.md` so an agent can locate the practice; keep `AGENTS.md` a short router
- [x] 2.5 Update root `README.md` so it points at the practice without copying it, and status reflects that the practice exists while prompt libraries and `sdd-*` catalogs still do not

## 3. Boundary verification

- [x] 3.1 Verify this change did not add a `prompts/` directory, prompt templates, `.cursor/` files, `sdd-*` assets, commands, agents, skills, an installer, MCP/plugin/hook config, a custom OpenSpec schema, or application code
- [x] 3.2 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged
- [x] 3.3 Run `openspec validate --change "define-sdd-human-ai-interaction-guidelines"` and resolve any validation issues in the change artifacts
