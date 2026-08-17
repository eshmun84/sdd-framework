## 1. Cursor integration architecture page

- [x] 1.1 Create `docs/architecture/cursor-integration.md` as the authoritative Cursor component constitution covering `AGENTS.md` (router, not a rule catalog), rules (operational constraints; always-apply exceptional; do not duplicate `docs/`), skills (canonical procedures), commands (optional human triggers; thin; same `sdd-*` name as the skill), and agents (Cursor subagent specialists; parent orchestrates; leaves only)
- [x] 1.2 Document ownership boundaries (OpenSpec lifecycle and vendor assets; Cursor primitives; framework `sdd-*` methodology; consuming-project extensions) and the cheapest-fitting-primitive rule
- [x] 1.3 Document reserved prefixes (`opsx-*`, `openspec-*`, `sdd-*`), primitive-matched `.cursor/` paths, the ban on wrapping OpenSpec lifecycle as `sdd-*`, and that project assets MUST NOT use or overwrite reserved names
- [x] 1.4 State that absence of a `sdd-*` catalog is valid; mark any naming examples as non-normative and not assets to create in this change

## 2. Navigation and entrypoints

- [x] 2.1 Add a `docs/README.md` index link to the Cursor integration architecture page
- [x] 2.2 Update `docs/architecture/overview.md` so it remains the four-layer summary and points to the Cursor integration page without reproducing the constitution
- [x] 2.3 Update `AGENTS.md` so an agent can locate the Cursor component model, keep `AGENTS.md` a short router, and retain the instruction not to invent a `sdd-*` catalog in this repository until a later change specifies it
- [x] 2.4 Update root `README.md` status so it reflects that Cursor architecture is specified while a skill, agent, or command catalog still does not exist

## 3. Boundary verification

- [x] 3.1 Verify existing `.cursor/commands/opsx-*` and `.cursor/skills/openspec-*` files are unchanged and still documented as vendor-managed
- [x] 3.2 Verify this change did not add `.cursor/rules/`, `.cursor/agents/`, any `sdd-*` Cursor files, an installer, MCP/plugin/hook config, a custom OpenSpec schema, or application code
- [x] 3.3 Run `openspec validate --change "define-sdd-cursor-architecture"` and resolve any validation issues in the change artifacts
