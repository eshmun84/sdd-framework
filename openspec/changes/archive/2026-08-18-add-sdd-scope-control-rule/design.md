## Context

See `proposal.md` for why. Rule-system architecture already defines identity, creation bar, activation policy, file contract, and copy-validity; this change follows that model and does not reopen it. Adoption already lists `.cursor/rules/sdd-*` as copyable. Spec First already travels as always-apply and is the existence gate, not the Apply-time bound. Git traceability already travels as always-apply and is attribution, not the bound. `sdd-workflow-architecture` already says Apply implements only an approved change and that contract drift goes to update or a new change; it does not yet make the bound first-class (contract artifacts, no new tasks, no unsolicited improvements, obligated mechanical edits stay in). Framework-owned rule source already lives under `assets/cursor/rules/`; this repository does not install published `sdd-*` files into its own `.cursor/`.

The remaining design work is where the Apply-scope methodology lives, how one `.mdc` file reminds it after copy/pin, and how the constraint stays separate from Apply procedure.

## Goals / Non-Goals

**Goals:**
- Place Apply-time scope control inside the existing workflow page, not a new layer or page.
- Choose activation that binds when the parent implements, without copy-unsafe globs.
- Keep the rule body to the operational must-not plus copy-valid pointers.
- Keep OpenSpec as the requirement source of truth and vendor `/opsx-*` as the lifecycle surface.
- Keep the file true in this repository and in a consuming project.

**Non-Goals:**
- Exact sentence-by-sentence wording of the `.mdc` or the workflow section (Apply writes those against the specs).
- Editing `AGENTS.md`, `README.md`, `sdd-spec-first.mdc`, `sdd-git-traceability.mdc`, or archived architecture pages other than `docs/architecture/workflow-system.md`.
- Path-mapping, installer behavior, a second documentation root, a scope-analysis skill, or a scope-reviewer agent.

## Decisions

### Decision 1: Methodology is a workflow section, not a new page or layer

**Choice:** Apply adds an Apply-time scope control section to `docs/architecture/workflow-system.md`, after **Incomplete, rejected, and evolving work**. No `docs/architecture/scope-*.md`, no `docs/practices/scope-*.md`, no fifth architecture layer. The existing contract-drift bullet stays; the new section makes the bound first-class rather than only a recovery path. Overview, documentation index, and `AGENTS.md` are not edited. Catalog status on that page is not rewritten to require this file.

**Why:** Apply-scope is a collaboration bound on an approved change. A new page would invent a home the documentation tree does not require. Putting the contract only in the rule would make the rule a hidden specification. Reopening catalog status would claim the original workflow architecture change required this asset.

**Alternatives considered:**
- New architecture page: extra layer-shaped surface; documentation-architecture would need reopening.
- Practices page sibling of human-AI: splits the Apply bound away from the collaboration model.
- Fold only into the existing contract-drift bullet: too narrow; drift is missing needed behavior, not gold-plating or new tasks.
- Rule-only, no docs: forbidden hidden spec.
- Extend human-AI instead: that page owns prompt identity; the bound is a workflow stage constraint.

### Decision 2: Always-apply is the activation mode

**Choice:** Frontmatter uses exceptional `alwaysApply: true`. No `globs`. `description` is present for humans and for Cursor metadata; it is not the activation mechanism.

**Why:** The failure happens when the parent implements, including product work outside `.cursor/**/sdd-*` and including implementation that never invokes `/opsx-apply`. Default glob-scoped activation has no copy-safe path for that moment. `openspec/**` and `docs/**` are forbidden globs. Description-only activation is forbidden. `@mention` is not the distribution model. A skill would bind only when invoked; the failure class is not invoking it, or invoking Apply and then expanding.

This is a short **adoption invariant**: after copy/pin, implementation against the host repository's OpenSpec workspace must stay inside the approved change. The body stays short so a third always-apply rule is not a dumped Apply handbook. Spec First and Git traceability remain distinct concerns; this file does not invoke them.

**Alternatives considered:**
- Glob `.cursor/**/sdd-*`: copy-safe, misses product implementation.
- Glob `openspec/**` or `docs/**`: forbidden by rule-system architecture.
- Leave the line only in the consuming project's `AGENTS.md`: cheaper in length, but this change does not write that file and does not reopen adoption Configure.
- Skill instead of rule: procedure-shaped; does not bind without invocation; would wrap `/opsx-apply`.
- Description-only: forbidden; persistence would be probabilistic.

### Decision 3: Filename is `sdd-scope-control.mdc`

**Choice:** Source path `assets/cursor/rules/sdd-scope-control.mdc`. Installed path `.cursor/rules/sdd-scope-control.mdc`. Concern name `scope-control`, not `sdd-rule-*`, not a procedure verb (`analyze-scope`, `apply`), not a specialist role (`scope-reviewer`).

**Why:** Rule-system naming is `sdd-<concern>`. Scope control names the constraint. `apply` collides with the vendor stage. `analyze-scope` is a skill-shaped name this change rejects. `scope-reviewer` is an agent-shaped name this change rejects.

**Alternatives considered:**
- `sdd-apply.mdc`: wraps the vendor stage by name.
- `sdd-analyze-scope.mdc`: procedure-verb; collides with a future skill.
- `sdd-scope-reviewer.mdc`: specialist-role; collides with a future agent.
- `sdd-scope-control-rule.mdc`: redundant `rule` suffix; collides with forbidden `sdd-rule-*`.

### Decision 4: Body is the must-not plus dual-root pointers

**Choice:** The file states, in operational language:

