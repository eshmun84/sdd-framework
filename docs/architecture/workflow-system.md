# Workflow system

This document is the authoritative **workflow operating model** for the SDD Framework. It defines how humans, optional planning assistants, Cursor, OpenSpec, and implementation work collaborate through one change — from intent to archived contract.

It does not replace [architecture overview](overview.md) (four-layer model), [Cursor integration](cursor-integration.md) (what a rule, skill, command, or agent *is*), [agent system](agent-system.md), [skill system](skill-system.md), [rule system](rule-system.md), [asset lifecycle](asset-lifecycle.md) (how Cursor assets evolve), [adoption](adoption.md), [OpenSpec lifecycle](../lifecycle/openspec-workflow.md) (vendor command surface), [human-AI interaction](../practices/human-ai-interaction.md) (how prompts initiate work), or [working agreements](../governance/working-agreements.md) (this-repository governance). Those pages keep their jobs. This page is how they operate together. It is not a fifth architecture layer.

This page does not create `.cursor/` assets, `sdd-*` catalog files, prompt libraries, or automation. Absence of those files is valid. It is not permission to wrap `/opsx-*`.

## Identity

The SDD workflow is a **collaboration operating model** for one change. Humans invoke stages. Cursor executes the named vendor OpenSpec command when that stage runs. OpenSpec holds the durable contract.

It is **not**:

- a fifth architecture layer
- a workflow engine
- an OpenSpec wrapper
- a prompt catalog
- a stored artifact type
- a replacement for vendor `/opsx-*` command behavior

This page does not redefine Cursor primitives, prompting practice, or OpenSpec command semantics. It uses those meanings:

| Home | Role this page does not copy |
|---|---|
| [Architecture overview](overview.md) | Four layers: OpenSpec, Cursor, SDD Framework, consuming projects |
| [Cursor integration](cursor-integration.md) | What `AGENTS.md`, rules, skills, commands, and agents *are* |
| [Human-AI interaction](../practices/human-ai-interaction.md) | Prompt as session instruction; how to write it |
| [OpenSpec lifecycle](../lifecycle/openspec-workflow.md) | Installed `/opsx-*` surface and typical orientation |
| [Adoption](adoption.md) | Copy/pin of a versioned baseline |
| [Working agreements](../governance/working-agreements.md) | How *this* repository applies the model |

Standing assignment of truth:

- **Prompt** = session instruction
- **OpenSpec** = durable requirement contract
- **Git** = history of landed change work (not a specification)
- **Cursor** = execution environment
- **Docs** = methodology explanation
- **Skills / rules / agents** = reusable framework assets when they later exist

## Change lifecycle

Primary stages describe intent and collaboration. They are **not** a mandatory OpenSpec command sequence and **not** a workflow engine. Vendor `/opsx-*` command behavior remains defined by OpenSpec. See [OpenSpec lifecycle](../lifecycle/openspec-workflow.md).

```
 HUMAN INTENT
      │
      │  optional: external planning assistant
      │  (analysis, alternatives, disposable execution brief)
      ▼
┌─────────────┐
│  0. INTAKE  │  no OpenSpec change yet
└──────┬──────┘
       │  Gate: universe and whether this is work
       ▼
┌─────────────┐
│ 1. EXPLORE  │  /opsx-explore     optional if intent is already bounded
└──────┬──────┘
       │  Gate: propose, discard, or keep thinking
       ▼
┌─────────────┐
│ 2. PROPOSE  │  /opsx-propose     contract is born
└──────┬──────┘
       │  Gate: human accepts the change as the contract
       │
       │     ┌──────────────┐
       │     │  UPDATE      │  /opsx-update   loop-back, not a primary stage
       │     └──────────────┘
       ▼
┌─────────────┐
│ 3. APPLY    │  /opsx-apply       implement the approved contract
└──────┬──────┘
       │  Gate: tasks done or explicitly accepted incomplete
       ▼
┌─────────────┐
│ 4. REVIEW   │  no vendor command  judge work against the contract
└──────┬──────┘
       │  Gate: pass, return to apply, or return to update
       │
       │     ┌──────────────┐
       │     │  SYNC        │  /opsx-sync     loop-back, not a primary stage
       │     └──────────────┘
       ▼
┌─────────────┐
│ 5. ARCHIVE  │  /opsx-archive     main specs become durable truth
└──────┬──────┘
       ▼
 MAINTENANCE = a new change, not mutation of the archive
```

