## Context

See `proposal.md` for why. `cursor-component-model` already maps an SDD skill to a reusable procedure in the current conversation, keeps commands as optional thin triggers, and forbids wrapping OpenSpec. `cursor-asset-model` already reserves `sdd-*` and the `.cursor/skills/` path. `sdd-agent-architecture` already classifies procedural work as a skill and forbids persona skills pretending to be agents. This repository still has no `sdd-*` skill catalog. Vendor `openspec-*` skills are paired with `opsx-*` commands that duplicate procedure text — a pattern the constitution already rejected for framework assets.

`docs/architecture/cursor-integration.md` is the component constitution; it must not become the skill handbook.

This change writes the skill operating model. Implementation is documentation and specs. It does not create Cursor skill files.

## Goals / Non-Goals

**Goals:**
- Give `docs/architecture/skill-system.md` a single, navigable skill operating model that specs can be validated against.
- Keep `docs/architecture/cursor-integration.md` as the component constitution; add a pointer, not a second copy of the operating model.
- Record creation criteria, decision tests, invocation policy, file contract, quality bar, and OpenSpec lifecycle of skill assets so later catalog changes do not re-decide them.
- Leave vendor OpenSpec assets, the component constitution's primitive definitions, and the agent operating model untouched.

**Non-Goals:**
- Exact sentence-by-sentence wording of the new page (prose is apply work; contracts are in the specs).
- Creating or stubbing `sdd-*` skill files or `.cursor/skills/sdd-*` directories.
- Choosing the first catalog of skills.
- Hardening Cursor's skill loader, adding scripts, MCP, hooks, or installer/sync tooling.
- Reopening when an agent is justified.

## Decisions

### Decision 1: New page, not an expanded constitution

**Choice:** Add `docs/architecture/skill-system.md` as the authoritative operating model. Keep the Skills section of `cursor-integration.md` short: canonical procedure in the current conversation, commands optional, pointer to the new page.

**Why:** The Cursor architecture change made `cursor-integration.md` the component constitution. Folding the operating model into it would stop that page from being a primitive map. A sibling of `agent-system.md` matches `docs/architecture/` without inventing `docs/skills/`.

**Alternatives considered:**
- Expand the Skills section of `cursor-integration.md`: one file, worse cohesion, same mistake the agent change avoided.
- `docs/skills/` tree now: documents a catalog this change forbids creating.

### Decision 2: New capability `sdd-skill-architecture`

**Choice:** Add `sdd-skill-architecture` for the operating model. Do not overload `cursor-component-model` with creation criteria, invocation policy, file contract, or skill-asset lifecycle. Extend `documentation-architecture` so the docs tree requires the new page. Do not extend `repository-hygiene`; `.cursor/skills/` is already trackable.

**Why:** Primitive meaning and operating rules are different contracts. The agent change rejected one-spec-per-primitive; this is a system spec, not a split of "what a skill is."

**Alternatives considered:**
- Only extend `cursor-component-model`: smaller tree, mixes constitution with operating model, invites duplicated SHALLs.
- Also extend `repository-hygiene`: no new ignore risk; skills are already named as trackable baseline.

### Decision 3: Creation bar is a repeatable known methodology procedure

**Choice:** A framework skill is justified only when the need is a repeatable procedure, a known workflow, reusable methodology, and predictable inputs and outputs. Independent judgment with isolation is an agent. Persistent constraints are rules. Identity is `AGENTS.md`. Prose is `docs/`. OpenSpec lifecycle stays vendor-owned.

**Why:** The constitution's "cheapest primitive" table is a map, not an operating test. Without a creation bar, the first skill will be a persona, a docs paste, or `/sdd-explore`.

**Alternatives considered:**
- Procedure alone, without "known / reusable / predictable": would allow exploratory playbooks that belong in `/opsx-explore`.
- Auto-create a skill whenever docs describe a method: would duplicate `docs/` into Cursor files.

### Decision 4: Invocation is explicit by default

**Choice:** Default to explicit invocation (`disable-model-invocation` or equivalent). Description-based discovery is allowed only when the OpenSpec change that creates the skill records why it is still a procedure and not a rule. Always-on skills are forbidden.

**Why:** Always-on context is expensive and is already owned by `AGENTS.md` and exceptional rules. Ambient discovery without justification recreates "apply intelligently" rules that the constitution already called skills in disguise — except they would fire uninvited. Some later procedures (for example in-session spec-authoring methods) will need description discovery; that is an exception with a recorded reason, not the default.

**Alternatives considered:**
- All skills auto-discovered from description: noisy, collides with rules, hard to audit.
- Ban description discovery entirely: forces `/` for every methodology procedure, including ones that should fire while authoring.

### Decision 5: Commands remain optional; first skills need not have command files

**Choice:** This architecture does not require `.cursor/commands/sdd-*`. A command appears only when a later change proves a human needs a named trigger that must not auto-fire *and* skill `/` invocation is insufficient. If both exist, they share one `sdd-*` name; the command does not duplicate procedure text.

**Why:** Already locked by the constitution. Restating it here prevents the first catalog change from copying OpenSpec's command+skill pair.

