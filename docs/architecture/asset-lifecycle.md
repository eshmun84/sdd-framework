# Asset lifecycle

This document is the authoritative **asset lifecycle operating model** for the SDD Framework. It defines what a framework-owned asset is, how a need is classified before a file exists, and how those assets are created, validated, published, adopted, maintained, deprecated, and retired.

It does not replace [architecture overview](overview.md) (four-layer model), [Cursor integration](cursor-integration.md) (what a rule, skill, command, or agent *is*), [agent system](agent-system.md), [skill system](skill-system.md), [rule system](rule-system.md), [workflow system](workflow-system.md) (change collaboration), [adoption](adoption.md) (copy/pin distribution), [OpenSpec lifecycle](../lifecycle/openspec-workflow.md), or [human-AI interaction](../practices/human-ai-interaction.md) (prompt promotion). Those pages keep their jobs. This page is how framework-owned Cursor files evolve across them. It is not a fifth architecture layer.

This page does not create Cursor assets, an `sdd-*` catalog, a planned-name inventory, templates, examples, an installer, a manifest, or release automation. Absence of `sdd-*` files is a valid complete published state. It is not permission to wrap `/opsx-*`.

## Identity

An SDD Framework asset is a **framework-owned Cursor reusable primitive** in the `sdd-*` namespace.

Supported categories:

| Category | Source path (this repository) | Installed path (after copy/pin) | Type model |
|---|---|---|---|
| Rule | `assets/cursor/rules/sdd-*` | `.cursor/rules/sdd-*` | [Rule system](rule-system.md) |
| Skill | `assets/cursor/skills/sdd-*` | `.cursor/skills/sdd-*` | [Skill system](skill-system.md) |
| Agent | `assets/cursor/agents/sdd-*` | `.cursor/agents/sdd-*` | [Agent system](agent-system.md) |
| Optional command | `assets/cursor/commands/sdd-*` | `.cursor/commands/sdd-*` | [Cursor integration](cursor-integration.md) (thin trigger) |

Source files are authored under `assets/cursor/`. Cursor loads installed files from project-root `.cursor/` after copy/pin. This repository does not install published `sdd-*` files into its own `.cursor/` tree. A primitive directory under `assets/cursor/` exists only when at least one published file of that primitive exists.

A command is a **dependent asset**. It exists only as an optional thin trigger for a canonical skill, shares that skill's `sdd-*` name, and is never proposed alone. Deprecating or retiring the skill includes the command. Command meaning stays in the constitution; this page does not reopen it.

These are **not** framework assets:

| Thing | Home instead |
|---|---|
| Methodology prose | `docs/` |
| Requirement contract | `openspec/specs/` |
| Routing contract | `AGENTS.md` |
| Session instruction | Prompt — [human-AI interaction](../practices/human-ai-interaction.md) |
| Vendor OpenSpec Cursor files | `opsx-*` / `openspec-*` |
| Product, domain, or stack extensions | Consuming-project Cursor names outside reserved prefixes |
| This repository's dogfood-only non-`sdd-*` rules | This `AGENTS.md` or a project-named rule here |
| Methodology snapshot at `docs/sdd-framework/` | [Adoption](adoption.md) payload, not a Cursor primitive |

The asset lifecycle is **not**:

- a fifth architecture layer
- a workflow engine
- an asset-management runtime
- a catalog
- a replacement for OpenSpec

It classifies needs into the homes above. It governs only the Cursor files that survive classification.

## Classification

Asset creation starts with classification. Product, domain, or stack work exits to the consuming project before this list. Remaining needs are asked in this order. Stop at the first home that fits. The cheapest valid home wins.

1. Session-only prompt
2. Methodology documentation
3. Specification requirement
4. Repository identity or navigation (`AGENTS.md`)
5. Vendor OpenSpec lifecycle (explore, propose, apply, update, sync, archive)
6. Rule
7. Skill
8. Agent
9. Optional command (only with a skill)

When the need is behavior the framework must guarantee, it is an OpenSpec specification even if it could also be written as prose. A Cursor asset must not replace that specification. Specify first; execute or remind later.

Type-specific tests stay on the existing pages. This page does not reprint them.

