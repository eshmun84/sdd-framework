# Rule system

This document is the authoritative **rule operating model** for the SDD Framework. It defines when an SDD rule is justified, how it differs from `AGENTS.md`, skills, agents, commands, specifications, documentation, and prompts, how future rule files are activated and structured, and how rule assets are evolved.

It does not replace [Cursor integration](cursor-integration.md) (what a rule, skill, command, or agent *is*). That page is the component constitution. This page is the operating model later `sdd-*` rule changes must follow. It is not permission to create those files now.

Procedure justification lives in [skill system](skill-system.md). Isolation justification for specialists lives in [agent system](agent-system.md). This page owns the rule-side test and does not reproduce those operating models.

Absence of framework-owned rule files is valid.

## Identity

An SDD rule is a **persistent operational constraint**. It binds the parent Cursor Agent when relevant work is in play, without requiring invocation. Its value is preventing a known, repeatable class of mistakes.

It is **not**:

- documentation
- a specification
- a procedure
- a persona
- a prompt
- an OpenSpec wrapper
- a consuming-project convention
- `AGENTS.md`

This page does not redefine Cursor primitives. Those definitions live in [Cursor integration](cursor-integration.md). In this operating model they are used as follows:

| Primitive | Role in this model |
|---|---|
| `AGENTS.md` | Routing contract: identity and navigation |
| Rule | Persistent operational constraint |
| Skill | Invoked procedure in the current conversation |
| Command | Optional thin trigger; does not own procedure text |
| SDD agent | Isolated specialist that returns analysis to the parent |
| OpenSpec specification | Requirement contract |
| `docs/` | Explanation and methodology prose |
| Prompt | Session-scoped instruction |

## Creation criteria

A framework-owned rule is justified only when **all** of these are true:

1. A **persistent constraint** (must / must-not the agent should already know).
2. **Repeatable applicability** (the same mistake class, different sessions).
3. **Operational wording** (constraint, not explanation).
4. **Copy-validity** (still true after copy/pin into a consuming project).
5. **Cheapest primitive** (no cheaper home fits).

Do **not** create a rule when:

| Situation | Use instead |
|---|---|
| Repository identity or navigation | `AGENTS.md` |
| A framework requirement | OpenSpec specification |
| Methodology prose or rationale | `docs/` |
| Repeatable method with steps, inputs, and outputs | Skill — see [skill system](skill-system.md) |
| Independent judgment, specialist stance, or isolation | Agent — see [agent system](agent-system.md) |
| This-turn-only instruction | Prompt — see [human-AI interaction](../practices/human-ai-interaction.md) |
| True only inside this repository | This repository's `AGENTS.md`, or a project-named rule outside reserved prefixes |
| Explore, propose, apply, update, sync, or archive | Vendor `opsx-*` / `openspec-*` — see [OpenSpec lifecycle](../lifecycle/openspec-workflow.md) |

A later change that implements a rule must record why the asset is a rule rather than `AGENTS.md`, a skill, an agent, a specification, a documentation page, or a vendor OpenSpec asset, and must record activation mode and copy-validity.

Constraints that are true only in this repository must not be named `sdd-*`. This repository may use project-named rules outside reserved prefixes for dogfood. Those files are not adopted baseline.

## Decision model

Ask in this order. Stop at the first yes.

| Need | Primitive |
|---|---|
| Identity or navigation | `AGENTS.md` |
| A requirement the framework must guarantee | OpenSpec specification (a later rule may *point* at it) |
| Explanation or methodology narrative | `docs/` |
| Repeatable method | Skill |
| Isolated judgment | Agent |
| Named trigger that must not auto-fire | Command (optional, thin) |
| Persistent must / must-not | Rule, if the creation bar also holds |
| This turn only | Prompt |
| Product, domain, or stack convention | Consuming-project asset (not `sdd-*`) |

### Rule vs AGENTS.md

`AGENTS.md` is identity and navigation. A **rule** is an operational constraint that is not the always-on router.

Keep category errors short in `AGENTS.md`. Extract a rule only when the constraint is operational and cannot stay one short line in the router.

### Rule vs skill

A **rule** binds without invocation. A **skill** is an invoked procedure.

Do not put step-by-step methods in rules. Do not put always-on constraints in skills. Skill-local constraints belong in the skill. See [skill system](skill-system.md).

### Rule vs specification

An OpenSpec **specification** is the requirement contract. A **rule** is a runtime reminder that points at that contract.

A rule must not introduce framework behavior that is not already specified. Specify first; remind later.

### Rule vs agent

A **rule** is a constraint the parent already knows. An **agent** is an isolated specialist stance. A persona stuffed into a rule is not a rule. See [agent system](agent-system.md).

### Rule vs command and prompt

A **command** is an optional human-named trigger. Manual `@mention` of a rule is not the framework distribution model; named triggers belong to skills or optional commands.

