## Why

OpenSpec is the requirement source of truth. Git is the history of what landed. The framework still has no durable contract for that relationship: change-related work can be committed without being attributable to a change, two OpenSpec changes can share one commit, and a commit message can be treated as a substitute specification. Spec First already binds implementation to an approved change after copy/pin; it does not bind how that work is recorded in Git. User rules and chat are not the contract.

## What Changes

- Specify **Git ↔ OpenSpec traceability** as part of the existing workflow operating model: Git records landed change work; OpenSpec remains the requirement contract; change-related Git work is attributable to the OpenSpec change in the current repository's workspace; a commit does not mix work from different OpenSpec changes; Git history does not replace specifications.
- Add **one** framework-owned Cursor rule at `assets/cursor/rules/sdd-git-traceability.mdc`. After copy/pin the installed file is `.cursor/rules/sdd-git-traceability.mdc`.
- The rule is a persistent operational reminder of that contract. It points at already-authoritative methodology (workflow, plus Spec First as a distinct concern). It does not reprint the workflow page, wrap `/opsx-*`, or encode Git procedure.
- Record type justification, activation, copy-validity, and repetition evidence in this change. Apply writes the workflow-page section and the `.mdc` file.

This change **does** introduce the traceability methodology (it does not exist yet) and materializes it as a rule in the same change so the reminder cannot outrun the contract.

### Type justification

| Alternative | Why it is not this change |
|---|---|
| `AGENTS.md` | Router for **this** repository; never transferred. The constraint can be one line, but the framework does not own the consuming project's router. |
| OpenSpec specification alone | Needed for the contract, insufficient to bind the parent agent during product work after copy/pin. |
| `docs/` alone | Needed for methodology prose; prose is not a persistent Cursor constraint. |
| Skill | Traceability is a must-not without invocation, not a procedure with steps, inputs, and outputs (staging, message drafting, rebase, PR). |
| Agent | No isolated specialist stance. The parent already performs Git operations; specialists must not own Git. |
| Vendor OpenSpec | Explore, propose, apply, update, sync, and archive stay on `opsx-*` / `openspec-*`. This rule does not own those stages. |
| Prompt or user rule | The constraint must still matter after the chat closes and after copy/pin. |
| New architecture layer or docs page | Git is the VCS around the collaboration model, not a fifth layer. Methodology lives in the existing workflow page. |

### Evidence of repetition

- Apply, propose, and archive all produce repository files that are later committed, in this repository and in consuming projects, across unrelated sessions.
- Spec First already travels as always-apply; without a copied Git-traceability rule, attribution and non-mixing have no Cursor binding after adoption.
- The failure class is committing change work without pointing at the change, mixing two changes in one commit, or treating Git history as the spec — not a one-off prompt.

## Capabilities

### New Capabilities

- `sdd-git-traceability`: Mandatory behavior of the single framework-owned Git traceability rule — operational constraint, activation, copy-validity, pointers to existing methodology, and what the file must not contain. Does not restate or replace workflow architecture, Spec First, rule-system architecture, or vendor OpenSpec.

### Modified Capabilities

- `sdd-workflow-architecture`: Add Git ↔ OpenSpec traceability to the collaboration operating model (Git records landed change work; attribution to the current workspace's change; no mixing of distinct changes in one commit; Git is not the specification). Does not reopen stages, gates, participants, vendor wrapping, or the catalog-absence clause for the original architecture change.

## Impact

- `docs/architecture/workflow-system.md` gains a traceability section. No new architecture page, no fifth layer.
- One Cursor rule file under `assets/cursor/rules/sdd-git-traceability.mdc`, plus this change's OpenSpec artifacts.
- After archive, that file is eligible for the published subset already listed by adoption (`.cursor/rules/sdd-*`). Consuming projects receive it through existing copy/pin. It remains framework-owned.
- This repository does not install a published copy under `.cursor/rules/`.
- No application code, installer, manifest, catalog, skill, hook, or other `sdd-*` files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- This repository's `AGENTS.md`, `README.md`, and archived architecture pages other than the workflow page are not modified.
- Consuming-project product behavior is unchanged. The rule binds the parent Cursor Agent in any repository that has adopted it, against **that** repository's OpenSpec workspace and Git history.

## Non-goals

- Conventional Commits, commit types (`feat`/`fix`/`docs`/etc.), gitmoji, or an exact commit-message grammar.
- Branching strategy, protected branches, CODEOWNERS, signed commits, or ticket-tracker IDs.
- Hooks, commitlint, husky, or other Git tooling.
- A Git skill (`sdd-git-workflow` or otherwise), including staging, rebase, squash, amend, push, or PR workflow.
- Requiring every commit in a repository to reference an OpenSpec change (only change-related work must be attributable).
- Restating Spec First, wrapping `/opsx-*` or `openspec-*`, or sequencing vendor commands.
- Creating additional rules, skills, agents, or commands, including empty stubs.
- A catalog, planned-name inventory, or “core rules” pack.
- Reopening `sdd-rule-architecture`, `sdd-spec-first`, `cursor-component-model`, `cursor-asset-model`, `project-adoption`, `documentation-architecture`, `sdd-agent-architecture`, or `sdd-skill-architecture`.
- A new architecture layer or a new documentation page for Git.
- Editing this repository's `AGENTS.md` or `README.md`.
- Globbing `openspec/**` or `docs/**`.
- Description-only (“apply intelligently”) activation or `@mention` as the distribution model.
- Dogfood-only wording that is false in a consuming project.
- Installer, path-mapping at copy time, user-level `~/.cursor/rules/`, or team-dashboard rules.
- Product, domain, or stack conventions.
- Cursor-agent safety such as “do not commit unless the human asks.”
