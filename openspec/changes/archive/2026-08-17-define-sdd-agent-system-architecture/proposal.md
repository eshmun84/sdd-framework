## Why

The Cursor component constitution maps an SDD agent to a Cursor custom subagent and already says specialists are leaves. It does not define the operating model: when an agent is justified, what it must not own, how multi-agent work is allowed without a runtime, or how an agent asset is proposed, changed, and deprecated. Without that model, the first `sdd-*` agent will become a disguised skill, wrap OpenSpec, or grow a hierarchy Cursor happens to allow.

## What Changes

- Define the SDD **agent system architecture**: identity relative to `AGENTS.md`, rules, skills, and commands; creation criteria; forbidden ownership; leaf hierarchy; multi-agent principles; OpenSpec lifecycle of agent assets; future file contract and naming.
- Add architecture documentation at `docs/architecture/agent-system.md`. Keep `docs/architecture/cursor-integration.md` as the component constitution; that page points here and does not become the agent handbook.
- Point `docs/README.md` and `AGENTS.md` at the new page without copying the operating model.
- Record that framework agent files, when later created, are version-controlled under `.cursor/agents/`.

This change is documentation and specification only. It does **not** create `.cursor/agents/` or any `sdd-*` agent file.

## Capabilities

### New Capabilities

- `sdd-agent-architecture`: Operating model for SDD Framework agents — identity, creation criteria, forbidden ownership, leaf hierarchy, multi-agent principles without a runtime, agent-asset lifecycle through OpenSpec, future `.cursor/agents/sdd-<role>.md` file contract, naming, and coexistence with consuming-project agents. Does not restate the Cursor component constitution.

### Modified Capabilities

- `documentation-architecture`: Architecture docs MUST include an agent-system page; the documentation index MUST link to it; `docs/architecture/cursor-integration.md` remains the Cursor component constitution and MUST NOT contain the full agent operating model.
- `repository-hygiene`: Shared Cursor agents that constitute the vendor or framework baseline MUST remain trackable when they exist, the same as commands, skills, and rules.

## Impact

- Documentation and specs only: new `docs/architecture/agent-system.md`, links from the Cursor integration page, docs index, and `AGENTS.md`; delta specs as listed above.
- No application code, installer, MCP, plugins, hooks, orchestration runtime, or Cursor agent files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Consuming projects are unaffected until a later catalog change creates framework agents. This change only defines the operating model those later assets must follow.

## Non-goals

- Creating `.cursor/agents/` or any `sdd-*` agent files, including empty stubs.
- A normative catalog of future `sdd-*` agent names (illustrative examples in design are non-normative).
- A multi-agent orchestration runtime, message bus, supervisor agent, or automation framework.
- MCP integrations, Cursor plugins, or hooks.
- Product-specific agents for consuming projects (AIRen, Nexus, or others).
- Replacing, wrapping, or redefining OpenSpec lifecycle commands or vendor Cursor assets.
- Reopening the Cursor component constitution (what a rule, skill, command, or agent primitive is).
- A skill-architecture deep dive or skill catalog.
- Changing the OpenSpec schema or this repository's specification universe.