A **prompt** is session-scoped. If the same constraint would still matter after the chat closes, it does not belong only in a prompt. See [human-AI interaction](../practices/human-ai-interaction.md).

## Activation

Framework-owned rules **default to glob-scoped activation**. Those globs must match paths whose meaning is identical after copy/pin into a consuming project. Framework-owned Cursor asset paths meet that test.

Always-apply is **exceptional**. It is limited to short adoption or namespace invariants that must bind even during product work and cannot remain one short line in `AGENTS.md`. `AGENTS.md` remains the default always-on router.

Description-only activation (“apply intelligently”) is **forbidden** for framework-owned rules. Optional discovery of a procedure belongs to the [skill operating model](skill-system.md).

Manual `@mention` is **not** the framework distribution model for rules.

Do **not** glob framework-owned rules to `openspec/**` or `docs/**`. Those trees do not mean the same thing in this repository and in a consuming project. Methodology authoring lives in `docs/`, OpenSpec specifications, vendor OpenSpec skills, and this repository's dogfood surface — not in adopted globs on product spec or product docs trees.

A later change that implements a rule must record the activation mode and why it was chosen.

## Session binding

Framework-owned rules bind the **parent Cursor Agent**. Glob or always-apply inheritance into specialist subagents is not a framework contract.

Specialists encode constraints by pointing at authoritative `docs/`. Do not copy a framework rule body into an agent file. See [agent system](agent-system.md).

## Quality

A valid SDD rule is concise, operational, limited to one concern, and non-duplicative of `AGENTS.md`, other rules, specifications, or `docs/`. It points at methodology instead of copying it. It does not become a hidden specification, a skill procedure, or an agent persona.

Cursor's own guidance that rules stay short (on the order of fifty lines) is quality orientation, not a numeric requirement. Concision is the bar; a line count is not.

Rules **accumulate** in context. They must not invoke other rules as steps. Overlap is a quality failure, not composition.

## Lifecycle

Creating, changing, or deprecating a framework-owned rule requires an OpenSpec change in this repository. Silent addition, in-place product overwrite, or undocumented deletion is not permitted. Shared classification, publication, adoption, and retirement are defined in [asset lifecycle](asset-lifecycle.md). This page does not own a second copy of that model.

A later change that implements a rule must record:

- why it is a rule rather than `AGENTS.md`, a skill, an agent, a specification, a documentation page, or a vendor OpenSpec asset
- activation mode and why
- copy-validity

Typical orientation (not a mandatory command sequence): explore → propose → apply → sync → archive. See [working agreements](../governance/working-agreements.md).

After archive, adopted copies participate in the existing versioned baseline: they remain framework-owned, are replaced on update, and must not be customized in place. See [adoption](adoption.md).

## File contract

When a later change creates a framework-owned rule:

- Path: `.cursor/rules/sdd-<concern>.mdc` in the **project** Cursor tree.
- Not distributed as a user-level rule (`~/.cursor/rules/`).
- Not homed in Cursor team-dashboard rules or nested `RULE.md` files in content trees as the framework location.
- Frontmatter records `description` and the chosen activation (`globs`, or exceptional `alwaysApply`).
- Body encodes the constraint and pointers to authoritative methodology. Do not copy a methodology page into the rule file.
- Pointers must remain valid after methodology lands at `docs/sdd-framework/` in a consuming project. Do not assume the rule only ever runs inside this repository.

This page does not create those files.

## Naming and project coexistence

Framework rules use `sdd-<concern>` (one operational topic). That contrasts with skill `sdd-<procedure>` (a verb or task phrase) and agent `sdd-<role>` (a noun-role). Do not use `sdd-rule-*`. Do not use procedure-verb or specialist-role names for rules.

Consuming-project rules use names outside `opsx-*`, `openspec-*`, and `sdd-*`. They must not overwrite framework `sdd-*` rules in place. Domain, product, or stack rules stay in the consuming project. Promotion into the framework happens through this repository's OpenSpec lifecycle.

This operating model does not define a catalog of consuming-project rules. A mandatory product prefix is not required. See [Cursor integration](cursor-integration.md) for reserved prefixes and [adoption](adoption.md) for how projects consume the baseline.

## Adoption

`.cursor/rules/sdd-*` is already in the published baseline inventory when those files exist. This operating model does not change that inventory.

Copied `sdd-*` rules remain **framework-owned**. A consuming project receives them through versioned copy/pin, replaces them on update, and must not fork them in place. Project-named rules sit beside them under other names.

Every `sdd-*` rule must remain correct after that copy. Dogfood that is only true here does not use an `sdd-*` name.

## Catalog status

This operating model does not require any `sdd-*` rule file or `.cursor/rules/` directory to exist. Empty stubs are not a catalog. The first framework-owned rules are a later OpenSpec change.

The Cursor constitution uses `sdd-spec-authoring` as a **non-normative** naming example of how `sdd-<concern>` might look. It is not an asset to create in this change, not a glob design, and not a catalog entry. This page does not add further rule names.
