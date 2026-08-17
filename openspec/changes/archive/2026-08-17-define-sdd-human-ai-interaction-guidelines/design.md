## Context

See `proposal.md` for why. Cursor component, agent, skill, and adoption constitutions already assign OpenSpec, Cursor, `AGENTS.md`, rules, skills, and agents. None of them define how a human message starts work. `docs/` has architecture, lifecycle, governance, and principles. There is no practices area.

This change writes the human-AI interaction practice. Implementation is documentation and specs. It does not create prompt files or Cursor assets.

## Goals / Non-Goals

**Goals:**
- Give `docs/practices/human-ai-interaction.md` a single, navigable practice that specs can be validated against.
- Keep the four-layer architecture unchanged; add navigation, not a fifth layer.
- Record prompt identity, intent flow, adaptive structure, tool boundaries, and promotion so later catalog or template changes cannot be smuggled in as “just prompting.”

**Non-Goals:**
- Exact sentence-by-sentence wording of the new page (prose is apply work; contracts are in the specs).
- Creating prompt files, `prompts/` directories, templates, or `sdd-*` assets.
- Choosing a vendor chat product as an architecture layer.
- Reopening Cursor, agent, skill, or adoption operating models.

## Decisions

### Decision 1: New practices page, not an architecture or lifecycle page

**Choice:** Authoritative prose lives at `docs/practices/human-ai-interaction.md`. Architecture pages stay constitutions and operating models. The lifecycle page gets a pointer: prompts ignite stages; they are not specs.

**Why:** Prompting is how humans use the system, not what OpenSpec or Cursor *is*. Folding it into `overview.md` or `openspec-workflow.md` would mix practice into those contracts. A `practices/` area leaves room for later methodology pages without stuffing architecture.

**Alternatives considered:**
- `docs/architecture/human-ai-interaction.md`: implies a fifth layer.
- `docs/prompt-engineering.md` at docs root: cheaper today, weaker home if more practices appear.
- Own the topic on the lifecycle page: OpenSpec commands are vendor-owned; prompting is broader (planning assistant included).

### Decision 2: New capability `human-ai-interaction`

**Choice:** Add `human-ai-interaction` for prompt identity, prompt/spec separation, context management, tool boundaries, adaptive structure, and reuse. Extend `documentation-architecture` so the docs tree requires the page. Do not extend `cursor-component-model`, `sdd-agent-architecture`, or `sdd-skill-architecture`.

**Why:** A prompt is not a Cursor primitive. Overloading the constitution would reopen it and invite duplicated SHALLs. Documentation location is a docs-tree concern; prompting behavior is a distinct contract.

**Alternatives considered:**
- Only extend `documentation-architecture`: would require a page without saying what the practice must establish.
- Fold into `cursor-component-model`: treats a session message as a primitive beside skills and agents.

### Decision 3: External planning assistant, not a ChatGPT layer

**Choice:** Specs name **external planning assistant**, **Cursor**, and **OpenSpec**. The practice page MAY use ChatGPT as an example of a planning assistant. No fifth architecture layer. No product integration.

**Why:** Cursor is already the named execution environment. Naming a chat vendor in SHALL language would lock the methodology to one product. The user workflow still matches: plan outside the repo, execute in Cursor.

**Alternatives considered:**
- Name ChatGPT in the spec: matches current habit, ages into an integration contract.
- Omit planning assistants entirely: leaves the ChatGPT→Cursor handoff undefined, which is the failure mode this change exists to prevent.

### Decision 4: Execution brief stays a prompt

**Choice:** A planning assistant may produce a Cursor-oriented instruction. That instruction is still a disposable prompt. Do not specify a brief form, filename, or repository path.

**Why:** A stored brief format is a template catalog under another name. Durable outcomes already land in OpenSpec artifacts.

**Alternatives considered:**
- Check in briefs under the change directory: duplicates proposal/specs and rots.
- Specify a mandatory brief schema: out of scope (templates).

### Decision 5: Intent flow is typical orientation

**Choice:** Document human intent → prompt → OpenSpec artifacts → implementation → validation as the primary path for new work. State that explore may produce nothing durable, and that apply must not smuggle new requirements.

**Why:** Matches OpenSpec’s “typical orientation, not a mandatory sequence.” Making every prompt enter propose would forbid legitimate debug/review turns.

**Alternatives considered:**
- Mandatory full sequence for every prompt: fights `/opsx-explore` and review work.
- Prompt-only implementation when the prompt is “complete”: the defect this change is written to stop.

### Decision 6: Adaptive structure; Role is not a core section

**Choice:** Recommended sections are objective, scope, context, constraints, non-goals, expected output, and validation expectations. None are universally mandatory. Include a section only when the agent cannot already get it from `AGENTS.md`, docs, specs, or the `/opsx-*` command. Role is omitted from the core list: in Cursor it duplicates `AGENTS.md`; a repeated isolated stance is a future agent, not a prompt header.

**Why:** A fixed eight-block template produces huge Cursor prompts and fights non-duplication. Validation expectations must point at specs/tasks, not invent a second acceptance list.

**Alternatives considered:**
- Mandatory template for all prompts: uniform, noisy, anti-`AGENTS.md`.
- Keep Role as a recommended section: teaches people to restyle the agent every turn.

### Decision 7: Overview one-liner; no fifth layer

**Choice:** `docs/architecture/overview.md` stays the four-layer summary and gains a single pointer to the practice page. Do not add a row or box for ChatGPT, prompts, or “human-AI interaction” as a layer. Index, `AGENTS.md`, `README.md`, and the lifecycle page also get thin links.

**Why:** Discovery should match other methodology pages. Expanding the layer table would contradict Decision 3.

**Alternatives considered:**
- No overview pointer: keeps overview pure; agents routing from architecture miss the practice.
- Add a fifth layer: reopens the architecture the user forbade reopening.

### Decision 8: Promotion uses existing primitives; this apply creates no assets

**Choice:** Repeated prompt patterns promote to docs, then rules, then skills, then agents, using the cheapest-fitting-primitive tests already specified. Apply writes the practice page and navigation only. No `.cursor/` files, no `prompts/`, no stubs.

**Why:** Saving prompts as files would create a hidden spec system. Creating `sdd-*` assets now would violate the catalog-status decisions already archived.

**Alternatives considered:**
- Ship example prompts as teaching assets: becomes a library immediately.
- Create a `sdd-prompt-*` skill: wraps methodology into Cursor before the practice exists as docs.

## Risks / Trade-offs

- [Teams still paste docs into ChatGPT because it cannot read the repo] → Mitigation: require a short brief plus pointers, not a dump; forbid treating the assistant as if it inspected files.
- [“Execution brief” is later mistaken for an artifact type] → Mitigation: spec states the brief is a disposable prompt; no path or schema.
- [Practice page restates agent/skill constitutions] → Mitigation: distinguish and link; do not copy operating models.
- [Consuming projects invent prompt folders anyway] → Mitigation: methodology snapshot carries the SHALL NOT; framework does not ship a `prompts/` example to copy.

## Migration Plan

Documentation-only. After archive, consuming projects receive the page on the next methodology snapshot into `docs/sdd-framework/`. No runtime, installer, or Cursor-asset migration. Rollback is reverting the docs and spec change.
