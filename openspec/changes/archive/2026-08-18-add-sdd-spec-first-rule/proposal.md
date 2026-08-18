## Why

Spec First is already the framework contract: implementation follows an approved OpenSpec change in the current repository's workspace; prompts and chat are not that contract. That must-not is restated in OpenSpec governance, workflow architecture, human-AI interaction, asset lifecycle, working agreements, and this repository's `AGENTS.md`. `AGENTS.md` is never copied. Vendor `/opsx-apply` binds only when invoked. After copy/pin, a consuming project therefore has methodology prose and no always-on Cursor surface for the same constraint. This change materializes that existing restriction as one copy-valid rule so it can travel with the published baseline.

## What Changes

- Add **one** framework-owned Cursor rule at `.cursor/rules/sdd-spec-first.mdc`.
- The rule is a persistent operational reminder: do not implement repository work that is not in an approved OpenSpec change in this project's workspace; do not treat the prompt or chat as the specification; send unspecified surviving behavior to propose or update.
- The rule points at already-authoritative methodology. It does not reprint workflow, human-AI, or governance pages. It does not wrap, rename, or redefine vendor `/opsx-*` commands or `openspec-*` skills.
- Record type justification, activation, copy-validity, and repetition evidence in this change. Apply writes the `.mdc` file only.

This change does **not** add Spec First as a new methodology requirement. Existing specs remain the source of truth for that behavior.

### Type justification

| Alternative | Why it is not this change |
|---|---|
| `AGENTS.md` | Router for **this** repository; never transferred. The constraint can be one line, but the framework does not own the consuming project's router. |
| OpenSpec specification | The requirement already exists. A spec cannot bind the parent agent during product work. |
| `docs/` | Explanation already exists. Prose is not a persistent Cursor constraint. |
| Skill | Spec First is a must-not without invocation, not a procedure with steps, inputs, and outputs. |
| Agent | No isolated specialist stance. The parent already knows the constraint. |
| Vendor OpenSpec | Explore, propose, apply, update, sync, and archive stay on `opsx-*` / `openspec-*`. This rule does not own those stages. |
| Prompt | The constraint must still matter after the chat closes. |

### Evidence of repetition

- The same must-not is encoded in at least four archived capabilities (`openspec-governance`, `sdd-workflow-architecture`, `human-ai-interaction`, `sdd-asset-lifecycle-architecture`) plus this repository's always-on router — a repeated standing instruction, not a one-off prompt.
- Adoption already forbids transferring this `AGENTS.md`. Without a copied rule, that repetition has no Cursor binding in a consuming project.
- Vendor apply only constrains work after someone invokes it. The failure class is implementation requested outside that invocation.

## Capabilities

### New Capabilities

- `sdd-spec-first`: Mandatory behavior of the single framework-owned Spec First rule — operational constraint, activation, copy-validity, pointers to existing methodology, and what the file must not contain. Does not restate or replace OpenSpec governance, workflow, human-AI, asset lifecycle, or rule-system architecture.

### Modified Capabilities

- None. This change does not reopen archived operating models. Spec First semantics stay in the capabilities listed above. Rule creation criteria, activation policy, and file contract stay in `sdd-rule-architecture`. Copy/pin inventory stays in `project-adoption`.

## Impact

- One Cursor rule file under `.cursor/rules/sdd-spec-first.mdc`, plus this change's OpenSpec artifacts.
- After archive, that file is eligible for the published subset already listed by adoption (`.cursor/rules/sdd-*`). Consuming projects receive it through existing copy/pin. It remains framework-owned.
- No application code, installer, manifest, catalog, or other `sdd-*` files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- This repository's `AGENTS.md`, `README.md`, and archived architecture pages are not modified.
- Consuming-project product behavior is unchanged. The rule binds the parent Cursor Agent in any repository that has adopted it, against **that** repository's OpenSpec workspace.

## Non-goals

- Creating additional rules, skills, agents, or commands, including empty stubs.
- A catalog, planned-name inventory, or “core rules” pack.
- Implementing the `.mdc` during propose; Apply creates the file.
- New Spec First methodology requirements, workflow stages, or OpenSpec command semantics.
- Reopening `sdd-rule-architecture`, `sdd-asset-lifecycle-architecture`, `sdd-workflow-architecture`, `human-ai-interaction`, `openspec-governance`, `cursor-component-model`, `cursor-asset-model`, `project-adoption`, or `documentation-architecture`.
- Editing this repository's `AGENTS.md` or `README.md`.
- Wrapping, renaming, or redefining `/opsx-*` or `openspec-*`.
- Globbing `openspec/**` or `docs/**`.
- Description-only (“apply intelligently”) activation or `@mention` as the distribution model.
- Dogfood-only wording that is false in a consuming project.
- Spec-authoring procedure, review playbook, namespace/ownership rule, or production-decoupling rule.
- Installer, path-mapping at copy time, user-level `~/.cursor/rules/`, or team-dashboard rules.
- Product, domain, or stack conventions.
