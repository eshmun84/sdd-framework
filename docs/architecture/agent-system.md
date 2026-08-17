# Agent system

This document is the authoritative **agent operating model** for the SDD Framework. It defines when an SDD agent is justified, what it must not own, how specialists relate to the parent Cursor Agent, and how agent assets are evolved.

It does not replace [Cursor integration](cursor-integration.md) (what a rule, skill, command, or agent *is*). That page is the component constitution. This page is the operating model later `sdd-*` agent changes must follow. It is not permission to create those files now.

Absence of framework-owned agent files is valid.

## Identity

An SDD agent is an **isolated specialist**. It returns independent analysis to the parent Cursor Agent. Independence is of context and judgment, not of control flow. The parent still decides whether and when to launch it.

It is **not**:

- an orchestrator
- a workflow engine
- an OpenSpec wrapper
- a product owner
- `AGENTS.md`
- the default Cursor Agent

The **parent Cursor Agent** remains the session orchestrator.

This page does not redefine Cursor primitives. Those definitions live in [Cursor integration](cursor-integration.md). In this operating model they are used as follows:

| Primitive | Role in this model |
|---|---|
| `AGENTS.md` | Routing contract for every session |
| Rule | Operational constraint |
| Skill | Procedure that runs in the current conversation |
| Command | Optional human-named trigger |
| SDD agent | Isolated specialist that returns analysis to the parent |

## Creation criteria

A framework-owned agent is justified only when **all** of these are true:

1. A **specialized stance** (a distinct reviewer, auditor, or critic — not “do these steps”).
2. **Independent reasoning** is the value (a second mind, not the implementer wearing a hat).
3. **Context isolation** is required (fresh eyes, uncontaminated by the implementation conversation).

A reusable procedure that can run in the current conversation is a **skill**, not an agent. Isolation justification must be recorded in the OpenSpec change that would create the agent.

## Forbidden ownership

SDD agents must not own:

| Concern | Owner instead |
|---|---|
| OpenSpec change lifecycle | Vendor `opsx-*` / `openspec-*` |
| Git operations | Parent Cursor Agent and the human |
| Product implementation decisions | Consuming-project specifications and the parent applying an approved change |
| Global orchestration | Parent Cursor Agent |

Do not create a framework agent whose purpose is explore, propose, apply, update, sync, or archive. Use the vendor surface. See [OpenSpec lifecycle](../lifecycle/openspec-workflow.md).

Cursor subagents inherit parent tools. The framework does not invent a tool allowlist. The no-write default in the [file contract](#file-contract) is the enforcement story for git and edits.

## Hierarchy

```
User
  │
  ▼
Cursor Main Agent                     ← only orchestrator of SDD agents
  │
  ├─ vendor skills     /opsx-*
  ├─ framework skills  /sdd-*         ← later
  │
  └─ delegate (serial or parallel)
       ├─ Cursor built-in subagents   ← Cursor-owned, not sdd-*
       ├─ sdd-* specialists           ← leaves (later)
       └─ project specialists         ← not this repo
```

Framework agents are **leaf specialists**. An SDD agent must not spawn, supervise, or orchestrate another SDD agent. The framework does not define an agent hierarchy or a supervisor agent.

Cursor built-in subagents (`explore`, `shell`, `browser`) are Cursor-owned primitives. They are not SDD agents. This model does not treat them as a framework org chart.

## Multi-agent principles

The parent **may** launch multiple specialists for parallel reviews, independent analysis, or specialist validation. Specialists return findings to the parent. They do not communicate with one another through a framework-defined channel. The parent synthesizes disagreement.

The framework does **not** specify:

- an orchestration runtime
- a message bus
- a supervisor agent

Cursor parent delegation is sufficient. Background or cloud execution is a Cursor mode, not a framework design.

## Lifecycle

Creating, changing, or deprecating a framework-owned agent requires an OpenSpec change in this repository. Silent addition, in-place product overwrite, or undocumented deletion is not permitted.

A later change that implements an agent must record:

- isolation justification (why not a skill)
- the specialist stance
- forbidden ownership

Typical orientation (not a mandatory command sequence): explore → propose → apply → sync → archive. See [working agreements](../governance/working-agreements.md).

## File contract

When a later change creates a framework-owned agent:

- Path: `.cursor/agents/sdd-<role>.md` in the **project** Cursor tree.
- Not distributed as a user-level agent (`~/.cursor/agents/`).
- Not homed in `.claude/agents/` or `.codex/agents/` as the framework location.
- Configured so it cannot edit files or run state-changing shell commands unless that later change justifies writes.
- Uses the parent agent's model unless that later change specifies otherwise. Do not pin vendor model IDs as the framework default.
- Body encodes specialist stance and forbidden ownership. Point at `docs/`. Do not copy a methodology page into the agent file. Playbooks are skills.

This page does not create those files.

## Naming and project coexistence

Framework agents use `sdd-<role>` (a noun-role). Consuming-project agents use names outside `opsx-*`, `openspec-*`, and `sdd-*`. They must not overwrite framework `sdd-*` agents in place. Domain or product agents stay in the consuming project. Promotion into the framework happens through this repository's OpenSpec lifecycle.

A mandatory product prefix is not required by this operating model. See [Cursor integration](cursor-integration.md) for reserved prefixes and [adoption](adoption.md) for how projects consume the baseline.

## Catalog status

This operating model does not require any `sdd-*` agent file or `.cursor/agents/` directory to exist. Empty stubs are not a catalog. The first framework-owned agents are a later OpenSpec change.

The following names are **non-normative examples** of how `sdd-<role>` might look. They are not assets to create in this change:

- `sdd-spec-reviewer`
- `sdd-security-reviewer`
