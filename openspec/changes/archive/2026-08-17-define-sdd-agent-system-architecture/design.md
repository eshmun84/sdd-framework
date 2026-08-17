## Context

See `proposal.md` for why. `cursor-component-model` already maps an SDD agent to a Cursor custom subagent, keeps the parent as orchestrator, and treats framework agents as leaves. `cursor-asset-model` already reserves `sdd-*` and the `.cursor/agents/` path. This repository still has no `.cursor/agents/` directory and no `sdd-*` catalog. `docs/architecture/cursor-integration.md` is the component constitution; it must not become the agent handbook.

Cursor can nest subagents and cannot strip git from a subagent except by denying writes. The operating model must be stricter than the vendor runtime.

This change writes that operating model. Implementation is documentation and specs. It does not create Cursor agent files.

## Goals / Non-Goals

**Goals:**
- Give `docs/architecture/agent-system.md` a single, navigable agent operating model that specs can be validated against.
- Keep `docs/architecture/cursor-integration.md` as the component constitution; add a pointer, not a second copy of the operating model.
- Record creation criteria, forbidden ownership, leaf/multi-agent rules, file contract, and OpenSpec lifecycle of agent assets so later catalog changes do not re-decide them.
- Leave vendor OpenSpec assets and the component constitution's primitive definitions untouched.

**Non-Goals:**
- Exact sentence-by-sentence wording of the new page (prose is apply work; contracts are in the specs).
- Creating or stubbing `sdd-*` agent files or `.cursor/agents/`.
- Choosing the first catalog of agents.
- Hardening Cursor's runtime (tool allowlists, MCP, hooks, cloud orchestration).
- Skill-architecture depth or a skill catalog.

## Decisions

### Decision 1: New page, not an expanded constitution

**Choice:** Add `docs/architecture/agent-system.md` as the authoritative operating model. Keep the Agents section of `cursor-integration.md` short: identity as Cursor subagent, parent orchestrates, leaves, pointer to the new page.

**Why:** The previous change made `cursor-integration.md` the component constitution. Folding the operating model into it would stop that page from being a primitive map. A sibling of `cursor-integration.md` matches `docs/architecture/` without inventing `docs/agents/`.

**Alternatives considered:**
- Expand the Agents section of `cursor-integration.md`: one file, worse cohesion.
- `docs/agents/` tree now: documents a catalog this change forbids creating.

### Decision 2: New capability `sdd-agent-architecture`

**Choice:** Add `sdd-agent-architecture` for the operating model. Do not overload `cursor-component-model` with creation criteria, git/implementation bans, file contract, or agent-asset lifecycle. Extend `documentation-architecture` so the docs tree requires the new page. Extend `repository-hygiene` so `.cursor/agents/` remains trackable when files exist.

**Why:** Primitive meaning and operating rules are different contracts. The previous design rejected one-spec-per-primitive; this is a system spec, not a split of "what an agent is."

**Alternatives considered:**
- Only extend `cursor-component-model`: smaller tree, mixes constitution with operating model, invites duplicated SHALLs.
- Skip `repository-hygiene`: gitignore could later exclude agents because the current list names commands, skills, and rules only.

### Decision 3: Creation bar is stance plus isolation

**Choice:** A framework agent is justified only when specialized stance, independent reasoning, *and* context isolation are all needed. Procedural work in the current conversation is a skill.

**Why:** Cursor's own skill-vs-subagent test is isolation and verification. SDD adds stance so a "persona skill" in the implementer's window cannot be called a review.

**Alternatives considered:**
- Isolation alone: would allow search-only agents that duplicate Cursor's built-in explore.
- Stance alone: would allow role-play skills with no fresh context.

### Decision 4: Forbidden ownership includes git and implementation

**Choice:** SDD agents must not own OpenSpec lifecycle, git operations, product implementation decisions, or global orchestration. OpenSpec and "not a product-domain expert" were already locked; git and implementation are explicit here.

**Why:** Cursor subagents inherit parent tools. Without a policy, a "reviewer" can commit. Implementation-capable SDD agents would wrap `/opsx-apply`.

**Alternatives considered:**
- Rely on component-model "leaves / not OpenSpec" only: too easy to miss git and apply.
- Invent a tool allowlist: Cursor does not provide one; that would be a runtime.

### Decision 5: Soft leaf — no SDD-to-SDD spawn

**Choice:** An SDD agent must not spawn, supervise, or orchestrate another SDD agent. No framework agent hierarchy. The parent is the only orchestrator of `sdd-*` agents. This change does not forbid Cursor built-in subagents (`explore`, `shell`, `browser`) as Cursor-owned primitives.

**Why:** Cursor allows two-level nesting. Forbidding `sdd-*` trees is the constraint that prevents a framework org chart. Hard-forbidding all child subagents would also block built-in explore inside a specialist and is more than the required model.

**Alternatives considered:**
- Hard leaf (no child subagents at all): simpler, less capable for large reviews.
- Orchestrator SDD agent: duplicates the parent and wraps OpenSpec.
- Planner → implementer → verifier as framework agents: the first two wrap explore/propose/apply.

