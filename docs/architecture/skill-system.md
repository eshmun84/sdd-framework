# Skill system

This document is the authoritative **skill operating model** for the SDD Framework. It defines when an SDD skill is justified, how it differs from rules, agents, and commands, how future skill files are structured and invoked, and how skill assets are evolved.

It does not replace [Cursor integration](cursor-integration.md) (what a rule, skill, command, or agent *is*). That page is the component constitution. This page is the operating model later `sdd-*` skill changes must follow. It is not permission to create those files now.

Isolation justification for specialists lives in [agent system](agent-system.md). This page owns the skill-side test and does not reproduce that operating model.

Absence of framework-owned skill files is valid.

## Identity

An SDD skill is a **reusable procedure**. It teaches the parent Cursor Agent how to perform a known methodology task in the current conversation.

It is **not**:

- an independent reasoning entity
- a documentation container
- an orchestrator
- an OpenSpec wrapper
- a persistent constraint
- `AGENTS.md`

This page does not redefine Cursor primitives. Those definitions live in [Cursor integration](cursor-integration.md). In this operating model they are used as follows:

| Primitive | Role in this model |
|---|---|
| `AGENTS.md` | Routing contract for every session |
| Rule | Persistent operational constraint |
| Skill | Invoked procedure in the current conversation |
| Command | Optional thin trigger; does not own procedure text |
| SDD agent | Isolated specialist that returns analysis to the parent |

## Creation criteria

A framework-owned skill is justified only when **all** of these are true:

1. A **repeatable procedure** (the same steps, different inputs).
2. A **known workflow** (execution of a method, not exploration).
3. **Reusable methodology** (framework practice, not a consuming project's domain or stack).
4. **Predictable inputs and outputs** (the task type can be named).

Do **not** create a skill when:

| Situation | Use instead |
|---|---|
| Independent judgment, specialist perspective, or isolation from the implementation conversation | Agent — see [agent system](agent-system.md) |
| Persistent operational restriction the agent should already know | Rule |
| Repository identity or navigation | `AGENTS.md` |
| Methodology prose | `docs/` |
| Explore, propose, apply, update, sync, or archive | Vendor `opsx-*` / `openspec-*` — see [OpenSpec lifecycle](../lifecycle/openspec-workflow.md) |

A later change that implements a skill must record why the asset is a skill rather than a rule, agent, documentation page, or vendor OpenSpec asset.

## Decision model

### Skill vs agent

Use a **skill** when the value is the procedure, the current conversation is enough, and the steps repeat with different inputs.

Use an **agent** when the value is isolated context, independent judgment, and a specialist perspective. Record isolation justification in the OpenSpec change that would create the agent. See [agent system](agent-system.md).

A persona without a procedure is not a skill. A playbook stuffed into a subagent file is not an agent.

### Skill vs rule

A **skill** is an invoked procedure. A **rule** is a persistent constraint (prefer glob-scoped).

Do not put step-by-step methods in rules. Do not put always-on constraints in skills. Skill-local constraints (restrictions that apply only while the procedure runs) belong in the skill.

### Skill vs command

The **skill** is the canonical procedure. A **command**, if it exists, is an optional thin trigger that shares the same `sdd-*` name and does not duplicate procedure text.

A procedure alone is not a reason to add a command. This architecture does not require `.cursor/commands/sdd-*`. Prefer invoking the skill with `/` rather than cloning OpenSpec’s duplicated command-plus-skill files.

## Invocation

Framework-owned skills **default to explicit invocation** (named by the human or included only when explicitly invoked).

Description-based discovery is allowed only when the OpenSpec change that creates the skill records why ambient discovery is still a procedure and not a rule.

Always-on skill behavior is forbidden. Always-on identity stays in `AGENTS.md`. Always-on constraints stay in rules.

## Composition

A skill **may** name another `sdd-*` skill as a step in the same conversation.

A skill **may** instruct the parent Cursor Agent to delegate to a specialist when a step requires isolation. The parent remains the orchestrator.

A skill **must not** own agents, supervise `sdd-*` agents, become a workflow engine, or wrap OpenSpec.

## Quality

A valid SDD skill has a narrow purpose. It points at `docs/` instead of copying methodology. It does not impersonate an agent. It does not wrap OpenSpec. It does not become a workflow engine.

`SKILL.md` encodes the steps the agent cannot infer. It is not a reprint of this operating model or of `docs/`.

## Lifecycle

Creating, changing, or deprecating a framework-owned skill requires an OpenSpec change in this repository. Silent addition, in-place product overwrite, or undocumented deletion is not permitted. Shared classification, publication, adoption, and retirement are defined in [asset lifecycle](asset-lifecycle.md). This page does not own a second copy of that model.

A later change that implements a skill must record why it is a skill rather than a rule, agent, documentation page, or vendor OpenSpec asset.

Typical orientation (not a mandatory command sequence): explore → propose → apply → sync → archive. See [working agreements](../governance/working-agreements.md).

## File contract

When a later change creates a framework-owned skill:

- Path: `.cursor/skills/sdd-<procedure>/SKILL.md` in the **project** Cursor tree.
- Not distributed as a user-level skill (`~/.cursor/skills/`).
- Not homed in Cursor’s internal skill directories as the framework location.
- Optional supporting reference files stay one level deep from `SKILL.md`.
- `SKILL.md` encodes purpose, trigger conditions, instructions, skill-local constraints, references to authoritative `docs/`, and named outputs. Do not copy a methodology page into the skill file.
- Markdown-first. Executable scripts inside skills are out of scope for this operating model. A valid skill does not require a `scripts/` directory.

This page does not create those files.

## Naming and project coexistence

Framework skills use `sdd-<procedure>` (a verb or task phrase). That contrasts with agent `sdd-<role>` (a noun-role). Consuming-project skills use names outside `opsx-*`, `openspec-*`, and `sdd-*`. They must not overwrite framework `sdd-*` skills in place. Domain, product, or stack skills stay in the consuming project. Promotion into the framework happens through this repository's OpenSpec lifecycle.

If a command exists for the same framework action, it shares the skill’s `sdd-*` name.

A mandatory product prefix is not required by this operating model. See [Cursor integration](cursor-integration.md) for reserved prefixes and [adoption](adoption.md) for how projects consume the baseline.

## Catalog status

This operating model does not require any `sdd-*` skill file or `.cursor/skills/sdd-*` directory to exist. Empty stubs are not a catalog. The first framework-owned skills are a later OpenSpec change.

The following name is a **non-normative example** of how `sdd-<procedure>` might look. It is not an asset to create in this change:

- `sdd-review-change`

Conceptual buckets such as specification, review, development, and documentation may describe later catalog work. They are not a reserved list of skills to implement now.
