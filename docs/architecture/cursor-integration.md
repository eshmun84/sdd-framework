# Cursor integration

This document is the authoritative Cursor **component constitution** for the SDD Framework. It defines what `AGENTS.md`, rules, skills, commands, and agents are, when each should exist, and how they relate to OpenSpec and consuming projects.

It does not replace [architecture overview](overview.md) (four-layer model and asset ownership), [agent system](agent-system.md) (agent operating model), [skill system](skill-system.md) (skill operating model), or [OpenSpec lifecycle](../lifecycle/openspec-workflow.md) (vendor command behavior). Root entrypoints summarize or link here; they do not own a second copy.

Absence of a framework-owned `sdd-*` catalog is valid. This page is the constitution later catalog changes must follow. It is not permission to create those files now.

## Component stack

```
┌─────────────────────────────────────────────────────────────┐
│  AGENTS.md                                                  │
│  Routing contract: identity, navigation, document discovery │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Rules  (.cursor/rules/sdd-*.mdc)                           │
│  Operational constraints. Not methodology prose.            │
└─────────────────────────────────────────────────────────────┘
                              │
              user types /    │    agent decides
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Commands (optional trigger)     Skills (canonical procedure)│
│  Explicit human-named action     How to do a repeatable task │
└─────────────────────────────────────────────────────────────┘
                              │
                    delegates when isolation is needed
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Agents  (.cursor/agents/sdd-*.md)                          │
│  Cursor subagent specialists. Not orchestrators.            │
└─────────────────────────────────────────────────────────────┘
```

## Cheapest fitting primitive

Choose the cheapest primitive that fits. Do not invent a heavier one.

| Need | Primitive |
|---|---|
| Every session must know this identity or where truth lives | `AGENTS.md` |
| When editing these files, follow this operational constraint | Rule (prefer glob-scoped) |
| A reusable multi-step methodology procedure | Skill |
| A human must type a named action that must not auto-fire | Command (thin trigger) or a skill invoked only via `/` |
| Isolated context, parallel verification, or a distinct specialist persona | Agent (Cursor subagent) |
| OpenSpec change lifecycle | Vendor `opsx-*` / `openspec-*` only |
| Product, domain, or stack behavior | Consuming-project asset (not `sdd-*`) |

A single-purpose repeatable procedure that does not need isolated context is a **skill**, not an agent. Description-only “apply intelligently” rules that encode a procedure are skills in disguise; use a skill.

## AGENTS.md

`AGENTS.md` is the repository **AI routing contract**. It tells an agent what this repository is, where authoritative documentation lives, how OpenSpec is used, and which boundaries apply.

It is **not**:

- a replacement for `docs/`
- a Cursor rule file
- a home for glob-scoped or always-apply rules
- an SDD Framework agent

Keep it short. Point here and to other `docs/` pages instead of copying them.

## Rules

Rules encode **operational constraints** and conventions the agent should already know. They are not playbooks and not a second copy of methodology.

When a later change creates framework-owned rules:

- Live under `.cursor/rules/` with `sdd-*` names.
- State a constraint. Point at the authoritative `docs/` page. Do not copy that page into the rule.
- Prefer glob-scoped rules (for example, conventions that apply when editing `openspec/` or `docs/`).
- Always-apply rules are **exceptional**. `AGENTS.md` remains the default always-on identity surface. An always-apply rule is justified only when `AGENTS.md` cannot keep that constraint short.

## Skills

Skills are the **canonical reusable procedures**. A skill teaches how to do a methodology task in the current conversation. It is not a subagent and does not get its own context window.

When a later change creates a framework-owned procedure, it is a skill under `.cursor/skills/` with an `sdd-*` name. A duplicated command file is not required to hold the same procedure text.

Prefer invoking the skill with `/` when a human trigger is needed, including a skill that is only included when explicitly invoked, rather than cloning OpenSpec’s duplicated command-plus-skill files.

When a skill is justified, how it is invoked, how `SKILL.md` is structured, and how skill assets are evolved are defined in [skill system](skill-system.md). That page is the operating model. This constitution does not reproduce it.

## Commands

