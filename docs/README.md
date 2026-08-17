# SDD Framework documentation

This is the documentation index for the SDD Framework.

`docs/` is the canonical location for methodology prose. OpenSpec specifications under `openspec/specs/` are the requirement contract for the framework itself. Root `README.md` is the human entrypoint. Root `AGENTS.md` is the AI-agent entrypoint. Those entrypoints summarize and link here; they do not replace this tree.

## Contents

- [Principles](principles.md) — core working principles of the framework
- [Architecture overview](architecture/overview.md) — four-layer relationship and Cursor asset ownership
- [Cursor integration](architecture/cursor-integration.md) — Cursor component constitution (`AGENTS.md`, rules, skills, commands, agents)
- [Agent system](architecture/agent-system.md) — SDD agent operating model (identity, creation criteria, boundaries, lifecycle)
- [Skill system](architecture/skill-system.md) — SDD skill operating model (identity, creation criteria, invocation, lifecycle)
- [Project adoption](architecture/adoption.md) — how consuming projects take a versioned baseline
- [OpenSpec lifecycle](lifecycle/openspec-workflow.md) — native change workflow used in this repository
- [Working agreements](governance/working-agreements.md) — how framework changes are specified, reviewed, and archived