Explore may be skipped when the problem, scope, and non-goals are already clear. Skip is not a reason to skip proposal, specifications, or tasks.

### Stage boundaries

| Stage | Begins | Ends | Durable output |
|---|---|---|---|
| **Intake** | Human intent (idea, defect, question, or planning-assistant brief) | Idea discarded, exploration warranted, or work ready to propose | None required |
| **Explore** | The problem is still open | Clear enough to propose, or dropped | Understanding; artifacts only if the human asks to capture thinking |
| **Propose** | A human asks to create a change | Proposal, specifications, tasks, and design when needed exist **and** a human has accepted them as the contract | OpenSpec change artifacts |
| **Apply** | A human asks to implement an **approved** change | Tasks complete, or incompleteness is explicit | Implementation matching the contract (docs and tooling here; product code in a consuming project) |
| **Review** | Implementation is claimed done, or a human asks to judge the work | Findings accepted (pass, return to apply, or return to update) | Findings. Not a second specification |
| **Archive** | A human approves finalizing a completed (or explicitly accepted incomplete) change | Change archived; main specs synced if needed | `openspec/specs/` remains the durable requirement source |

**Update** and **sync** are loop-backs. Update revises planning artifacts of an open change. Sync merges delta specs into main specs without closing the change.

**Maintenance** is not a vendor command. Archived work is frozen. New behavior, silent doc/spec drift, and defects that change requirements are a **new** change. Defects that do not change requirements restore the existing contract through a new change, or a fix inside an still-open change.

Asking for repository implementation with no approved OpenSpec change is incorrect. Send that work to propose or update. Chat history is not a specification.

## Participants

The human is the only gate owner. Cursor may recommend that a stage is ready. Cursor must not treat its own recommendation as approval.

| Participant | Owns | Does not |
|---|---|---|
| **Human** | Intent, universe selection, stage gates, approval, rejection | Treating chat as the contract |
| **External planning assistant** (optional) | Analysis, alternatives, disposable execution briefs | Inspecting the repository, implementing, creating OpenSpec artifacts |
| **Cursor** (parent agent) | Repository inspection, `/opsx-*` execution, edits, local validation | Owning the requirement contract |
| **OpenSpec** | Requirements, design decisions, lifecycle artifacts | Methodology prose, Cursor UX |
| **Implementation** | Work that matches the approved contract | Inventing requirements. In this model, implementation is Cursor applying that change |
| **Docs** | Readable methodology | Replacing specifications |
| **Later `sdd-*` skills, rules, agents** | Reusable execution *inside* a stage, when a later change creates them | Owning the lifecycle, wrapping `/opsx-*`, becoming a workflow engine |

A planning assistant is not required. A human may go straight to `/opsx-explore` or `/opsx-propose` in Cursor. An execution brief remains a disposable prompt. If a conclusion must survive the chat, Cursor writes it into OpenSpec. Prompt practice lives in [human-AI interaction](../practices/human-ai-interaction.md).

CI, other IDEs, and cloud agents are not specified participants.

## Durable versus temporary information

If a sentence would still matter after the conversation ends, it does not belong only in a prompt. Record it in the OpenSpec artifact that already owns that kind of truth.

| Temporary (session) | Durable (change or main specs) |
|---|---|
| Prompt wording and tone | Proposal (why, scope, non-goals) |
| This-turn constraints (“do not touch X this turn”) | Specifications (behavior that must remain true) |
| Discarded alternatives after design records the choice | Design decisions |
| Planning-assistant narrative | Tasks |
| Chat clarifications that did not change the contract | Implementation that matches the contract; main specs after sync or archive |

How to write the session instruction is defined in [human-AI interaction](../practices/human-ai-interaction.md). This page does not restate that practice.

## Git ↔ OpenSpec traceability

Git is the history of change work that has landed in the repository. It is not a fifth architecture layer. OpenSpec remains the durable requirement contract. Git history and commit messages are not specifications.

