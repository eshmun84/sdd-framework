## Context

See `proposal.md` for why. Rule-system architecture already defines identity, creation bar, activation policy, file contract, and copy-validity; this change follows that model and does not reopen it. Adoption already lists `.cursor/rules/sdd-*` as copyable. Spec First already travels as an always-apply rule and does not cover Git attribution. `sdd-workflow-architecture` already owns the collaboration model and has no Git ↔ OpenSpec contract. Framework-owned rule source already lives under `assets/cursor/rules/`; this repository does not install published `sdd-*` files into its own `.cursor/`.

The remaining design work is where the new methodology lives, how one `.mdc` file reminds it after copy/pin, and how constraint stays separate from Git procedure.

## Goals / Non-Goals

**Goals:**
- Place Git ↔ OpenSpec traceability inside the existing workflow page, not a new layer or page.
- Choose activation that binds when the parent is asked to commit, without copy-unsafe globs.
- Keep the rule body to the operational must-not plus copy-valid pointers.
- Keep OpenSpec as the requirement source of truth and vendor `/opsx-*` as the lifecycle surface.
- Keep the file true in this repository and in a consuming project.

**Non-Goals:**
- Exact sentence-by-sentence wording of the `.mdc` or the workflow section (Apply writes those against the specs).
- Editing `AGENTS.md`, `README.md`, `sdd-spec-first.mdc`, or archived architecture pages other than `docs/architecture/workflow-system.md`.
- Path-mapping, installer behavior, a second documentation root, or a Git skill.

## Decisions

### Decision 1: Methodology is a workflow section, not a new page or layer

**Choice:** Apply adds a Git ↔ OpenSpec traceability section to `docs/architecture/workflow-system.md`. No `docs/architecture/git-*.md`, no `docs/practices/git-*.md`, no fifth architecture layer. The workflow page remains the collaboration operating model. Overview, documentation index, and `AGENTS.md` are not edited.

**Why:** Git is the VCS that already records what landed around the change lifecycle. A new page would invent a home the documentation tree does not require. Putting the contract only in the rule would make the rule a hidden specification.

**Alternatives considered:**
- New architecture page: extra layer-shaped surface; documentation-architecture would need reopening.
- Practices page sibling of human-AI: splits collaboration recording away from the collaboration model.
- Rule-only, no docs: forbidden hidden spec.
- Extend adoption or asset-lifecycle instead: those pages own baseline identity and asset evolution, not per-change Git history.

### Decision 2: Always-apply is the activation mode

**Choice:** Frontmatter uses exceptional `alwaysApply: true`. No `globs`. `description` is present for humans and for Cursor metadata; it is not the activation mechanism.

**Why:** The failure happens when the parent is asked to record work in Git, including product work outside `.cursor/**/sdd-*`. Default glob-scoped activation has no copy-safe path for that moment. `openspec/**` and `docs/**` are forbidden globs. Description-only activation is forbidden. `@mention` is not the distribution model. A skill would bind only when invoked; the failure class is not invoking it.

This is a short **adoption invariant**: after copy/pin, change-related Git history in the host repository must remain attributable to that repository's OpenSpec workspace. The body stays short so a second always-apply rule is not a dumped Git handbook. Spec First remains a distinct concern; this file does not invoke it.

**Alternatives considered:**
- Glob `.cursor/**/sdd-*`: copy-safe, misses product and OpenSpec artifact commits.
- Glob `openspec/**` or `docs/**`: forbidden by rule-system architecture.
- Leave the line only in the consuming project's `AGENTS.md`: cheaper in length, but this change does not write that file and does not reopen adoption Configure.
- Skill instead of rule: procedure-shaped; does not bind without invocation.
- Description-only: forbidden; persistence would be probabilistic.

### Decision 3: Filename is `sdd-git-traceability.mdc`

**Choice:** Source path `assets/cursor/rules/sdd-git-traceability.mdc`. Installed path `.cursor/rules/sdd-git-traceability.mdc`. Concern name `git-traceability`, not `sdd-rule-*`, not a procedure verb (`git-workflow`), not `git-conventions`.

**Why:** Rule-system naming is `sdd-<concern>`. Traceability names the constraint. `git-conventions` invites message grammar, branching, and tooling. `git-workflow` is a skill-shaped name this change rejects.

**Alternatives considered:**
- `sdd-git-conventions.mdc`: baggy concern; kitchen-sink risk.
- `sdd-git-workflow.mdc`: procedure-verb; collides with a future skill.
- `sdd-git-traceability-rule.mdc`: redundant `rule` suffix; collides with forbidden `sdd-rule-*`.

### Decision 4: Body is the must-not plus dual-root pointers

**Choice:** The file states, in operational language:

1. Git work associated with an OpenSpec change in **this** repository's OpenSpec workspace must be attributable to that change.
2. A single commit must not contain work that belongs to more than one OpenSpec change.
3. Git history is not the specification; OpenSpec remains the requirement contract.
4. Committing propose, apply, sync, or archive work for a change is allowed when that commit is attributable to that change. Not every commit must name a change.

