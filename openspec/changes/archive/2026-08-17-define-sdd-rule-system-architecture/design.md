## Context

See `proposal.md` for why. `cursor-component-model` already maps an SDD rule to a persistent operational constraint, keeps always-apply exceptional, and treats description-only procedures as skills in disguise. `cursor-asset-model` already reserves `sdd-*` and the `.cursor/rules/` path. `project-adoption` already lists `.cursor/rules/sdd-*` as copyable and requires later assets to remain valid after copy/pin. `sdd-skill-architecture` already classifies persistent restrictions as rules. This repository still has no `.cursor/rules/` tree and no `sdd-*` rule catalog.

`docs/architecture/cursor-integration.md` is the component constitution; it must not become the rule handbook.

This change writes the rule operating model. Implementation is documentation and specs. It does not create Cursor rule files.

## Goals / Non-Goals

**Goals:**
- Give `docs/architecture/rule-system.md` a single, navigable rule operating model that specs can be validated against.
- Keep `docs/architecture/cursor-integration.md` as the component constitution; add a pointer, not a second copy of the operating model.
- Record creation criteria, activation policy, copy-validity, file contract, quality bar, and OpenSpec lifecycle of rule assets so later catalog changes do not re-decide them.
- Leave vendor OpenSpec assets, the component constitution's primitive definitions, the agent operating model, and the skill operating model untouched.

**Non-Goals:**
- Exact sentence-by-sentence wording of the new page (prose is apply work; contracts are in the specs).
- Creating or stubbing `sdd-*` rule files or a `.cursor/rules/` directory.
- Choosing the first catalog of rules.
- Changing `project-adoption` or `cursor-asset-model` (the inventory and copy/pin model already include rules).
- Hardening Cursor's rules engine, adding templates, MCP, hooks, or installer/sync tooling.
- Reopening when a skill or agent is justified.

## Decisions

### Decision 1: New page, not an expanded constitution

**Choice:** Add `docs/architecture/rule-system.md` as the authoritative operating model. Keep the Rules section of `cursor-integration.md` short: operational constraint, prefer glob-scope, always-apply exceptional, pointer to the new page.

**Why:** The Cursor architecture change made `cursor-integration.md` the component constitution. Folding the operating model into it would stop that page from being a primitive map. A sibling of `agent-system.md` and `skill-system.md` matches `docs/architecture/` without inventing `docs/rules/`.

**Alternatives considered:**
- Expand the Rules section of `cursor-integration.md`: one file, worse cohesion, same mistake the agent and skill changes avoided.
- `docs/rules/` tree now: documents a catalog this change forbids creating.

### Decision 2: New capability `sdd-rule-architecture`

**Choice:** Add `sdd-rule-architecture` for the operating model. Do not overload `cursor-component-model` with creation criteria, activation policy, file contract, or rule-asset lifecycle. Extend `documentation-architecture` so the docs tree requires the new page. Do not extend `repository-hygiene`; rules are already named as trackable baseline. Do not extend `project-adoption`; copy/pin of `.cursor/rules/sdd-*` is already specified.

**Why:** Primitive meaning and operating rules are different contracts. The agent and skill changes rejected one-spec-per-primitive; this is a system spec, not a split of "what a rule is."

**Alternatives considered:**
- Only extend `cursor-component-model`: smaller tree, mixes constitution with operating model, invites duplicated SHALLs.
- Also extend `repository-hygiene`: no new ignore risk; rules are already named.
- Also extend `project-adoption`: would restated copy/pin without changing behavior.

### Decision 3: Creation bar includes copy-validity

**Choice:** A framework rule is justified only when the need is a persistent operational constraint, it applies repeatedly, the wording is operational, it remains true after copy/pin into a consuming project, and no cheaper primitive fits. Identity stays in `AGENTS.md`. Requirements stay in OpenSpec specs. Prose stays in `docs/`. Procedures are skills. Isolated judgment is an agent. Session instruction is a prompt. OpenSpec lifecycle stays vendor-owned. Constraints that are true only in this repository stay in this `AGENTS.md` or in a non-`sdd-*` project rule here.

