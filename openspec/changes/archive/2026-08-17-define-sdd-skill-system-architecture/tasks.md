## 1. Skill-system architecture page

- [x] 1.1 Create `docs/architecture/skill-system.md` covering skill identity vs `AGENTS.md`, rules, commands, and agents; creation criteria (repeatable procedure, known workflow, reusable methodology, predictable inputs/outputs); and when not to create a skill (agent, rule, `AGENTS.md`, `docs/`, vendor OpenSpec)
- [x] 1.2 Document the skill vs agent/rule/command decision model, invocation policy (explicit default, justified description discovery, no always-on skills), composition limits (same-conversation chaining, parent delegation, no workflow engine), and the quality bar (narrow purpose, no docs dump, no persona, no OpenSpec wrap)
- [x] 1.3 Document skill-asset lifecycle through OpenSpec, the future file contract (`.cursor/skills/sdd-<procedure>/SKILL.md`, project tree only, optional one-level references, markdown-first, no scripts in this architecture), naming (`sdd-<procedure>`; project names outside reserved prefixes; no in-place overwrite), and that absence of skill files is valid
- [x] 1.4 Mark any naming examples and conceptual categories as non-normative and not assets to create in this change

## 2. Navigation and entrypoints

- [x] 2.1 Point the Skills section of `docs/architecture/cursor-integration.md` at the skill-system page without copying the operating model into the constitution
- [x] 2.2 Add a `docs/README.md` index link to the skill-system architecture page
- [x] 2.3 Update `docs/architecture/overview.md` with a pointer to the skill-system page while keeping it the four-layer summary
- [x] 2.4 Update `AGENTS.md` so an agent can locate the skill operating model; keep `AGENTS.md` a short router; retain the instruction not to invent a `sdd-*` catalog until a later change specifies it
- [x] 2.5 Update root `README.md` status so it reflects that the skill operating model is specified while a skill catalog still does not exist

## 3. Boundary verification

- [x] 3.1 Verify `.gitignore` does not exclude `.cursor/skills/` and that existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged and still documented as vendor-managed
- [x] 3.2 Verify this change did not add `.cursor/skills/sdd-*`, any other `sdd-*` Cursor files, commands, agents, scripts, an installer, MCP/plugin/hook config, a custom OpenSpec schema, or application code
- [x] 3.3 Run `openspec validate --change "define-sdd-skill-system-architecture"` and resolve any validation issues in the change artifacts