When Git work is associated with an OpenSpec change in the **current** repository's OpenSpec workspace, that work must be attributable to that change. A reader of the commit must be able to identify the change. Propose, apply, sync, and archive artifacts for a change are change-related work.

A single commit must not contain work that belongs to more than one OpenSpec change. Record that work in separate commits, each attributable to one change.

Not every commit must reference an OpenSpec change. Commits that do not contain change-related work still must not be treated as a specification.

This page does not specify commit-message grammar, Conventional Commits, branching, hooks, Git tooling, or Git procedure (staging, rebase, squash, push, pull request). Attribution is the observable association to the change in this workspace; exact placement in the message is not specified.

## Human approval gates

Human approval is required:

1. Before generated OpenSpec artifacts are treated as **the contract**. Artifact existence alone does not authorize apply.
2. Before implementation proceeds as **approved work**.
3. Before **archive**.

Universe selection is a human decision during intake or propose:

| Work | Universe |
|---|---|
| Framework methodology | This repository's OpenSpec |
| Product behavior | The consuming project's OpenSpec |
| Framework baseline update | [Adoption](adoption.md) replace of copied assets — not a product OpenSpec change here |

Product requirements must not be recorded in this repository's OpenSpec workspace.

## Review

Review is a primary SDD collaboration stage. Its job is to judge implementation against the approved contract.

It is **not** an OpenSpec command. Do not invent `/opsx-review` or `/sdd-review`. Do not create an `sdd-*` command or skill whose purpose is to wrap or replace `/opsx-*`. A later change may encode review as a skill or specialist agent using the cheapest-fitting-primitive tests already specified in [Cursor integration](cursor-integration.md). This operating model does not require those files.

Findings refer to existing specifications or tasks. They must not invent a second acceptance list. If review discovers behavior that should remain true and is not in the approved change, that behavior goes to propose or update. It must not be applied from the review prompt alone.

## Incomplete, rejected, and evolving work

- **Dropped exploration** is valid. No durable artifacts are required. Chat dies with the session.
- **Rejected proposal** must not be applied. The originating prompt must not survive as the specification. File deletion or unused-change mechanics stay defined by OpenSpec.
- **Incomplete apply** must be completed or explicitly accepted as incomplete before archive.
- **Contract drift** during implementation requires `/opsx-update` or a new change. Prefer a new change over expanding an in-flight change past its non-goals.

## Independent OpenSpec universes

The same collaboration stages apply in this repository and in consuming projects that use OpenSpec. The content and the OpenSpec workspace differ.

```
sdd-framework                         consuming project
─────────────                         ─────────────────
OpenSpec: framework requirements      OpenSpec: product requirements
docs/: canonical methodology          docs/sdd-framework/: snapshot
AGENTS.md: this repo's router         AGENTS.md: that product's router
opsx-*: vendor, this workspace        opsx-*: vendor, that workspace
sdd-*: source (when they exist)       sdd-*: copied, still framework-owned
apply: docs and tooling               apply: product code and product docs
```

Consuming projects do not import this repository's OpenSpec specifications as product specs. They do not follow this repository's `AGENTS.md`. They follow this collaboration model once they have adopted the methodology snapshot and obtained OpenSpec locally. How the baseline is copied is defined in [adoption](adoption.md). This page does not define product-specific lifecycles.

Two maintenance loops in a consuming project must not be mixed:

- Product defect or feature → that project's OpenSpec change
- Framework baseline update → adoption replace of copied `sdd-*` and the docs snapshot

A consuming project that has not installed OpenSpec cannot run this change lifecycle. Prompts are not a substitute.

## Catalog status

This operating model does not require any `sdd-*` rule, skill, command, or agent file to exist. It does not introduce a workflow engine, orchestrator runtime, hooks, MCP integration, plugin, prompt library, or automation that runs the lifecycle. Empty stubs are not a catalog.

Humans invoke stages. Cursor executes the named vendor command. Later skills, agents, or rules may operate inside a stage. They must not own explore, propose, apply, update, sync, or archive. Use the vendor `opsx-*` / `openspec-*` surface. How those later files are classified, created, and retired is defined in [asset lifecycle](asset-lifecycle.md).
