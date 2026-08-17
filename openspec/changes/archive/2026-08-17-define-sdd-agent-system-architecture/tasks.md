## 1. Agent-system architecture page

- [x] 1.1 Create `docs/architecture/agent-system.md` covering agent identity vs `AGENTS.md`, rules, skills, and commands; creation criteria (stance, independent reasoning, isolation; procedural work is a skill); and forbidden ownership (OpenSpec lifecycle, git, product implementation, global orchestration)
- [x] 1.2 Document hierarchy (parent Cursor Agent orchestrates; SDD agents are leaves; no SDD-to-SDD spawn; no framework agent hierarchy) and multi-agent principles (parent fan-out, parallel reviews, no bus/supervisor/runtime)
- [x] 1.3 Document agent-asset lifecycle through OpenSpec, the future file contract (`.cursor/agents/sdd-<role>.md`, project tree only, no-write default, inherit parent model, stance not playbook), naming (`sdd-<role>`; project names outside reserved prefixes; no in-place overwrite), and that absence of agent files is valid
- [x] 1.4 Mark any naming examples as non-normative and not assets to create in this change

## 2. Navigation and entrypoints

- [x] 2.1 Point the Agents section of `docs/architecture/cursor-integration.md` at the agent-system page without copying the operating model into the constitution
- [x] 2.2 Add a `docs/README.md` index link to the agent-system architecture page
- [x] 2.3 Update `docs/architecture/overview.md` with a pointer to the agent-system page while keeping it the four-layer summary
- [x] 2.4 Update `AGENTS.md` so an agent can locate the agent operating model; keep `AGENTS.md` a short router; retain the instruction not to invent a `sdd-*` catalog until a later change specifies it
- [x] 2.5 Update root `README.md` status so it reflects that the agent operating model is specified while an agent catalog still does not exist

## 3. Hygiene and boundary verification

- [x] 3.1 Verify `.gitignore` does not exclude `.cursor/agents/`; extend the existing comment that names commands and skills so agents are also called out as trackable
- [x] 3.2 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged and still documented as vendor-managed
- [x] 3.3 Verify this change did not add `.cursor/agents/`, any `sdd-*` Cursor files, an installer, MCP/plugin/hook config, a custom OpenSpec schema, application code, or a multi-agent runtime
- [x] 3.4 Run `openspec validate --change "define-sdd-agent-system-architecture"` and resolve any validation issues in the change artifacts