**Why:** The constitution's "cheapest primitive" table is a map, not an operating test. Without copy-validity, the first `sdd-*` rule will encode dogfood ("this is not a product") that is false in every consuming project.

**Alternatives considered:**
- Constraint alone, without copy-validity: adopted rules would lie in product repos.
- A dogfood subclass of `sdd-*` excluded from the published inventory: splits the namespace and fights the existing adoption list.

### Decision 4: Activation is glob-scoped, copy-safe, and not discoverable

**Choice:** Default to glob-scoped activation on paths whose meaning is identical after copy (framework-owned Cursor assets). Always-apply is exceptional and limited to short adoption or namespace invariants that must bind during product work. Description-only ("apply intelligently") is forbidden for framework rules. Manual `@mention` is not the distribution model. Globs on `openspec/**` and `docs/**` are forbidden because those trees mean different things here and in a consuming project.

**Why:** Skills are invoked; agents are launched; rules fire from paths. `openspec/**` in this repo is framework specs; in a consuming project it is product specs. Description-only activation recreates the "skills in disguise" failure the constitution already named, except as optional discovery of a constraint — which means it is not persistent. The constitution example `sdd-spec-authoring` remains non-normative naming, not a glob design.

**Alternatives considered:**
- Always-apply as the default for adopted rules: burns context during product work; contradicts the constitution.
- Allow `openspec/**` / `docs/**` globs for "universal SDD practice": still unsafe because this repo's spec rules (no application stack) are not product spec rules.
- Allow description-only for constraints with recorded justification: makes persistence probabilistic and collides with skill ambient discovery.
- Dual glob files or templated globs at copy time: invents installer behavior this change forbids.

### Decision 5: Rules bind the parent session

**Choice:** Framework rules bind the parent Cursor Agent. Specialist subagent inheritance is not a framework contract. Specialists point at `docs/` for constraints; they do not reprint rule bodies.

**Why:** Cursor rule inheritance into subagents is not a stable contract the framework should depend on. Duplicating rule text into agent files recreates the docs-dump failure.

**Alternatives considered:**
- Claim rules bind all specialists: unverifiable, invites duplicate text in agent files.
- Require specialists to load the same `.mdc` files: invents a Cursor mechanism the framework does not own.

### Decision 6: Project `.cursor/rules/` only; filename is `sdd-<concern>.mdc`

**Choice:** Framework rules live at `.cursor/rules/sdd-<concern>.mdc` in the project tree (versioned baseline). They are not distributed as `~/.cursor/rules/` and not homed in Cursor team-dashboard or user rules. Frontmatter records `description` and the chosen activation (`globs` or exceptional `alwaysApply`). The body is the constraint plus pointers to methodology — not a reprint. Pointers must remain valid after methodology lands at `docs/sdd-framework/` in a consuming project.

**Why:** User-level `sdd-*` leaks into non-SDD repos. The agent and skill operating models already made the same distribution choice. Long essays in `.mdc` recreate `docs/` inside a rule.

**Alternatives considered:**
- User-level or team-dashboard distribution: overwrite and leak hazards; not copy/pin.
- Nested `RULE.md` in content trees: not a Cursor load path the adoption contract copies.

### Decision 7: Naming stays `sdd-<concern>`; no product-prefix mandate

**Choice:** Framework rules use `sdd-<concern>` (one operational topic). That contrasts with skill `sdd-<procedure>` (verb) and agent `sdd-<role>` (noun-role). Do not use `sdd-rule-*`. Project rules use names outside reserved prefixes. Do not require `airen-*` / `nexus-*`. Do not publish a catalog.

**Why:** Reserved-prefix exclusion is already locked. Concern vs procedure vs role makes a playbook rule (`sdd-review-change`) or persona rule (`sdd-reviewer`) visibly wrong. Examples stay non-normative so apply cannot be read as permission to create files.