A framework-owned command exists **only** when a human needs an explicit named trigger that must not fire merely because an agent judged it relevant. A procedure alone is not enough reason to add a command.

If a command exists for a framework procedure:

- it is a **thin trigger** for the canonical skill
- it shares the same `sdd-*` name as that skill
- it does not own or duplicate the procedure

Commands live under `.cursor/commands/` when a separate command file is used. They complement vendor `/opsx-*`; they do not replace them.

## Agents

An SDD Framework agent is a **Cursor custom subagent** (later: `.cursor/agents/sdd-<role>.md`). It has isolated context and returns results to the parent.

It is **not** `AGENTS.md`. It is **not** the default Cursor Agent.

The **parent Cursor Agent** is the orchestrator. Framework agents are **leaf specialists**. They do not supervise other SDD agents, do not own `/opsx-*`, and are not product-domain experts.

Product-domain agents (for a consuming project’s business domain) stay in that project. They are not specified in this repository.

When an agent is justified, what it must not own, how multi-agent work is allowed, and how agent assets are evolved are defined in [agent system](agent-system.md). That page is the operating model. This constitution does not reproduce it.

```
User
  │
  ▼
Cursor Agent                          ← orchestrator
  │  AGENTS.md + future sdd rules + project rules
  │
  ├─ vendor skills     /opsx-*        ← OpenSpec lifecycle
  ├─ framework skills  /sdd-*         ← methodology procedures (later)
  ├─ project skills                   ← product / stack (not this repo)
  │
  └─ delegate
       ├─ Cursor built-in subagents
       ├─ sdd-* specialists           ← framework roles (later)
       └─ project specialists         ← product roles (not this repo)
```

## Ownership

| Layer | Owns in this model |
|---|---|
| **OpenSpec** | Change lifecycle, specification artifacts, vendor Cursor files (`opsx-*` commands, `openspec-*` skills) |
| **Cursor** | Execution environment: rules engine, skill loader, slash triggers, subagents |
| **SDD Framework** | Reusable methodology, this constitution, later `sdd-*` assets, conventions, governance |
| **Consuming projects** | Product specs, domain, code, their own OpenSpec workspace, local Cursor extensions outside reserved prefixes |

The framework does not redefine OpenSpec command semantics. Cursor does not replace OpenSpec. Consuming projects do not write product specifications into this repository.

## Naming and paths

Reserved prefixes are exclusive:

| Prefix | Owner | Primitive paths (when the asset exists) |
|---|---|---|
| `opsx-*` | OpenSpec (vendor) | `.cursor/commands/` |
| `openspec-*` | OpenSpec (vendor) | `.cursor/skills/` |
| `sdd-*` | SDD Framework | `.cursor/rules/`, `.cursor/skills/`, `.cursor/commands/`, `.cursor/agents/` matching the primitive |

Consuming-project Cursor assets **must not** use `opsx-*`, `openspec-*`, or `sdd-*`. They use project-specific names outside that set. A mandatory product prefix (for example a product name plus hyphen) is not required by this constitution.

Framework `sdd-*` names remain framework-owned after they are copied into a consuming project’s Cursor context. The project must not overwrite them in place with product-specific behavior. Promotion into the framework happens through this repository’s OpenSpec lifecycle.

A framework-owned asset lives in the `.cursor/` path that matches its primitive. Do not place a rule under `skills/`, a skill under `agents/`, or an agent under `commands/`.

If a command and skill represent the same framework action, they share one `sdd-*` name.

## OpenSpec is not wrapped

Do not create `sdd-*` commands or skills whose purpose is to replace, wrap, or redefine explore, propose, apply, update, sync, or archive. Use the vendor `opsx-*` / `openspec-*` surface. See [OpenSpec lifecycle](../lifecycle/openspec-workflow.md).

## Catalog status

This constitution does not require any `sdd-*` rule, skill, command, or agent file to exist. Empty stubs are not a catalog. The first framework-owned Cursor assets are a later OpenSpec change.

The following names are **non-normative examples** of how `sdd-*` might look. They are not assets to create in this change:

- `sdd-spec-authoring` (rule)
- `sdd-review-change` (skill)
- `sdd-spec-auditor` (agent)
