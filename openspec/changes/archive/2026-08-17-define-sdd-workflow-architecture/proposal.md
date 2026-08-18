## Why

The framework already defines Cursor primitives, agent/skill/rule operating models, prompting practice, vendor OpenSpec lifecycle, adoption, and this-repository governance. Those pages do not compose into one operating model for how humans, optional planning assistants, Cursor, OpenSpec, and implementation work collaborate through a change. Without that model, teams treat chat as the contract, skip proposal because a prompt felt complete, invent review commands that wrap OpenSpec, or assume consuming projects share this repository's specification universe.

## What Changes

- Define the SDD **workflow architecture**: identity as a collaboration operating model (not a fifth architecture layer, not a workflow engine); canonical change-lifecycle stages and boundaries; participant responsibilities; durable versus session information; human approval gates; review as an SDD stage without a new OpenSpec command; incomplete, rejected, and evolving work; same workflow in independent OpenSpec universes.
- Add architecture documentation at `docs/architecture/workflow-system.md`. Keep the four-layer overview unchanged. Keep `docs/lifecycle/openspec-workflow.md` as the vendor OpenSpec surface. Keep `docs/practices/human-ai-interaction.md` as prompt practice. Keep `docs/governance/working-agreements.md` as this-repository governance. Those pages point here and do not own a second copy of the collaboration model.
- Point `docs/README.md`, `README.md`, and `AGENTS.md` at the new page without copying the operating model. Soften `AGENTS.md` so it requires OpenSpec artifacts rather than a mandatory command sequence.

This change is documentation and specification only. It does **not** create `.cursor/` assets, `sdd-*` catalog files, prompt libraries, or automation.

## Capabilities

### New Capabilities

- `sdd-workflow-architecture`: Operating model for how a change moves from intent to archived contract — identity, lifecycle stages and boundaries, participant responsibilities, durable versus temporary information, human gates, review without a vendor command, incomplete/rejected handling, framework and consuming-project applicability, and non-engine constraints. Does not restate Cursor, agent, skill, rule, adoption, or human-AI operating models.

### Modified Capabilities

- `documentation-architecture`: Architecture docs MUST include a workflow-system page; the documentation index MUST link to it; `docs/architecture/overview.md` remains the four-layer summary and MUST NOT add a fifth architecture layer; lifecycle, human-AI practice, and working-agreements pages MUST point to the workflow page rather than owning a second copy.

## Impact

- Documentation and specs only: new `docs/architecture/workflow-system.md`; thin pointers from overview, OpenSpec lifecycle, human-AI practice, working agreements, docs index, `README.md`, and `AGENTS.md`; delta specs as listed above.
- No application code, installer, MCP, plugins, hooks, orchestration runtime, prompt folders, templates, or Cursor asset files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Cursor component, agent, skill, rule, adoption, and human-AI contracts are not reopened except for navigation pointers.
- Consuming projects receive the methodology later via the `docs/sdd-framework/` snapshot. They do not receive this repository's OpenSpec universe.

## Non-goals

- Creating `.cursor/` assets or any `sdd-*` skills, rules, agents, or commands, including empty stubs.
- Workflow automation, scripts, hooks, MCP integrations, plugins, or an orchestrator runtime.
- Wrapping, renaming, or redefining vendor OpenSpec commands (`/opsx-*`) or skills (`openspec-*`).
- Prompt libraries, prompt folders, or prompt templates.
- Making planning assistants mandatory.
- Adding CI agents, cloud execution models, or additional implementation environments as specified participants.
- Redefining the Cursor component constitution, agent architecture, skill architecture, rule architecture, human-AI interaction practice, or project adoption model.
- Product-specific workflows for AIRen, Nexus, or other consuming projects.
- Changing the OpenSpec schema or mixing specification universes.
