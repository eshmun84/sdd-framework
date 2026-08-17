## Why

The foundation locked Cursor **ownership and namespaces** (`opsx-*` / `openspec-*` vs future `sdd-*`) but not what a rule, skill, command, or agent *is*, when each should exist, or how they interact with `AGENTS.md`, OpenSpec, and consuming projects. Without that constitution, the first `sdd-*` assets will invent conflicting shapes, wrap OpenSpec, or duplicate `docs/`. The model must be specified now, before any framework-owned Cursor files are created.

## What Changes

- Define a Cursor **component model**: `AGENTS.md` as routing contract; rules as operational constraints; skills as canonical procedures; commands as optional human triggers; agents as Cursor subagent specialists.
- Record ownership boundaries among OpenSpec (lifecycle and vendor assets), Cursor (execution primitives), the SDD Framework (reusable methodology assets under `sdd-*`), and consuming projects (local extensions outside reserved prefixes).
- Document naming: reserved vendor and framework prefixes; project assets MUST NOT use `opsx-*`, `openspec-*`, or `sdd-*`.
- Add architecture documentation at `docs/architecture/cursor-integration.md`. Keep `docs/architecture/overview.md` as the four-layer summary.
- Tighten `cursor-asset-model` so reserved prefixes are exclusive. Extend `documentation-architecture` so the docs tree requires the Cursor integration page.
- Point `AGENTS.md`, `docs/README.md`, and the overview at the new page without copying the constitution into those files.

This change is documentation and specification only. It does **not** create `.cursor/rules/`, `.cursor/agents/`, `sdd-*` skills, or `sdd-*` commands.

## Capabilities

### New Capabilities

- `cursor-component-model`: Responsibilities and interaction rules for `AGENTS.md`, rules, skills, commands, and agents; when each primitive is used; parent-orchestrator vs specialist-subagent; skills as canonical procedures; prohibition on wrapping OpenSpec lifecycle as `sdd-*`.

### Modified Capabilities

- `documentation-architecture`: Architecture docs MUST include a Cursor integration page; the documentation index MUST link to it; `docs/architecture/overview.md` remains the four-layer summary and MUST NOT become the component constitution.
- `cursor-asset-model`: Reserved prefixes (`opsx-*`, `openspec-*`, `sdd-*`) are exclusive. Consuming-project Cursor assets SHALL NOT use those prefixes. Framework-owned assets, when later created, SHALL use the Cursor paths that match their primitive.

## Impact

- Documentation and specs only: new `docs/architecture/cursor-integration.md`, links from overview, docs index, and `AGENTS.md`; delta specs as listed above.
- No application code, installer, MCP, plugins, hooks, or Cursor asset files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Consuming projects are unaffected until a later catalog and adoption-sync change. This change only defines the constitution those later assets must follow.

## Non-goals

- Creating any `sdd-*` rules, skills, commands, or agents.
- Implementing a multi-agent system or product-specific agents (AIRen, Nexus, or other consuming projects).
- Installer or synchronization tooling.
- MCP servers, Cursor plugins, or hooks.
- Replacing, wrapping, or redefining OpenSpec lifecycle commands or vendor Cursor assets.
- A normative catalog of future `sdd-*` names (illustrative examples in design are non-normative).
- Changing the OpenSpec schema or this repository's specification universe.
