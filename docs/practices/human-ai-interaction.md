# Human-AI interaction

This document is the authoritative **practice** for how humans communicate intent, context, constraints, and expected outcomes to AI-assisted development workflows.

It is not an architecture layer. The four-layer model in [architecture overview](../architecture/overview.md) is unchanged. This page does not replace [Cursor integration](../architecture/cursor-integration.md), [agent system](../architecture/agent-system.md), [skill system](../architecture/skill-system.md), or [OpenSpec lifecycle](../lifecycle/openspec-workflow.md). It points at those pages instead of copying them.

This page does not create prompt files, a prompt catalog, templates, or `sdd-*` Cursor assets. Absence of those files is valid.

## Identity

A prompt is a **session-scoped instruction**. It carries human intent and expected-output guidance for the current turn or handoff.

It is **not**:

- a requirement
- durable knowledge
- methodology storage
- a specification
- a skill, rule, or agent
- `AGENTS.md`
- a replacement for OpenSpec

If a sentence would still matter after the chat is closed, it does not belong only in a prompt. Record it in the artifact that already owns that kind of truth.

| Artifact | Role | Prompt relationship |
|---|---|---|
| Prompt | Session instruction | Initiates this turn |
| OpenSpec specification | Requirement contract | The prompt must not replace it |
| `docs/` | Durable methodology or explanation | Point at it; do not paste it |
| `AGENTS.md` | Routing contract | Cursor already has it |
| Rule | Persistent operational constraint | Do not reprint in the prompt |
| Skill | Reusable procedure | Invoke it; do not restate the playbook |
| Agent | Isolated specialist | A repeated isolated stance is a later agent, not a prompt header |

Primitive definitions live in [Cursor integration](../architecture/cursor-integration.md). Agent and skill operating models live on their own pages. This practice uses those meanings; it does not redefine them.

## Intent flow

The prompt initiates work. The specification defines the contract. Implementation follows the approved contract. Chat history is not a specification.

Primary path for new work:

```
Human intent
    → prompt
    → OpenSpec artifacts
    → implementation
    → validation
```

That path is a typical orientation, not a mandatory sequence. An exploration prompt may produce no durable artifacts. An implementation prompt must not introduce requirements that are not in the approved change.

```
Human intent
        │
        ├─ optional external planning assistant
        │     (analysis, alternatives, execution brief)
        │     brief = still a prompt, not a stored artifact
        ▼
   session prompt
        │
        ├─ explore        → understanding (may create nothing durable)
        ├─ propose        → contract (proposal, specs, design, tasks)
        ├─ apply          → implementation of that contract
        ├─ review         → findings against the contract
        ├─ debug          → evidence; new requirements go to propose or update
        └─ documentation  → docs that match specs, not chat history
```

Asking for repository implementation with no approved OpenSpec change is incorrect. Send that work to `/opsx-propose` or `/opsx-update`. See [OpenSpec lifecycle](../lifecycle/openspec-workflow.md) and [working agreements](../governance/working-agreements.md).

Behavior that would still matter after the conversation, and that is not already specified, must be recorded as an OpenSpec requirement or design decision. Leaving it only in the prompt or chat is incorrect.

## Conceptual stages

These names describe kinds of prompting. They are not a catalog of templates to implement.

| Stage | Job | Durable output |
|---|---|---|
| **Exploration** | Clarify the problem, options, and non-goals | Understanding; maybe a later change |
| **Specification** | Turn intent into proposal, specs, design, and tasks | OpenSpec artifacts |
| **Implementation** | Execute an approved change | Code or docs; checked-off tasks |
| **Review** | Judge work against the contract | Findings |
| **Debugging** | Explain a failure with evidence | A fix inside the open change, or a new change if requirements moved |
| **Documentation** | Make `docs/` match the specs | Methodology or product docs |

Lifecycle commands that already encode the procedure (`update`, `sync`, `archive`) need a thin prompt: name the change and answer what the command asks. They are not extra template types.

Prompt size is inverse to durable artifacts already in the repository. Explore is often rich. Apply against an approved change is thin.

## Adaptive structure

Recommended sections: **objective**, **scope**, **context**, **constraints**, **non-goals**, **expected output**, **validation expectations**.

These are vocabulary, not a mandatory template. Include a section only when the agent cannot already get that information from `AGENTS.md`, `docs/`, specifications, or the `/opsx-*` command being used.

| Section | External planning assistant | Cursor |
|---|---|---|
| Objective | Include | Include, or let the command imply it |
| Scope / non-goals | Include for new work | Include unless the named change already bounds them |
| Expected output | Include | Often implied by `/opsx-*` |
| Context | Short brief plus pointers; never a docs dump | Paths and change names |
| Constraints | What the assistant cannot know | This-turn only |
| Validation expectations | When the turn is a review | Point at specs or tasks |

Role is not a core section. In Cursor it duplicates `AGENTS.md`. A repeated isolated stance belongs in a later agent change, not in every prompt header.

Validation expectations refer to existing specifications or tasks. They must not add acceptance criteria that are not in OpenSpec.

## Context management

Prompts reference standing knowledge. They do not copy it.

Do not paste `AGENTS.md`, documentation chapters, or specification bodies into prompts as the normal practice. Name the path or capability instead.

If the same paragraph appears in every prompt, it is prompt-only knowledge. Move it to `docs/`, a specification, a rule, a skill, or an agent, then stop pasting it.

Temporary context belongs in the prompt: this change's goal, this failure, "do not touch X this turn." Permanent knowledge belongs in the artifact that already owns it.

## Planning assistant, Cursor, and OpenSpec

This practice does not add a fifth architecture layer and does not define an AI integration, ChatGPT product integration, Cursor plugin, MCP, hook, or orchestration runtime.

**External planning assistant** (ChatGPT is an example, not an architecture layer): architecture discussion, analysis, alternatives, and generation of execution briefs. It does not inspect the repository. Do not treat its output as if it had read the project files.

**Cursor**: repository inspection, OpenSpec execution, code and documentation changes, and validation.

**OpenSpec**: requirements, design decisions, and lifecycle artifacts.

An **execution brief** produced by a planning assistant is a disposable Cursor-oriented prompt. It is not a stored artifact type, a template catalog entry, or a specification. If the conclusion matters, Cursor writes it into OpenSpec.

Do not ask a planning assistant to implement a change. Do not ask Cursor to skip OpenSpec because the prompt was thorough.

## Quality

A good prompt has one objective matched to one lifecycle stage, a bound on scope, a named expected output (or a command that already defines it), and this-turn constraints only. It respects existing architecture and points at standing knowledge instead of duplicating it.

A bad prompt mixes explore, implement, and review in one turn; asks for implementation without a specification; hides requirements in narrative; or treats chat history as the spec.

## Storage and reuse

Prompts are not framework assets. Do not create prompt folders, prompt catalogs, or prompt libraries in this repository.

Repeated prompt patterns promote using the cheapest fitting primitive already specified in [Cursor integration](../architecture/cursor-integration.md):

```
ad hoc prompt → repeated pattern → this practice (docs) → later rule, skill, or agent
```

Saving a prompt file is not the reuse model. This page does not create those Cursor files. Conceptual stages above are not templates to implement.