**Alternatives considered:**
- `sdd-<boundary>` filenames: too abstract; the body already encodes the boundary.
- Procedure or role names: collides with skills and agents.
- Mandatory product prefixes now: invents product naming before adoption tooling exists.

### Decision 8: Quality is behavioral, not a line-count SHALL

**Choice:** A valid rule is concise, operational, one concern, non-duplicative, and referential. It must not become a hidden spec, a skill, or a persona. Cursor's ~50-line guidance may be mentioned as quality orientation on the architecture page. Specs do not impose a numeric line limit.

**Why:** Specs should stay behavioral. A 51-line rule that is still one constraint is not a different capability from a 49-line rule.

**Alternatives considered:**
- Encode "under 50 lines" as a SHALL: typographic, brittle, not observable methodology behavior.
- No size guidance at all: invites docs dumps the quality bar already forbids.

### Decision 9: Rules accumulate; they do not compose as procedures

**Choice:** Multiple rules may be in context at once. A rule MUST NOT invoke another rule as a step. Overlap is a quality failure, not a composition feature.

**Why:** Rules are constraints, not a workflow engine. Skill chaining already covers procedure composition.

**Alternatives considered:**
- A meta-rule that lists all other rules: duplicates Cursor's loader and `AGENTS.md`.
- Allow rules to name other rules as steps: recreates skills.

### Decision 10: This apply creates zero rule files

**Choice:** Apply writes `docs/architecture/rule-system.md` and navigation links. It does not add `.cursor/rules/` or any rule files, including empty stubs. Rule-asset lifecycle (discover → propose → design → implement → validate → adopt → update → retire) is specified for *later* changes.

**Why:** Same as the constitution, agent, and skill changes: stubs fake a catalog.

**Alternatives considered:**
- Empty `sdd-*` placeholders: forbidden by the proposal non-goals.

Non-normative examples that MAY appear on the architecture page to explain naming are concern nouns, not assets to create in this change. The constitution's `sdd-spec-authoring` example remains non-normative and is not a glob or catalog entry.

## Risks / Trade-offs

- **[Risk] Contributors still add `sdd-*` rules in the next chat** → Mitigation: `AGENTS.md` keeps the "do not invent the catalog" rule; tasks do not create rule files; specs make absence valid.
- **[Risk] Glob ban on `openspec/**` is read as "framework rules cannot constrain spec authoring"** → Mitigation: the page states that methodology authoring lives in `docs/`, specs, vendor OpenSpec skills, and this repo's dogfood surface; adopted `sdd-*` rules protect framework assets and namespace invariants instead of globbing product spec trees.
- **[Risk] Constitution page and rule-system page drift** → Mitigation: constitution keeps a short Rules section plus a pointer; operating model lives on one page; entrypoints link.
- **[Risk] Rule vs skill tests are restated in two operating models** → Mitigation: this page owns the rule-side test and points at `skill-system.md` for procedures; it does not copy the skill handbook.
- **[Trade-off] Copy-safe globs vs methodology-file targeting** → Copy-safety is locked; a later change would be required to introduce path-mapping at adoption time.
- **[Trade-off] Operating model without examples vs a starter catalog** → Examples stay non-normative.

## Migration Plan

Greenfield documentation. No rule catalog to migrate.

1. Apply writes `docs/architecture/rule-system.md` and adds links from `docs/architecture/cursor-integration.md`, `docs/architecture/overview.md`, `docs/README.md`, and `AGENTS.md`. Optionally a status clarification in `README.md`.
2. Vendor `.cursor/` files stay unchanged. No `sdd-*` files are added. `.cursor/rules/` is not created.
3. Archive syncs `sdd-rule-architecture` into `openspec/specs/` and merges the ADDED delta into `documentation-architecture`.

Rollback is reverting the documentation and change artifacts.

## Open Questions

None that affect this change. The first `sdd-*` rule catalog remains a dedicated later change.