### Decision 6: Multi-agent means parent fan-out

**Choice:** The parent MAY launch multiple specialists in parallel. Leaves report only to the parent. No message bus, supervisor agent, or orchestration runtime. Background or cloud execution is a Cursor mode, not a framework design.

**Why:** Cursor already fans out Task calls. Specifying a runtime would implement what this change forbids.

**Alternatives considered:**
- Framework supervisor agent: extra layer, no new capability.
- Specialist-to-specialist channel: hidden coupling, unreviewable.

### Decision 7: Default no-write; inherit the parent model

**Choice:** When a later change creates a framework agent, configure it so it cannot edit files or run state-changing shell commands, unless that later change justifies writes. Use the parent model; do not pin vendor model IDs in the framework. Apply of *this* change still creates no files.

**Why:** Review/analysis specialists should not write. Pinned model IDs drift with Cursor's catalog and leak plan assumptions into the methodology.

**Alternatives considered:**
- Allow writes until a catalog change decides: first agent would likely write.
- Pin a "strong" model for reviewers: vendor-specific, not reusable.

### Decision 8: Project `.cursor/agents/` only

**Choice:** Framework agents live at `.cursor/agents/sdd-<role>.md` in the project tree (versioned baseline). They are not distributed as `~/.cursor/agents/` and not homed in `.claude/agents/` or `.codex/agents/`. File body is stance, forbidden ownership, and pointers to `docs/` — not a playbook (playbooks are skills).

**Why:** User-level `sdd-*` leaks into non-SDD repos. Compatibility directories are not the primitive-matched path already required by `cursor-asset-model`. Long checklists in an agent file recreate skills inside a subagent.

**Alternatives considered:**
- User-level distribution for convenience: overwrite and leak hazards.
- Embed full review checklists in the agent: duplicates skills; Cursor warns against long prompts.

### Decision 9: Naming stays `sdd-<role>`; no product-prefix mandate

**Choice:** Framework agents use `sdd-<role>` (noun-role, e.g. illustrative `sdd-spec-reviewer`). Project agents use names outside reserved prefixes. Do not require `airen-*` / `nexus-*`. Do not publish a catalog.

**Why:** Reserved-prefix exclusion is already locked. A mandatory product prefix is an adoption convention, not an operating-model need. Examples stay non-normative so apply cannot be read as permission to create files.

**Alternatives considered:**
- Mandatory product prefixes now: invents product naming before adoption tooling exists.
- Verb names (`sdd-review-change`) for agents: those are skill names.

### Decision 10: This apply creates zero agent files

**Choice:** Apply writes `docs/architecture/agent-system.md` and navigation links. It does not add `.cursor/agents/` or `sdd-*` files, including empty stubs. Agent-asset lifecycle (propose → design → implement → validate → deprecate) is specified for *later* changes.

**Why:** Same as the constitution change: stubs fake a catalog. Hygiene is updated so a future catalog *can* be tracked, not so this change creates it.

**Alternatives considered:**
- Empty `.cursor/agents/` or placeholder markdown: forbidden by the proposal non-goals.

Non-normative examples that MAY appear on the architecture page: `sdd-spec-reviewer`, `sdd-security-reviewer`. They are not assets to create in this change.

## Risks / Trade-offs

- **[Risk] Contributors still add `sdd-*` agents in the next chat** → Mitigation: `AGENTS.md` keeps the "do not invent the catalog" rule; tasks do not create agent files; specs make absence valid.
- **[Risk] Soft leaf is read as permission to build agent trees with Cursor built-ins** → Mitigation: the page states built-ins are Cursor-owned; `sdd-*` still cannot spawn `sdd-*`.
- **[Risk] Git ban is policy-only because Cursor has no tool allowlist** → Mitigation: default no-write configuration is the enforcement story; parent keeps git.
- **[Risk] Constitution page and agent-system page drift** → Mitigation: constitution keeps a short Agents section plus a pointer; operating model lives on one page; entrypoints link.
- **[Trade-off] Soft leaf vs hard leaf** → Soft leaf is locked; a later change may tighten if specialists start hiding work in nested built-ins.
- **[Trade-off] Operating model without examples vs a starter catalog** → Examples stay non-normative.

## Migration Plan

Greenfield documentation. No agent catalog to migrate.

1. Apply writes `docs/architecture/agent-system.md` and adds links from `docs/architecture/cursor-integration.md`, `docs/README.md`, and `AGENTS.md`. Optionally a one-line pointer from `docs/architecture/overview.md` and a status clarification in `README.md`.
2. Vendor `.cursor/` files stay unchanged. No `sdd-*` files are added. `.gitignore` is checked so it would not exclude `.cursor/agents/` when those files later exist; change it only if it currently would.
3. Archive syncs `sdd-agent-architecture` into `openspec/specs/` and merges the ADDED deltas into `documentation-architecture` and `repository-hygiene`.

Rollback is reverting the documentation and change artifacts.

## Open Questions

None that affect this change. The first `sdd-*` agent catalog remains a dedicated later change.
