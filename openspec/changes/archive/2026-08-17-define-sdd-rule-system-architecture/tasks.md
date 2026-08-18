## 1. Rule-system architecture page

- [x] 1.1 Create `docs/architecture/rule-system.md` covering rule identity vs `AGENTS.md`, skills, agents, commands, specifications, documentation, and prompts; creation criteria (persistent constraint, repeatable applicability, operational wording, copy-validity, cheapest primitive); and when not to create a rule (procedure, persona, identity, requirement, prose, prompt, dogfood-only, vendor OpenSpec)
- [x] 1.2 Document the decision model, activation policy (glob default on copy-safe paths, always-apply exceptional, no description-only, no manual distribution, no `openspec/**` or `docs/**` globs), parent-session binding, and the quality bar (concise, one concern, referential, not a hidden spec, not a skill, not a persona)
- [x] 1.3 Document rule-asset lifecycle through OpenSpec, the future file contract (`.cursor/rules/sdd-<concern>.mdc`, project tree only, constraint plus pointer, no procedure composition), naming (`sdd-<concern>`; project names outside reserved prefixes; no in-place overwrite), adoption participation in existing copy/pin, and that absence of rule files is valid
- [x] 1.4 Mark any naming examples as non-normative and not assets to create in this change; keep the constitution's `sdd-spec-authoring` example naming-only, not a glob or catalog entry

## 2. Navigation and entrypoints

- [x] 2.1 Point the Rules section of `docs/architecture/cursor-integration.md` at the rule-system page without copying the operating model into the constitution
- [x] 2.2 Add a `docs/README.md` index link to the rule-system architecture page
- [x] 2.3 Update `docs/architecture/overview.md` with a pointer to the rule-system page while keeping it the four-layer summary
- [x] 2.4 Update `AGENTS.md` so an agent can locate the rule operating model; keep `AGENTS.md` a short router; retain the instruction not to invent a `sdd-*` catalog until a later change specifies it
- [x] 2.5 Update root `README.md` status so it reflects that the rule operating model is specified while a rule catalog still does not exist

## 3. Boundary verification

- [x] 3.1 Verify `.gitignore` does not exclude `.cursor/rules/` and extend the existing comment that names commands, skills, and agents so rules are also called out as trackable
- [x] 3.2 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged and still documented as vendor-managed
- [x] 3.3 Verify this change did not add `.cursor/rules/`, any `sdd-*` Cursor files, templates, an installer, MCP/plugin/hook config, a custom OpenSpec schema, or application code
- [x] 3.4 Run `openspec validate define-sdd-rule-system-architecture --type change --strict` and resolve any validation issues in the change artifacts
