## Context

See `proposal.md` for why. Spec First is already specified. This repository has no `.cursor/rules/` tree and no `sdd-*` files. Rule-system architecture already defines identity, creation bar, activation policy, file contract, and copy-validity; this change follows that model and does not reopen it. Adoption already lists `.cursor/rules/sdd-*` as copyable. `AGENTS.md` already carries the constraint here and is never transferred.

The remaining design work is how one `.mdc` file reminds that contract at Cursor runtime after copy/pin.

## Goals / Non-Goals

**Goals:**
- Choose activation that binds during product work without copy-unsafe globs.
- Keep the rule body to the operational must-not plus copy-valid pointers.
- Keep OpenSpec as the requirement source of truth and vendor `/opsx-*` as the lifecycle surface.
- Keep the file true in this repository and in a consuming project.

**Non-Goals:**
- Exact sentence-by-sentence wording of the `.mdc` (Apply writes the file against the spec).
- Editing `AGENTS.md`, `README.md`, or archived architecture pages.
- Path-mapping, installer behavior, or a second documentation root in this repository.

## Decisions

### Decision 1: Always-apply is the activation mode

**Choice:** Frontmatter uses exceptional `alwaysApply: true`. No `globs`. `description` is present for humans and for Cursor metadata; it is not the activation mechanism.

**Why:** Spec First must bind when a human asks to implement, including product work outside `.cursor/**/sdd-*`. Default glob-scoped activation has no copy-safe path for that moment. `openspec/**` and `docs/**` are forbidden globs because those trees mean framework specs/docs here and product specs/docs in a consuming project. Source-tree globs would couple the rule to an application stack. Description-only activation is forbidden. `@mention` is not the distribution model.

This is a short **adoption invariant**: the constraint must bind during product work after copy/pin because the framework does not own the consuming project's `AGENTS.md`. The body stays short so always-apply is not a dumped router.

**Alternatives considered:**
- Glob `.cursor/**/sdd-*`: copy-safe, misses the actual failure (implementing product or docs work without a change).
- Glob `openspec/**` or `docs/**`: forbidden by rule-system architecture.
- Leave the line only in the consuming project's `AGENTS.md`: cheaper in length, but this change does not write that file and does not reopen adoption Configure.
- Description-only: forbidden; persistence would be probabilistic.

### Decision 2: Filename is `sdd-spec-first.mdc`

**Choice:** Path `.cursor/rules/sdd-spec-first.mdc`. Concern name `spec-first`, not `sdd-rule-*`, not a procedure verb, not `sdd-spec-authoring`.

**Why:** Rule-system naming is `sdd-<concern>`. `spec-first` names the constraint. `sdd-spec-authoring` remains the constitution's non-normative example and is a spec-authoring playbook shape this change rejects.

**Alternatives considered:**
- `sdd-spec-first-rule.mdc`: the `rule` suffix is redundant and collides with the forbidden `sdd-rule-*` pattern.
- `sdd-spec-authoring.mdc`: example name; implies procedure and `openspec/**` globs.

### Decision 3: Body is the must-not plus dual-root pointers

**Choice:** The file states, in operational language:

1. Do not implement repository work that is not in an approved OpenSpec change in **this** repository's OpenSpec workspace.
2. A prompt and chat history are not the specification.
3. Behavior that would still matter after the conversation and is not specified goes to the existing OpenSpec change lifecycle; it is not applied from the prompt.
4. Implementing an already approved change is allowed.

Then it points at existing methodology by **page title** and names both documentation roots: `docs/` in this repository, `docs/sdd-framework/` after copy/pin. It does not paste those pages. It does not hardcode a single path that is valid in only one universe.

**Why:** Quality bar is constraint plus pointer. A single hard-coded `docs/architecture/workflow-system.md` breaks after adoption. Inventing copy-time path rewrite is installer behavior. Dual-root wording stays true in both places. If OpenSpec is not initialized yet, (1)–(3) remain true: the prompt is still not the spec.

