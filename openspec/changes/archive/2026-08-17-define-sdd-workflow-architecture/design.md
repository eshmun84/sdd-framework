## Context

See `proposal.md` for why. Cursor constitution, agent/skill/rule operating models, human-AI practice, vendor OpenSpec lifecycle, adoption, and working agreements already exist. None of them owns how those pieces collaborate through one change.

`openspec-governance` already requires lifecycle documentation to treat `explore → propose → apply → sync → archive` as orientation, not a mandatory command sequence, and to defer command semantics to vendor assets. `human-ai-interaction` already defines prompts as session instructions. This change must compose those contracts, not reopen them.

Implementation is documentation and specs. It does not create Cursor files, prompt libraries, or automation.

## Goals / Non-Goals

**Goals:**
- Give `docs/architecture/workflow-system.md` a single, navigable collaboration operating model that specs can be validated against.
- Keep the four-layer overview, vendor OpenSpec lifecycle page, human-AI practice, and working agreements in their current roles; add pointers, not second copies.
- Record stage identity, gates, review-without-command, and dual-universe applicability so later catalog or automation changes cannot smuggle a workflow engine.
- Align `AGENTS.md` with existing OpenSpec-governance: require artifacts, not a mandatory command sequence.

**Non-Goals:**
- Exact sentence-by-sentence wording of the new page (prose is apply work; contracts are in the specs).
- Creating `.cursor/` assets, `sdd-*` files, prompt templates, or scripts.
- Reopening Cursor, agent, skill, rule, adoption, or human-AI requirement contracts except navigation.
- Changing vendor OpenSpec command behavior or the OpenSpec schema.

## Decisions

### Decision 1: Architecture page, not a fifth layer

**Choice:** Authoritative prose lives at `docs/architecture/workflow-system.md`. `docs/architecture/overview.md` stays the four-layer summary and gains a pointer. Do not add a box or table row for workflow, prompts, or planning assistants as a layer.

**Why:** The four layers are OpenSpec, Cursor, SDD Framework, and consuming projects. Workflow is how those layers operate together, the same way agent-system is an operating model rather than a layer. Putting it under `docs/architecture/` matches agent, skill, and rule operating models.

**Alternatives considered:**
- `docs/lifecycle/sdd-workflow.md`: sibling of the vendor page, but two “workflow” files in `lifecycle/` invite mixing command surface with collaboration model.
- Expand `docs/lifecycle/openspec-workflow.md`: collides with the archived rule that this page defers command semantics and stays orientation-only.
- Expand `docs/practices/human-ai-interaction.md`: mixes session prompting with durable stage gates.

### Decision 2: New capability `sdd-workflow-architecture`

**Choice:** Add `sdd-workflow-architecture` for the operating model. Extend `documentation-architecture` so the docs tree requires the page and forbids duplication. Do not modify `openspec-governance`, `human-ai-interaction`, `cursor-component-model`, `sdd-agent-architecture`, `sdd-skill-architecture`, `sdd-rule-architecture`, or `project-adoption`.

**Why:** Collaboration behavior is a distinct contract. Overloading OpenSpec governance would reopen “orientation not sequence.” Overloading human-AI practice would reopen prompt identity. Overloading Cursor/agent/skill/rule would treat a lifecycle as a primitive.

**Alternatives considered:**
- Only extend `documentation-architecture`: would require a page without saying what the workflow must establish.
- Delta `openspec-governance` to mention the SDD workflow: unnecessary; the existing orientation and vendor-authority requirements remain true. Pointers belong on the lifecycle page via documentation-architecture.

### Decision 3: Human-AI practice ignites stages; workflow owns collaboration

**Choice:** `docs/practices/human-ai-interaction.md` remains how a prompt initiates work. Conceptual prompt kinds (exploration, specification, implementation, review, debugging, documentation) stay on that page. The workflow page owns collaboration stages, participants, gates, and durable transitions. Each page points at the other; neither copies the other.

**Why:** Prompting is session practice. Workflow is change-level collaboration. Folding them would recreate a prompt catalog disguised as architecture, or a workflow that hides inside prompting advice.

**Alternatives considered:**
- Move prompt stages onto the workflow page: reopens human-AI and duplicates session guidance.
- Treat review only as a prompt kind: leaves no durable stage for “judge work against the contract.”

### Decision 4: OpenSpec lifecycle page stays the vendor surface

**Choice:** `docs/lifecycle/openspec-workflow.md` keeps installed `/opsx-*` mapping, typical orientation, and spec-universe isolation. It gains a pointer to `workflow-system.md` for the collaboration model. It does not gain stage-boundary tables, participant matrices, or review-as-command language.

**Why:** Archived `openspec-governance` forbids restating command allow/forbid rules on that page. The SDD collaboration model would violate that if stuffed into the vendor surface.

**Alternatives considered:**
- Merge both topics onto the lifecycle page: shorter nav, second command spec.
- Duplicate the vendor table onto the workflow page: two sources of `/opsx-*` mapping.

### Decision 5: Working agreements stay this-repository governance

**Choice:** `docs/governance/working-agreements.md` keeps framework-specific specify/apply/archive rules (no product specs here, no application code unless a change says so, `sdd-*` namespace). It points to the workflow page for the shared collaboration model and does not grow a second copy of stages, participants, or review.

**Why:** Consuming projects must follow the workflow without inheriting this repository's governance lists. Working agreements are how *this* repo applies the model. Deleting those lists would hide framework-only constraints.

**Alternatives considered:**
- Replace working agreements with “see workflow”: loses this-repo constraints.
- Expand working agreements into the full SDLC: hides the reusable model in governance that consuming projects do not copy as `AGENTS.md`.

