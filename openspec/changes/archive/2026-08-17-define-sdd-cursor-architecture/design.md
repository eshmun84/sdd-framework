## Context

See `proposal.md` for why. The foundation already documents four layers and the `sdd-*` namespace (`docs/architecture/overview.md`, `openspec/specs/cursor-asset-model`). This repository's `.cursor/` tree contains only vendor `opsx-*` commands and `openspec-*` skills. There is no `.cursor/rules/`, no `.cursor/agents/`, and no `sdd-*` catalog. `AGENTS.md` is the agent router; `docs/` is methodology.

This change writes the constitution those later assets must follow. Implementation is documentation and specs. It does not create Cursor files.

## Goals / Non-Goals

**Goals:**
- Give `docs/architecture/cursor-integration.md` a single, navigable component model that specs can be validated against.
- Keep `docs/architecture/overview.md` as the four-layer summary; add a pointer, not a second constitution.
- Record layer-boundary decisions so later catalog changes do not re-decide primitive meaning, orchestration, or naming.
- Leave vendor OpenSpec assets untouched.

**Non-Goals:**
- Exact sentence-by-sentence wording of the new page (prose is apply work; contracts are in the specs).
- Creating or stubbing `sdd-*` files.
- Choosing the first catalog of skills, rules, commands, or agents.
- Installer, MCP, plugins, hooks, or a consuming-project `AGENTS.md` template.

## Decisions

### Decision 1: New capability, not an overload of `cursor-asset-model`

**Choice:** Add `cursor-component-model` for primitive responsibilities and interactions. Keep `cursor-asset-model` as ownership, reserved prefixes, and paths. Extend it only with exclusive prefixes and primitive-matched paths.

**Why:** Namespace/ownership and “what a rule is” are different contracts. Overloading the foundation spec would mix two concerns and make later catalog changes harder to scope.

**Alternatives considered:**
- Put the whole constitution into `cursor-asset-model`: shorter tree, worse cohesion.
- Split one spec per primitive: too much surface for one constitution.

### Decision 2: Authoritative page is `docs/architecture/cursor-integration.md`

**Choice:** New architecture page owns the component constitution. Overview stays the four-layer diagram plus a short pointer. `docs/README.md` and `AGENTS.md` link; they do not copy.

**Why:** Foundation already forbade duplicating architecture into entrypoints and deferred a deeper Cursor docs tree until this class of change. A sibling of `overview.md` and `adoption.md` matches the existing `docs/architecture/` layout without inventing `docs/cursor/`.

**Alternatives considered:**
- Fold the constitution into `overview.md`: that file would stop being a four-layer summary.
- `docs/cursor/` tree now: documents a catalog this change forbids creating.

### Decision 3: Map “SDD agent” to Cursor subagents

**Choice:** An SDD Framework agent is a Cursor custom subagent (later: `.cursor/agents/sdd-<role>.md`). The default Cursor Agent is the orchestrator. `AGENTS.md` is not an agent.

**Why:** Cursor already has this primitive (isolated context, optional model, optional readonly). Leaving “agent” metaphorical would collide with `AGENTS.md` and invite product-team role-play.

**Alternatives considered:**
- Treat skills with personas as agents: no isolation, mixes procedure and role.
- Hierarchical manager agents: contradicts leaf-specialist orchestration and would wrap OpenSpec.

### Decision 4: Parent orchestrates; `sdd-*` agents are leaves

**Choice:** Multi-agent structure is one parent Cursor Agent plus optional specialist subagents. Framework agents do not supervise other SDD agents and do not own `/opsx-*`.

**Why:** OpenSpec already owns lifecycle. Cursor already owns delegation. A framework “org chart” would duplicate both.

**Alternatives considered:**
- Orchestrator subagent that calls other SDD agents: extra layer, no new capability.
- Product agents in this repo: violates spec-universe isolation.

### Decision 5: Skills are canonical; commands are optional thin triggers

**Choice:** A reusable procedure is a skill. A command exists only for an explicit human trigger that must not auto-fire. If both exist, they share one `sdd-*` name; the command does not duplicate procedure text. Prefer a skill invoked with `/` (including `disable-model-invocation` when the trigger must stay explicit) over a second markdown file that clones OpenSpec’s command+skill duplication.

**Why:** Vendor OpenSpec pairs duplicate content. Cursor is consolidating slash triggers into skills. The framework should not freeze the vendor duplication as its own pattern.