**Alternatives considered:**
- Paste workflow/human-AI text into the rule: documentation dump; hidden spec.
- Pointer only to `docs/...`: false after copy/pin.
- Pointer only to `docs/sdd-framework/...`: false in this repository.
- Require an installer to rewrite paths: out of scope.

### Decision 4: Vendor commands are not in the procedure

**Choice:** The rule names the OpenSpec **change lifecycle** as the place unspecified work must go. It does not list `/opsx-explore` → `/opsx-propose` → `/opsx-apply` as steps, does not say those commands are mandatory in that order, and does not explain how to author artifacts. Explore remaining skippable stays a workflow fact, not a rule body topic.

**Why:** Wrapping vendor OpenSpec is forbidden. Encoding authoring steps would turn the rule into a skill. The vendor surface in a consuming project is obtained locally; this file is not that distribution channel.

**Alternatives considered:**
- "Always run `/opsx-propose` then `/opsx-apply`": wrapper plus false mandatory sequence.
- Teach spec authoring in the rule: different concern; glob trap; skill-shaped.

### Decision 5: Layer boundaries stay as already specified

**Choice:**

| Layer | Role for this file |
|---|---|
| OpenSpec | Source of truth for Spec First behavior; this project's workspace is the contract the rule points at |
| Cursor | Loads `.cursor/rules/sdd-spec-first.mdc` and binds the parent agent |
| SDD Framework | Owns the source file; copied copies remain framework-owned |
| Consuming project | Receives the file through copy/pin; does not fork it; product specs stay in **that** OpenSpec workspace |

This repository's `AGENTS.md` is unchanged. Overlap with its OpenSpec bullet is accepted in **this** repo because the rule is the vehicle that survives adoption. Do not shorten `AGENTS.md` in this change (out of scope). Do not invoke other rules from this file.

**Alternatives considered:**
- Edit `AGENTS.md` to drop the duplicated line: user-out-of-scope; would mix router work into an asset change.
- Add a namespace or review rule in the same change: catalog/pack; forbidden.

## Risks / Trade-offs

- **[Risk] Always-apply burns context on every product turn** → Mitigation: keep the body to the four operational clauses plus short pointers; one concern only.
- **[Risk] Reading always-apply as a general methodology dump** → Mitigation: Decision 1 limits the exception to this short adoption invariant; later rules still default to globs.
- **[Risk] Pointers ignored; agents treat the rule as the spec** → Mitigation: spec requires reminder-not-hidden-spec; Apply wording must say existing specs remain source of truth.
- **[Risk] Contributors add `/opsx-*` steps while drafting the `.mdc`** → Mitigation: Decision 4 and tasks that validate no vendor wrap.
- **[Risk] Dogfood wording (“this is not a product”) leaks in** → Mitigation: spec forbids framework-repo-only identity; review checks copy-validity.
- **[Trade-off] Dual-root pointer vs a single path** → Two roots in one sentence is slightly longer; it is the only copy-valid option without an installer.
- **[Trade-off] Overlap with this `AGENTS.md`** → Temporary duplication inside the framework repo; the copied surface is the rule, not the router.

## Migration Plan

1. Apply creates `.cursor/rules/sdd-spec-first.mdc` only. No vendor edits. No other `sdd-*` files. No `AGENTS.md` edit.
2. Human review validates the file against this change (type, activation, copy-validity, no hidden spec, no docs dump, no OpenSpec wrapper).
3. Archive makes `sdd-spec-first` a main spec. The `.mdc` becomes eligible for the published subset already defined by adoption.
4. Consuming projects that later copy/pin receive the file under project-root `.cursor/rules/` and replace it on baseline update. They do not customize it in place.

Rollback is deleting the `.mdc` through a new OpenSpec change (or reverting this change if it is not yet archived). Silent deletion after publication is not the path.

## Open Questions

None that affect specs, activation, or tasks.
