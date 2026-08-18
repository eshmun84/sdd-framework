## Why

The Cursor component constitution maps an SDD rule to a persistent operational constraint and already says always-apply rules are exceptional. It does not define the operating model: when a rule is justified, how activation is chosen, how a rule stays valid after copy/pin, or how a rule asset is proposed, changed, and deprecated. Without that model, the first `sdd-*` rule will become duplicated documentation, a hidden specification, a procedural skill, an agent persona, or a dogfood constraint that is wrong in a consuming project.

## What Changes

- Define the SDD **rule system architecture**: identity relative to `AGENTS.md`, skills, agents, commands, specifications, documentation, and prompts; creation criteria including copy-validity; activation policy; future file contract; quality bar; OpenSpec lifecycle of rule assets; naming and ownership.
- Add architecture documentation at `docs/architecture/rule-system.md`. Keep `docs/architecture/cursor-integration.md` as the component constitution; that page points here and does not become the rule handbook.
- Point `docs/architecture/overview.md`, `docs/README.md`, and `AGENTS.md` at the new page without copying the operating model.
- Record that framework rule files, when later created, are version-controlled under `.cursor/rules/sdd-<concern>.mdc`.

This change is documentation and specification only. It does **not** create `.cursor/rules/` or any `sdd-*` rule file.

## Capabilities

### New Capabilities

- `sdd-rule-architecture`: Operating model for SDD Framework rules — identity, creation criteria, rule vs other primitives, activation policy, future `.cursor/rules/sdd-<concern>.mdc` file contract, quality bar, rule-asset lifecycle through OpenSpec, naming, copy-validity, and coexistence with consuming-project rules. Does not restate the Cursor component constitution.

### Modified Capabilities

- `documentation-architecture`: Architecture docs MUST include a rule-system page; the documentation index MUST link to it; `docs/architecture/cursor-integration.md` remains the Cursor component constitution and MUST NOT contain the full rule operating model.

## Impact

- Documentation and specs only: new `docs/architecture/rule-system.md`, links from the Cursor integration page, architecture overview, docs index, and `AGENTS.md`; delta specs as listed above.
- No application code, installer, MCP, plugins, hooks, templates, or Cursor rule files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Consuming projects are unaffected until a later catalog change creates framework rules. This change only defines the operating model those later assets must follow.
- `project-adoption` and `cursor-asset-model` already list `.cursor/rules/sdd-*` as copyable framework-owned assets; this change does not alter that inventory.

## Non-goals

- Creating `.cursor/rules/` or any `sdd-*` rule files, including empty stubs.
- A normative catalog of future `sdd-*` rule names (illustrative examples in design are non-normative).
- Creating templates, installers, or synchronization tooling.
- Creating framework-owned skills, commands, or agents.
- MCP integrations, Cursor plugins, or hooks.
- Defining consuming-project rule catalogs (coexistence and reserved prefixes only).
- Replacing, wrapping, or redefining OpenSpec lifecycle commands or vendor Cursor assets.
- Reopening the Cursor component constitution (what a rule, skill, command, or agent primitive is).
- Reopening the agent operating model or the skill operating model.
- Changing the OpenSpec schema or this repository's specification universe.
