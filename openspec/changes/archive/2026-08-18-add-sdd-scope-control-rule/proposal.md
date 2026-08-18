## Why

Spec First already binds implementation to an approved OpenSpec change. Git traceability already binds how that work is recorded. Neither binds how far Apply may go once a contract exists: the parent can still add requirements, invent tasks, or ship unsolicited improvements beside the authorized work. After copy/pin, methodology prose is not a Cursor constraint, and vendor `/opsx-apply` binds only when invoked. User rules and chat are not the contract.

## What Changes

- Specify **Apply-time scope control** as part of the existing workflow operating model: an approved change bounds allowed work to that change's proposal, specifications, design when present, tasks, and non-goals; Apply implements that contract; Apply does not add requirements or tasks; Apply does not perform unsolicited improvements outside the contract; work required by the contract, including mechanical edits the contract obliges, remains allowed; checking off existing tasks remains Apply; deviations go to update or a new change.
- Add **one** framework-owned Cursor rule at `assets/cursor/rules/sdd-scope-control.mdc`. After copy/pin the installed file is `.cursor/rules/sdd-scope-control.mdc`.
- The rule is a persistent operational reminder of that contract. It points at already-authoritative methodology. It does not reprint the workflow page, wrap `/opsx-*`, restate Spec First or Git traceability, or encode an apply playbook.
- Record type justification, activation, copy-validity, and repetition evidence in this change. Apply writes the workflow-page section and the `.mdc` file.

This change **does** introduce the Apply-scope methodology (the bound is not yet a first-class workflow requirement) and materializes it as a rule in the same change so the reminder cannot outrun the contract.

### Type justification

| Alternative | Why it is not this change |
|---|---|
| `AGENTS.md` | Router for **this** repository; never transferred. The constraint can be one line, but the framework does not own the consuming project's router. |
| OpenSpec specification alone | Needed for the contract, insufficient to bind the parent agent during product work after copy/pin. |
| `docs/` alone | Needed for methodology prose; prose is not a persistent Cursor constraint. |
| Skill | Scope control is a must-not without invocation, not a procedure with steps, inputs, and outputs for analyzing the change. Vendor `/opsx-apply` already reads the contract. |
| Agent | No isolated specialist stance. Judging scope creep after the fact is Review, not this constraint. Specialists must not own Apply. |
| Vendor OpenSpec | Explore, propose, apply, update, sync, and archive stay on `opsx-*` / `openspec-*`. This rule does not own those stages. |
| Prompt or user rule | The constraint must still matter after the chat closes and after copy/pin. |
| New architecture layer or docs page | Apply-scope is a collaboration bound, not a fifth layer. Methodology lives in the existing workflow page. |

### Evidence of repetition

- Every Apply session, with or without `/opsx-apply`, can add adjacent work once a change is approved, in this repository and in consuming projects.
- Spec First travels as always-apply and stops work with no contract; it does not stop gold-plating inside a contract. Vendor apply only constrains work after someone invokes it.
- The failure class is adding requirements, tasks, or unsolicited improvements during implementation of an approved change — not a one-off prompt.

## Capabilities

### New Capabilities

- `sdd-scope-control`: Mandatory behavior of the single framework-owned Scope control rule — operational constraint, activation, copy-validity, pointers to existing methodology, and what the file must not contain. Does not restate or replace workflow architecture, Spec First, Git traceability, rule-system architecture, or vendor OpenSpec.

### Modified Capabilities

- `sdd-workflow-architecture`: Add Apply-time scope control to the collaboration operating model (an approved change bounds allowed work; Apply does not add requirements or tasks; Apply does not perform unsolicited improvements outside the contract; mechanical work the contract obliges remains allowed; checking off existing tasks remains Apply; deviations go to update or a new change). Does not reopen stages, gates, participants, Git traceability, vendor wrapping, or the catalog-absence clause for the original architecture change.

## Impact

- `docs/architecture/workflow-system.md` gains an Apply-scope section. No new architecture page, no fifth layer.
- One Cursor rule file under `assets/cursor/rules/sdd-scope-control.mdc`, plus this change's OpenSpec artifacts.
- After archive, that file is eligible for the published subset already listed by adoption (`.cursor/rules/sdd-*`). Consuming projects receive it through existing copy/pin. It remains framework-owned.
- This repository does not install a published copy under `.cursor/rules/`.
- No application code, installer, manifest, catalog, skill, agent, command, hook, or other `sdd-*` files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- This repository's `AGENTS.md`, `README.md`, and archived architecture pages other than the workflow page are not modified.
- Consuming-project product behavior is unchanged. The rule binds the parent Cursor Agent in any repository that has adopted it, against **that** repository's OpenSpec workspace.

## Non-goals

- Creating additional rules, skills, agents, or commands, including empty stubs.
- A catalog, planned-name inventory, or “core rules” pack.
- Wrapping, renaming, or redefining `/opsx-*` or `openspec-*`, or sequencing vendor commands.
- Restating Spec First or Git traceability, or invoking those rules as steps.
- Project-management methodology: backlogs, tickets, estimation, sprints, or trackers.
- File allowlists, path inventories, CODEOWNERS, or a filesystem fence as the definition of scope.
- Git policy, commit grammar, branching, or hooks.
- A skill that analyzes change scope or an agent that reviews scope creep.
- Reopening `sdd-rule-architecture`, `sdd-spec-first`, `sdd-git-traceability`, `human-ai-interaction`, `cursor-component-model`, `cursor-asset-model`, `project-adoption`, `documentation-architecture`, `sdd-agent-architecture`, or `sdd-skill-architecture`.
- A new architecture layer or a new documentation page for scope.
- Editing this repository's `AGENTS.md` or `README.md`.
- Globbing `openspec/**` or `docs/**`.
- Description-only (“apply intelligently”) activation or `@mention` as the distribution model.
- Dogfood-only wording that is false in a consuming project.
- Forbidding mechanical edits the approved contract obliges, or forbidding checking off existing tasks during Apply.
- Installer, path-mapping at copy time, user-level `~/.cursor/rules/`, or team-dashboard rules.
- Product, domain, or stack conventions.