| If the need is… | Use |
|---|---|
| Persistent operational constraint | [Rule system](rule-system.md) |
| Repeatable procedure | [Skill system](skill-system.md) |
| Isolated specialist stance | [Agent system](agent-system.md) |
| Named trigger that must not auto-fire | Optional command, constitution in [Cursor integration](cursor-integration.md) |

Do not create an `sdd-*` file when a cheaper home already owns the behavior. Do not create a framework asset whose purpose is explore, propose, apply, update, sync, or archive. Use the vendor `opsx-*` / `openspec-*` surface.

Classification may exit with no asset. That outcome is valid.

## Creation criteria

A framework-owned asset is justified only when **all** of these are true:

1. **Reusable methodology** with framework-wide applicability (not product, domain, or stack).
2. **Copy-validity** — still true after copy/pin, including pointers that land at `docs/sdd-framework/` in a consuming project.
3. **Stable behavior** — no longer being explored.
4. **Evidence of repetition** — more than one observed occurrence, recorded in the OpenSpec proposal (prompt pattern, dogfood miss, or project extension).
5. **Correct primitive** — the classified type passes its operating-model tests.
6. **OpenSpec approval** — a human has accepted the change as the contract.

A hypothetical or one-time need is not evidence. Empty stubs are not a catalog. Absence of `sdd-*` files remains valid.

Asking to add an `sdd-*` file with no approved OpenSpec change is incorrect. Send that work to propose. Chat history is not permission to create the asset.

One change may create a skill and its optional command. It must not create a catalog.

## Lifecycle stages

These stages are **operating concepts**. They are not a mandatory command sequence, not new Cursor commands, and not a workflow engine. Mutation uses the existing OpenSpec change lifecycle. Collaboration stages stay on [workflow system](workflow-system.md). Distribution stays on [adoption](adoption.md).

Do not create `/sdd-publish`, `/sdd-validate`, `/sdd-retire`, or any `sdd-*` command or skill whose purpose is to own this lifecycle.

```
 NEED
   │
   ▼
 CLASSIFY      may exit: not an asset
   │
   ▼
 PROPOSE       workflow: propose
   │
   ▼
 IMPLEMENT     workflow: apply
   │
   ▼
 VALIDATE      workflow: review
   │
   ▼
 PUBLISH       eligible after archive
   │
   ▼
 ADOPT         adoption: copy/pin
   │
   ▼
 MAINTAIN      new OpenSpec change; projects update the subset
   │
   ▼
 DEPRECATE     still copied; marked; do not use for new work
   │
   ▼
 RETIRE        removed from the published subset
```

### Stage boundaries

| Stage | Begins | Ends | Durable output |
|---|---|---|---|
| **Need** | An observed pattern | Classified or discarded | None required |
| **Classify** | The need is framework-shaped | A home is chosen, or the need is dropped | Understanding; maybe a docs-only or spec-only change |
| **Propose** | A human asks to create a change for an asset | Human-accepted OpenSpec artifacts that record type justification and repetition evidence | OpenSpec change artifacts |
| **Implement** | A human asks to apply an **approved** change | The file exists in this repository matching the contract | `assets/cursor/**/sdd-*` for that change |
| **Validate** | Implementation is claimed done | Review findings accepted | Findings against the contract |
| **Publish** | The creating change is archived | The asset sits in a published-inventory path | Eligibility for copy/pin |
| **Adopt** | A project takes or updates a baseline | Copied files present; pin recorded | Project-side copy; still framework-owned |
| **Maintain** | Behavior must change | A new change is archived | Same name, or a planned rename |
| **Deprecate** | Removal or breaking replacement is planned | The file is marked and remains available | OpenSpec change + notice in docs and the file |
| **Retire** | The deprecation transition is complete | The file is gone from the published subset | Removal change archived |

**Publish is not archive.** Archive makes `openspec/specs/` durable. Publish means the archived asset in `assets/cursor/` is eligible for the published subset. Git tags remain the baseline identifier in [adoption](adoption.md). This operating model does not require tags, releases, or publication tooling to exist.

Observation alone does not require an OpenSpec change. Implement begins only after a human has accepted the contract. Do not write the Cursor file from classification or chat history.

## Ownership

| Participant | Owns | Does not |
|---|---|---|
| **Human** | Classification, creation, adoption, and retirement decisions | Treating chat as permission to add an asset |
| **This repository** | Source `sdd-*` files, framework OpenSpec changes, methodology evolution | Product extensions |
| **OpenSpec** | Mutation history and requirements | Methodology prose, Cursor UX |
| **Cursor** | Execution of assets | Lifecycle transitions |
| **Consuming project** | Project-named extensions outside reserved prefixes; whether to adopt or update | In-place edits of `sdd-*` |