1. Implementation of an approved OpenSpec change in **this** repository's OpenSpec workspace must stay inside that change's proposal, specifications, design when present, tasks, and non-goals.
2. Do not add requirements that are not in the approved change. Do not add new tasks during Apply.
3. Do not perform unsolicited improvements the approved contract does not oblige. Mechanical edits the contract obliges remain allowed. Checking off existing tasks remains Apply.
4. Work that would leave that bound is recorded through the existing OpenSpec change lifecycle, not applied from the implementation prompt.

Then it points at existing methodology by **page title** and names both documentation roots: `docs/` in this repository, `docs/sdd-framework/` after copy/pin. It does not paste those pages. It does not hardcode a single path that is valid in only one universe. Scope means the change's contract artifacts, not a file allowlist.

**Why:** Quality bar is constraint plus pointer. A single hard-coded `docs/architecture/workflow-system.md` breaks after adoption. Dual-root wording stays true in both places. If OpenSpec is not initialized yet, the prompt still does not authorize expanding implementation beyond an approved change.

**Alternatives considered:**
- Paste the workflow section into the rule: documentation dump; hidden spec.
- Pointer only to `docs/...`: false after copy/pin.
- Pointer only to `docs/sdd-framework/...`: false in this repository.
- Encode a path allowlist: imposes a filesystem fence this change forbids.
- Require an installer to rewrite paths: out of scope.

### Decision 5: Constraint and Apply procedure stay split

**Choice:** The rule and the workflow section encode the bound, no new requirements or tasks during Apply, no unsolicited improvements, and obligated mechanical edits. They do not encode how to select a change, read artifacts, loop tasks, or invoke `/opsx-apply`. Vendor `/opsx-apply` remains the procedure. A later skill may own extra procedure; this change does not create it. A later agent may judge scope creep in Review; this change does not create it.

**Why:** A rule that teaches how to apply is a skill in disguise and would wrap vendor OpenSpec. Keeping procedure out is what makes always-apply tolerable beside Spec First and Git traceability.

**Alternatives considered:**
- Include a minimal “read proposal, then tasks” recipe: procedure creep; hidden Apply skill.
- Create `sdd-analyze-scope` in the same change: pack of primitives; out of scope.
- Point the rule at vendor apply as a step to run: wraps `/opsx-apply`.

### Decision 6: Layer boundaries stay as already specified

**Choice:**

| Layer | Role for this file |
|---|---|
| OpenSpec | Source of truth for the approved change that bounds implementation in this project's workspace |
| Cursor | Loads `.cursor/rules/sdd-scope-control.mdc` and binds the parent agent |
| SDD Framework | Owns the source file and the workflow methodology; copied copies remain framework-owned |
| Consuming project | Receives the file through copy/pin; does not fork it; product specs stay in **that** repository |

This repository's `AGENTS.md` is unchanged. Spec First and Git traceability are unchanged. Do not invoke other rules from this file. The workflow page may mention that a copied rule reminds the parent of this contract; it must not claim the collaboration model is a workflow engine or that the original architecture change required this file.

**Alternatives considered:**
- Edit `AGENTS.md` to add a scope line: user-out-of-scope; mixes router work into an asset change.
- Invoke `sdd-spec-first` from this rule: rules must not compose as steps.
- Add a namespace, skill, or agent file in the same change: catalog/pack; forbidden.

## Risks / Trade-offs

- **[Risk] Third always-apply rule burns context on every product turn** → Mitigation: keep the body to the four operational clauses plus short pointers; one concern only; no Apply handbook.
- **[Risk] Reading always-apply as permission to dump Apply procedure later** → Mitigation: Decision 2 and Decision 5 limit the exception to this short adoption invariant; later procedure stays a skill if justified and must not wrap `/opsx-apply`.
- **[Risk] Rule restates Spec First and the two concerns blur** → Mitigation: this file does not mention implementation-without-a-change; it talks about extent once a change is approved. Spec First stays the existence gate.
- **[Risk] “Unsolicited improvements” is too vague to test** → Mitigation: specs split obligated mechanical edits (in) from adjacent work the contract does not oblige (out); the rule restates that split and does not invent a file fence.
- **[Risk] Contributors encode a path allowlist while drafting the `.mdc`** → Mitigation: specs forbid file allowlists; tasks validate no path inventory, CODEOWNERS, or backlog language.
- **[Risk] Dogfood wording (“this is not a product”) leaks in** → Mitigation: spec forbids framework-repo-only identity; review checks copy-validity.
- **[Trade-off] Dual-root pointer vs a single path** → Two roots in one sentence is slightly longer; it is the only copy-valid option without an installer.
- **[Trade-off] Not forbidding all refactors** → Avoids blocking mechanical edits the contract obliges; gold-plating remains out.

## Migration Plan

1. Apply updates `docs/architecture/workflow-system.md` with the Apply-scope section and creates `assets/cursor/rules/sdd-scope-control.mdc` only. No vendor edits. No other `sdd-*` files. No `AGENTS.md` edit. No published copy under this repository's `.cursor/`.
2. Human review validates the page and the file against this change (type, activation, copy-validity, no hidden spec, no docs dump, no OpenSpec wrapper, no Apply procedure).
3. Archive makes `sdd-scope-control` a main spec and merges the workflow delta. The `.mdc` becomes eligible for the published subset already defined by adoption.
4. Consuming projects that later copy/pin receive the file under project-root `.cursor/rules/` and replace it on baseline update. They do not customize it in place.

Rollback is deleting the `.mdc` and reverting the workflow section through a new OpenSpec change (or reverting this change if it is not yet archived). Silent deletion after publication is not the path.

## Open Questions

None that affect specs, activation, or tasks.