Then it points at existing methodology by **page title** and names both documentation roots: `docs/` in this repository, `docs/sdd-framework/` after copy/pin. It does not paste those pages. It does not hardcode a single path that is valid in only one universe. Attribution means a reader of the commit can identify the change; the file does not prescribe subject line, trailer, or Conventional Commits.

**Why:** Quality bar is constraint plus pointer. A single hard-coded `docs/architecture/workflow-system.md` breaks after adoption. Dual-root wording stays true in both places. If OpenSpec is not initialized yet, (3) remains true: commit messages are still not the spec.

**Alternatives considered:**
- Paste the workflow section into the rule: documentation dump; hidden spec.
- Pointer only to `docs/...`: false after copy/pin.
- Pointer only to `docs/sdd-framework/...`: false in this repository.
- Require a specific trailer or `feat:` prefix: imposes grammar this change forbids.
- Require an installer to rewrite paths: out of scope.

### Decision 5: Constraint and Git procedure stay split

**Choice:** The rule and the workflow section encode attribution, non-mixing, and Git-is-not-spec. They do not encode staging, rebase, squash, amend, push, pull-request workflow, hooks, or commitlint. A later skill may own procedure; this change does not create it.

**Why:** A rule that teaches how to commit is a skill in disguise. Tooling and branching are consuming-project conventions. Keeping procedure out is what makes always-apply tolerable beside Spec First.

**Alternatives considered:**
- Include a minimal “how to write the message” recipe: format creep; hidden Conventional Commits.
- Create `sdd-git-workflow` in the same change: pack of primitives; out of scope.
- Point the rule at Cursor user rules for commit procedure: not copy-valid; not framework-owned.

### Decision 6: Layer boundaries stay as already specified

**Choice:**

| Layer | Role for this file |
|---|---|
| OpenSpec | Source of truth for requirements; this project's workspace is the contract Git work is attributed to |
| Git | History of landed change work; not a specification; not an architecture layer |
| Cursor | Loads `.cursor/rules/sdd-git-traceability.mdc` and binds the parent agent |
| SDD Framework | Owns the source file and the workflow methodology; copied copies remain framework-owned |
| Consuming project | Receives the file through copy/pin; does not fork it; product specs and Git history stay in **that** repository |

This repository's `AGENTS.md` is unchanged. Spec First is unchanged. Do not invoke other rules from this file. The workflow page may mention that a copied rule reminds the parent of this contract; it must not claim the collaboration model is a workflow engine or that the original architecture change required this file.

**Alternatives considered:**
- Edit `AGENTS.md` to add a Git line: user-out-of-scope; mixes router work into an asset change.
- Invoke `sdd-spec-first` from this rule: rules must not compose as steps.
- Add a namespace or Git-skill file in the same change: catalog/pack; forbidden.

## Risks / Trade-offs

- **[Risk] Second always-apply rule burns context on every product turn** → Mitigation: keep the body to the four operational clauses plus short pointers; one concern only; no Git handbook.
- **[Risk] Reading always-apply as permission to dump Git conventions later** → Mitigation: Decision 2 and Decision 5 limit the exception to this short adoption invariant; later Git procedure stays a skill if justified.
- **[Risk] Contributors encode a commit-message format while drafting the `.mdc`** → Mitigation: specs forbid grammar; tasks validate no Conventional Commits, types, or trailers-as-SHALL.
- **[Risk] Rule restates Spec First and the two concerns blur** → Mitigation: this file does not mention implementation-without-a-change; it talks about recording work that already has a change. Spec First stays the implementation gate.
- **[Risk] Dogfood wording (“this is not a product”) leaks in** → Mitigation: spec forbids framework-repo-only identity; review checks copy-validity.
- **[Risk] “Attributable” is too vague to test** → Mitigation: observable association to the change name in the current workspace is enough; exact placement in the message is not specified.
- **[Trade-off] Dual-root pointer vs a single path** → Two roots in one sentence is slightly longer; it is the only copy-valid option without an installer.
- **[Trade-off] Not requiring every commit to name a change** → Avoids fake attribution; Spec First already limits creating unspecified work.

## Migration Plan

1. Apply updates `docs/architecture/workflow-system.md` with the traceability section and creates `assets/cursor/rules/sdd-git-traceability.mdc` only. No vendor edits. No other `sdd-*` files. No `AGENTS.md` edit. No published copy under this repository's `.cursor/`.
2. Human review validates the page and the file against this change (type, activation, copy-validity, no hidden spec, no docs dump, no OpenSpec wrapper, no Git procedure).
3. Archive makes `sdd-git-traceability` a main spec and merges the workflow delta. The `.mdc` becomes eligible for the published subset already defined by adoption.
4. Consuming projects that later copy/pin receive the file under project-root `.cursor/rules/` and replace it on baseline update. They do not customize it in place.

Rollback is deleting the `.mdc` and reverting the workflow section through a new OpenSpec change (or reverting this change if it is not yet archived). Silent deletion after publication is not the path.

## Open Questions

None that affect specs, activation, or tasks.