Copied `sdd-*` files remain **framework-owned**. Reusable improvements return through this repository's OpenSpec lifecycle. A consuming project must not fork them in place. A project-named extension or waiting for a framework update is the local path; editing copied `sdd-*` is not.

## Validation

Validation is the existing [workflow](workflow-system.md) **review** stage. It judges the implementation against the approved OpenSpec change. It is not a new command.

Review checks:

- type justification recorded in the change
- file-contract fit for that primitive
- cheapest-primitive fit
- copy-validity after adoption
- no hidden specification (behavior was specified first)
- no documentation dump (points at `docs/`, does not copy the page)
- no OpenSpec wrapper

Findings refer to the existing contract. They must not invent a second acceptance list. An asset that is true only inside this repository must not be published as `sdd-*`.

## Versioning

Assets ride the **framework baseline**. The primary identifier is a git tag, as already specified by [adoption](adoption.md). There is no per-asset version, version catalog, manifest, sync tool, or release automation in this model.

| Change | Class | Project sees it |
|---|---|---|
| Wording, pointers, copy-validity fix | Compatible | Next whole-subset update |
| New `sdd-*` file | Additive | Appears on next update |
| Meaning change, rename, or removal | Breaking | Deprecate, then retire, then drop on a later update |

Partial updates that keep some copied `sdd-*` files while replacing others are not the model. Update replaces the framework-owned subset as a unit.

## Adoption

After publication, consuming projects receive assets through the existing versioned **copy/pin** contract. This page does not restate landing paths, never-transfer inventory, vendor OpenSpec exclusion, or installer deferral. See [adoption](adoption.md).

- Updates replace framework-owned copied assets and the docs snapshot, then the pin.
- Human-reviewed diff. No silent whole-tree overwrite.
- Projects do not fork `sdd-*`.
- No per-asset synchronization mechanism exists.

A useful non-`sdd-*` Cursor file in a consuming project may be **evidence** for proposing a framework asset here. It is not an in-place rename to `sdd-*`. If the behavior is actually product-specific, it stays a project extension.

## Deprecation and retirement

```
 Active ──► Deprecated ──► Retired ──► Absent from the next project update
              still in                  removed from
              published subset          published subset
              marked "do not use"
```

Creating, changing, deprecating, or retiring a framework-owned asset requires an OpenSpec change in this repository. Silent addition, in-place product overwrite, or undocumented deletion is not permitted.

- **Deprecation** marks the asset so new work does not use it. The file remains in the published subset during the transition. Notice lives in the OpenSpec change, in `docs/`, and in the file. This page does not define a release calendar or a numeric waiting period.
- **Retirement** is a later OpenSpec change that removes the asset from the published subset. A consuming project's next baseline update drops the file as part of replacing framework-owned copied assets. Keeping a retired `sdd-*` name after that update would be a fork of a reserved prefix.
- An asset that was **never eligible** for the published subset may be removed by an OpenSpec change without a prior deprecation period. Silent deletion is still forbidden.

## Publication policy

A published framework baseline **may contain zero** framework-owned `sdd-*` Cursor files. Methodology, architecture, and OpenSpec governance are sufficient. Publishing a baseline does not require Cursor assets. Absence of those files is not an incomplete implementation and is not unfinished foundation work.

There is **no planned-name catalog**. Do not create a catalog document, a backlog of `sdd-*` names, or empty stubs so a catalog appears populated. The inventory is the `sdd-*` files that exist under `assets/cursor/` plus the path patterns in [adoption](adoption.md). This repository's `.cursor/` is not the published inventory. Example `sdd-*` names elsewhere in architecture docs are naming illustrations, not creation intent.

Each later `sdd-*` file is its own OpenSpec change that follows this lifecycle (classification, evidence of repetition, human acceptance). One change may create a skill and its optional command. A change must not create a catalog of assets.

This page does not introduce an installer, synchronization tool, manifest, release automation, workflow engine, asset-management runtime, MCP integration, hook, plugin, template catalog, or example assets.

Humans invoke OpenSpec stages. Cursor executes assets when those files exist.