**Alternatives considered:**
- Always ship command+skill pairs like OpenSpec: guaranteed drift.
- Commands as the canonical procedure: fights Cursor's skill model and the constitution.

### Decision 6: Markdown-first; scripts are out of this architecture

**Choice:** A valid future skill is `SKILL.md` plus optional one-level-deep reference files. Executable `scripts/` inside skills are not part of this operating model. A later dedicated change would be required to allow them.

**Why:** This repository does not ship application code unless a change specifies it. Scripts would invent a runtime inside the methodology baseline.

**Alternatives considered:**
- Allow scripts now "because Cursor skills can have them": expands scope into tooling this change forbids.
- Require scripts for fragile steps: there are no framework skills yet; premature.

### Decision 7: Project `.cursor/skills/` only

**Choice:** Framework skills live at `.cursor/skills/sdd-<procedure>/` in the project tree (versioned baseline). They are not distributed as `~/.cursor/skills/` and not homed in Cursor's internal skill directories. File body is procedure, triggers, constraints, outputs, and pointers to `docs/` — not a methodology reprint.

**Why:** User-level `sdd-*` leaks into non-SDD repos. The agent operating model already made the same distribution choice. Long essays in `SKILL.md` recreate `docs/` inside a skill.

**Alternatives considered:**
- User-level distribution for convenience: overwrite and leak hazards.
- Embed full methodology in the skill: duplicates docs; Cursor skill authoring already warns against token bloat.

### Decision 8: Naming stays `sdd-<procedure>`; no product-prefix mandate

**Choice:** Framework skills use `sdd-<procedure>` (verb or task phrase, e.g. illustrative `sdd-review-change`). That contrasts with agent `sdd-<role>` (noun-role). Project skills use names outside reserved prefixes. Do not require `airen-*` / `nexus-*`. Do not publish a catalog.

**Why:** Reserved-prefix exclusion is already locked. Verb-procedure vs noun-role makes a persona skill (`sdd-reviewer`) visibly wrong. Examples stay non-normative so apply cannot be read as permission to create files.

**Alternatives considered:**
- Noun names for skills: collides with agents and invites personas.
- Mandatory product prefixes now: invents product naming before adoption tooling exists.

### Decision 9: Composition is chaining and parent delegation, not a workflow engine

**Choice:** A skill MAY name another `sdd-*` skill as a step in the same conversation. A skill MAY instruct the parent to delegate to a specialist when a step needs isolation. A skill MUST NOT own agents, supervise `sdd-*` agents, or wrap OpenSpec.

**Why:** Same-conversation chaining is how procedures compose without a runtime. Isolation remains the agent's reason to exist and the parent's job to launch. A skill that spawns agent trees would reopen the agent hierarchy decision.

**Alternatives considered:**
- Forbid all composition: forces giant skills.
- Let skills launch `sdd-*` agents directly as owners: hidden orchestration, contradicts leaf specialists.

### Decision 10: This apply creates zero skill files

**Choice:** Apply writes `docs/architecture/skill-system.md` and navigation links. It does not add `.cursor/skills/sdd-*` or any skill files, including empty stubs. Skill-asset lifecycle (propose → design → implement → validate → deprecate) is specified for *later* changes.

**Why:** Same as the constitution and agent changes: stubs fake a catalog.

**Alternatives considered:**
- Empty `sdd-*` placeholders: forbidden by the proposal non-goals.

Non-normative examples that MAY appear on the architecture page: `sdd-review-change`. They are not assets to create in this change. Conceptual categories (specification, review, development, documentation) MAY be mentioned as buckets; they are not a reserved catalog.

## Risks / Trade-offs

- **[Risk] Contributors still add `sdd-*` skills in the next chat** → Mitigation: `AGENTS.md` keeps the "do not invent the catalog" rule; tasks do not create skill files; specs make absence valid.
- **[Risk] Explicit-by-default is read as "skills never auto-apply"** → Mitigation: the page states description discovery as a justified exception, not a ban.
- **[Risk] Constitution page and skill-system page drift** → Mitigation: constitution keeps a short Skills section plus a pointer; operating model lives on one page; entrypoints link.
- **[Risk] Skill vs agent tests are restated in two operating models** → Mitigation: this page owns the skill-side test and points at `agent-system.md` for isolation justification; it does not copy the agent handbook.
- **[Trade-off] Markdown-only vs scripts** → Markdown-only is locked; a later change may allow scripts if a catalog skill needs a deterministic helper.
- **[Trade-off] Operating model without examples vs a starter catalog** → Examples stay non-normative.

## Migration Plan

Greenfield documentation. No skill catalog to migrate.

1. Apply writes `docs/architecture/skill-system.md` and adds links from `docs/architecture/cursor-integration.md`, `docs/README.md`, and `AGENTS.md`. Optionally a one-line pointer from `docs/architecture/overview.md` and a status clarification in `README.md`.
2. Vendor `.cursor/` files stay unchanged. No `sdd-*` files are added.
3. Archive syncs `sdd-skill-architecture` into `openspec/specs/` and merges the ADDED delta into `documentation-architecture`.

Rollback is reverting the documentation and change artifacts.

## Open Questions

None that affect this change. The first `sdd-*` skill catalog remains a dedicated later change.
