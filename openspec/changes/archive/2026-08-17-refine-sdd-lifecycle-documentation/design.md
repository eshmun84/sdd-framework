## Context

See `proposal.md` for why. `docs/lifecycle/openspec-workflow.md` already states that vendor OpenSpec assets own command behavior, then contradicts that in the Explore purpose cell and the `/opsx-explore` Use cell. Foundation change `establish-sdd-framework-foundation` is implemented and not yet archived; `openspec/specs/` is empty.

This is a wording and ownership-boundary edit in one documentation file, plus an ADDED requirement on `openspec-governance`.

## Goals / Non-Goals

**Goals:**
- Make purpose and Use columns intent-only.
- Qualify the lifecycle arrow as orientation, not a required sequence.
- Keep the existing page disclaimer that vendor assets are authoritative.

**Non-Goals:**
- Exact sentence-for-sentence copies of vendor Explore skill text.
- Editing `AGENTS.md` or governance docs (same class of issue, out of this change).

## Decisions

### Decision 1: One file, three edits

**Choice:** Change only `docs/lifecycle/openspec-workflow.md`: Explore purpose cell, `/opsx-explore` Use cell, and a qualifier on the flow diagram.

**Why:** The defect is compressed command rules in that file. Widening to routers or governance reopens methodology, which this change forbids.

**Alternatives considered:**
- Also fix `AGENTS.md` “must follow explore → propose → …” — related, out of scope.
- Copy vendor Explore stance into `docs/` — would recreate a second command spec.

### Decision 2: Intent wording, not vendor paraphrase

**Choice:** Use the requested intent wording:

- Explore purpose: clarify ideas, problems, requirements, and constraints; command behavior is defined by OpenSpec.
- Use cell: “Discovery and clarification.”
- Flow: typical orientation, not a mandatory execution sequence.

**Why:** Purpose language belongs to SDD methodology. Allow/forbid language belongs to OpenSpec vendor assets.

**Alternatives considered:**
- “Thinking stance; may capture OpenSpec artifacts if asked” — restates vendor rules on this page.

### Decision 3: ADDED requirement on `openspec-governance`, not a new capability

**Choice:** Delta `specs/openspec-governance/spec.md` with ADDED requirements (no Purpose). Do not MODIFY “Native spec-driven lifecycle”; that requirement stays. This adds documentation-precision behavior.

**Why:** Foundation already owns “SHALL NOT redefine OpenSpec command semantics.” This change makes that observable in lifecycle docs. A new capability would split one boundary across two specs.

**Alternatives considered:**
- New `lifecycle-documentation` capability — extra surface for one file.
- MODIFY the existing native-lifecycle requirement — unnecessary; the old requirement remains true.

### Decision 4: Archive foundation before this change

**Choice:** Archive `establish-sdd-framework-foundation` first so `openspec/specs/openspec-governance/spec.md` exists, then sync this ADDED delta into it.

**Why:** Main specs are empty. Archiving this change first would create the capability from a Purpose-less delta.

## Risks / Trade-offs

- **[Risk] Foundation not archived first** → Mitigation: archive foundation before this change; do not archive this delta onto an empty main spec.
- **[Risk] AGENTS.md still implies a mandatory sequence** → Mitigation: accepted for this change; call out as a later precision fix if it recurs.
- **[Trade-off] Shorter Use cell vs fuller Explore explanation** → Shorter Use cell avoids becoming a command spec; purpose cell carries the OpenSpec-authority sentence.

## Migration Plan

1. Apply the three wording edits to `docs/lifecycle/openspec-workflow.md`.
2. Archive foundation (separate operation) before or with this change’s archive so `openspec-governance` main spec exists.
3. Sync this ADDED delta into that main spec.

Rollback is reverting the markdown wording. No runtime impact.