**Alternatives considered:**
- Always ship command+skill pairs like OpenSpec: guaranteed drift.
- Commands as the canonical procedure: fights Cursor’s skill model and this proposal’s “skills are canonical” rule.

### Decision 6: No `sdd-*` wrappers for OpenSpec lifecycle

**Choice:** Forbid framework commands or skills whose purpose is explore, propose, apply, update, sync, or archive as a replacement or wrapper of `/opsx-*` / `openspec-*`.

**Why:** Already required by vendor-asset ownership. Restating it in the component model makes it testable when someone later proposes `/sdd-explore`.

**Alternatives considered:**
- Thin `sdd-*` aliases that call vendor skills: still a second lifecycle surface and upgrade hazard.

### Decision 7: `AGENTS.md` stays always-on; always-apply rules are exceptional

**Choice:** Identity and navigation stay in `AGENTS.md`. Future rules are operational constraints, preferably glob-scoped. Always-apply rules need a justification that `AGENTS.md` cannot keep short.

**Why:** Always-on context is expensive. Documentation-architecture already forbids a second copy of governance. Rules that republish `docs/` will drift.

**Alternatives considered:**
- Large always-apply rule pack instead of `AGENTS.md`: duplicates the router and bloats every session.
- Intelligent/description-only rules for procedures: those are skills.

### Decision 8: Project naming is reserved-prefix exclusion, not a mandatory product prefix

**Choice:** Consuming projects MUST NOT use `opsx-*`, `openspec-*`, or `sdd-*`. They MAY use any other project-specific names. A mandatory `airen-*` / `nexus-*` convention is not required by this constitution.

**Why:** The user-locked naming model is reservation plus project-specific names. A mandatory product prefix can be added later if copy/pin makes mixed trees hard to read. Specs already forbid overwriting `sdd-*` in place.

**Alternatives considered:**
- Mandatory `<product>-*` now: stricter, but invents a product-naming scheme in the framework repo before adoption tooling exists.

### Decision 9: This apply creates zero Cursor catalog files

**Choice:** Apply updates docs, entrypoint links, and (after archive) specs. It does not add `.cursor/rules/`, `.cursor/agents/`, or `sdd-*` skills/commands, including empty stubs.

**Why:** `cursor-asset-model` already made absence of the catalog valid. Stubs would fake a catalog and invite use before a dedicated change specifies it.

**Alternatives considered:**
- Empty `sdd-*` placeholders: forbidden by the proposal non-goals.

Non-normative examples that MAY appear on the architecture page to explain naming (not a catalog to implement): `sdd-spec-authoring` (rule), `sdd-review-change` (skill), `sdd-spec-auditor` (agent).

## Risks / Trade-offs

- **[Risk] Contributors still invent `sdd-*` files in the next chat** → Mitigation: `AGENTS.md` and working-agreements keep pointing at the constitution; tasks do not create catalog files; specs make absence valid.
- **[Risk] Command-vs-skill trigger mechanism drifts with Cursor** → Mitigation: spec the *roles* (canonical procedure vs optional human trigger), not a frozen file format; later catalog changes pick the current Cursor trigger mechanism.
- **[Risk] Overview and the new page drift** → Mitigation: overview owns four layers only; new page owns components; entrypoints link.
- **[Trade-off] Reserved-prefix exclusion vs mandatory product prefix** → Exclusion is locked; product prefixes remain a later adoption convention if needed.
- **[Trade-off] Constitution without examples vs a starter catalog** → Examples stay non-normative so apply cannot be read as permission to create files.

## Migration Plan

Greenfield documentation. No production system and no Cursor catalog to migrate.

1. Apply writes `docs/architecture/cursor-integration.md` and adds links from `docs/architecture/overview.md`, `docs/README.md`, and `AGENTS.md`. Optionally a one-line status clarification in `README.md`.
2. Vendor `.cursor/` files stay unchanged. No `sdd-*` files are added.
3. Archive syncs `cursor-component-model` into `openspec/specs/` and merges the ADDED deltas into `documentation-architecture` and `cursor-asset-model`.

Rollback is reverting the documentation and change artifacts.

## Open Questions

None that affect this change. First `sdd-*` catalog, consuming-project `AGENTS.md` template, mandatory product prefixes, and installer/sync remain dedicated later changes.
