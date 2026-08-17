## Why

The Cursor component constitution maps an SDD skill to a reusable procedure that runs in the current conversation and already says commands must not own that text. It does not define the operating model: when a skill is justified, how it differs in practice from rules, agents, and commands, how `SKILL.md` is structured, how invocation works, or how a skill asset is proposed, changed, and deprecated. Without that model, the first `sdd-*` skill will become a persona, a documentation dump, a wrapped OpenSpec command, or a disguised rule.

## What Changes

- Define the SDD **skill system architecture**: identity relative to `AGENTS.md`, rules, commands, and agents; creation criteria; decision model; future file contract; invocation policy; quality bar; OpenSpec lifecycle of skill assets; naming and ownership.
- Add architecture documentation at `docs/architecture/skill-system.md`. Keep `docs/architecture/cursor-integration.md` as the component constitution; that page points here and does not become the skill handbook.
- Point `docs/README.md` and `AGENTS.md` at the new page without copying the operating model.
- Record that framework skill files, when later created, are version-controlled under `.cursor/skills/sdd-<procedure>/`.

This change is documentation and specification only. It does **not** create any `.cursor/skills/sdd-*` directory or skill file.

## Capabilities

### New Capabilities

- `sdd-skill-architecture`: Operating model for SDD Framework skills — identity, creation criteria, skill vs agent/rule/command, future `.cursor/skills/sdd-<procedure>/SKILL.md` file contract, invocation policy, composition limits, quality bar, skill-asset lifecycle through OpenSpec, naming, and coexistence with consuming-project skills. Does not restate the Cursor component constitution.

### Modified Capabilities

- `documentation-architecture`: Architecture docs MUST include a skill-system page; the documentation index MUST link to it; `docs/architecture/cursor-integration.md` remains the Cursor component constitution and MUST NOT contain the full skill operating model.

## Impact

- Documentation and specs only: new `docs/architecture/skill-system.md`, links from the Cursor integration page, docs index, and `AGENTS.md`; delta specs as listed above.
- No application code, installer, MCP, plugins, hooks, scripts, commands, agents, or Cursor skill files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Consuming projects are unaffected until a later catalog change creates framework skills. This change only defines the operating model those later assets must follow.

## Non-goals

- Creating `.cursor/skills/sdd-*` or any skill files, including empty stubs.
- A normative catalog of future `sdd-*` skill names (illustrative examples in design are non-normative).
- Creating framework-owned commands or agents.
- Executable scripts inside skills.
- Installer or synchronization tooling.
- MCP integrations, Cursor plugins, or hooks.
- Product-specific skills for consuming projects (AIRen, Nexus, or others).
- Replacing, wrapping, or redefining OpenSpec lifecycle commands or vendor Cursor assets.
- Reopening the Cursor component constitution (what a rule, skill, command, or agent primitive is).
- Reopening the agent operating model (when an agent is justified).
- Changing the OpenSpec schema or this repository's specification universe.