### Decision 6: `AGENTS.md` requires artifacts, not a command sequence

**Choice:** Change the router line that currently says framework changes **must** follow `explore → propose → apply → sync → archive` so it requires native OpenSpec artifacts (proposal, specs, tasks; design when needed) and forbids bypassing them, while treating the arrow as typical orientation. Add a link to `workflow-system.md`. Do not modify the `documentation-architecture` agent-entrypoint requirement; it already says “native OpenSpec lifecycle,” not a mandatory sequence.

**Why:** The current wording is stronger than `openspec-governance` and stronger than this workflow spec. Softening it is alignment, not a new identity rule.

**Alternatives considered:**
- Leave `AGENTS.md` as a mandatory sequence: contradicts the new spec and the archived lifecycle change.
- MODIFY the agent-entrypoint requirement: unnecessary churn; the SHALL already matches the softened wording.

### Decision 7: Review is a named SDD stage with no command

**Choice:** Name review as a primary collaboration stage. Do not add `/opsx-review` or `/sdd-review`. Do not require a `sdd-review-change` skill or reviewer agent in this change. Findings judge the existing contract. Missing requirements go to propose or update.

**Why:** OpenSpec has no review command. Inventing one would wrap vendor lifecycle. Leaving review only as a prompt kind leaves no stage boundary for validation. A later catalog change can encode the procedure or isolated stance using existing cheapest-fitting-primitive tests.

**Alternatives considered:**
- Add a framework review command: forbidden wrap of OpenSpec.
- Omit review from the lifecycle: validation stays tribal knowledge.
- Require a review skill now: creates catalog this change forbids.

### Decision 8: Stages are conceptual; humans own gates

**Choice:** Intake, explore, propose, apply, review, and archive are conceptual stages. Update and sync are loop-backs. Humans approve contract creation, apply-as-approved-work, and archive. Cursor may recommend readiness; it may not self-approve. Explore may be skipped when intent is already bounded. File mechanics for unused change folders stay with OpenSpec.

**Why:** Matches vendor orientation. Making the arrow a state machine would redefine OpenSpec. Artifact existence without human acceptance would let an agent “propose then apply” in one turn against working agreements.

**Alternatives considered:**
- Mandatory explore for every change: fights small, already-bounded work and `/opsx-propose` used directly.
- Treat generated artifacts as automatically approved: removes the human gate the spec requires.

### Decision 9: Optional planning assistant; Cursor is the named implementation environment

**Choice:** An external planning assistant is optional. When used, it produces disposable briefs only. Do not name a chat vendor in SHALL language. Implementation environment in this model is Cursor applying an approved change. CI, other IDEs, and cloud agents are unnamed and out of scope.

**Why:** Human-AI practice already locked “external planning assistant” rather than a ChatGPT layer. Requiring a planning assistant would make a vendor habit into architecture. Specifying CI would invent an execution participant the framework does not own.

**Alternatives considered:**
- Required planning-assistant step: overfits current habit; contradicts optional-participant spec.
- Name CI as a validation participant: expands into automation this change forbids.

### Decision 10: This apply creates documentation only

**Choice:** Apply writes `docs/architecture/workflow-system.md` and navigation/pointer edits listed in tasks. It creates no `.cursor/` files, no `prompts/` tree, no scripts, and no stubs. Later skills or agents may operate *inside* a stage; they must not own the lifecycle.

**Why:** Same class as agent/skill/rule/human-AI architecture changes. Stubs fake a catalog. Automation would be a workflow engine.

**Alternatives considered:**
- Ship a `sdd-review-change` skill as illustration: violates non-goals and “absence is valid.”
- Add workflow checklists as Cursor rules: rules are constraints, not procedures, and would duplicate the new page.

## Risks / Trade-offs

- **[Risk] Stages are read as a mandatory `/opsx-*` sequence** → Mitigation: spec and page must repeat “conceptual stages; command behavior stays with OpenSpec”; `AGENTS.md` is softened in this change.
- **[Risk] Review is later implemented as `/sdd-review` wrapping apply/archive** → Mitigation: spec forbids wrapping `/opsx-*`; later catalog changes must pass existing skill/agent tests.
- **[Risk] Workflow page copies human-AI, lifecycle, or working agreements** → Mitigation: documentation-architecture requires pointers; apply tasks are pointer-sized on those pages.
- **[Risk] Consuming projects treat this repository's OpenSpec as theirs** → Mitigation: workflow spec restates universe isolation and points at adoption rather than copying it.
- **[Risk] Planning assistant briefs get checked in as artifacts** → Mitigation: spec keeps briefs as disposable prompts; no path or schema.
- **[Trade-off] Named review stage vs prompt-only review** → Named stage is locked; no command is locked.
- **[Trade-off] Working agreements keep this-repo lists vs shrinking to a pointer** → Pointer plus retained framework-specific lists is locked.

## Migration Plan

Documentation-only.

1. Apply writes `docs/architecture/workflow-system.md`.
2. Add pointers from `docs/architecture/overview.md`, `docs/lifecycle/openspec-workflow.md`, `docs/practices/human-ai-interaction.md`, `docs/governance/working-agreements.md`, `docs/README.md`, `README.md`, and `AGENTS.md`. Soften the `AGENTS.md` sequence line.
3. Vendor `.cursor/` files stay unchanged. No `sdd-*` files are added.
4. Archive syncs `sdd-workflow-architecture` into `openspec/specs/` and merges the ADDED delta into `documentation-architecture`.

After archive, consuming projects receive the page on the next methodology snapshot into `docs/sdd-framework/`. Rollback is reverting the documentation and change artifacts.

## Open Questions

None that affect this change. The first review skill or reviewer agent remains a dedicated later catalog change.
