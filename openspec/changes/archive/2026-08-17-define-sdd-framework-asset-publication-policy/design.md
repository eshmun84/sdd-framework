## Context

See `proposal.md` for why. Asset lifecycle already owns classification, evidence, stages, and “absence is valid.” Adoption already lists copyable `sdd-*` paths “when those assets exist.” The remaining defect is wording: overview, README, Cursor constitution, `AGENTS.md`, and the lifecycle catalog-status section still read as if a later catalog change is remaining foundation work.

This change is documentation and specification. It does not create Cursor files. Skill, rule, agent, workflow, and human-AI operating models stay closed except that their existing “absence is valid / later OpenSpec change” lines remain true as per-asset statements.

## Goals / Non-Goals

**Goals:**
- Home publication policy on `docs/architecture/asset-lifecycle.md` as a section of the existing page, not a new architecture document.
- Close catalog-as-backlog wording on overview, Cursor integration, README, and `AGENTS.md` without copying the policy.
- Point adoption at completeness of a zero-`sdd-*` subset without reopening copy/pin.
- Keep lifecycle identity, classification, evidence, stages, ownership, validation, versioning, deprecation, and retirement as already specified.

**Non-Goals:**
- Exact sentence-by-sentence wording (prose is apply work; contracts are in the specs).
- A new docs page, catalog page, or planned-name list.
- Spec deltas on skill, rule, agent, workflow, human-AI, or Cursor constitution capabilities.
- Git tags, manifests, installers, or release mechanics.

## Decisions

### Decision 1: Policy lives on the lifecycle page, not a new capability or page

**Choice:** Extend `sdd-asset-lifecycle-architecture` and `docs/architecture/asset-lifecycle.md`. Do not add `sdd-asset-publication-policy` as a capability and do not add `docs/architecture/asset-catalog.md` or `asset-publication.md`.

**Why:** Publication of an empty Cursor subset is how the existing publish stage is interpreted, not a fifth architecture topic. A new page would become the catalog document this change forbids.

**Alternatives considered:**
- New capability and page: clearer name, extra navigation and a second home next to lifecycle.
- Only README status: would leave overview and lifecycle “later catalog changes” intact.

### Decision 2: Additive lifecycle requirements; one wording modification

**Choice:** Add publication-policy requirements. Modify only `Operating model without catalog implementation` so “later changes to add them” becomes later **per-asset** OpenSpec changes and an explicit ban on a catalog document. Do not modify classification, creation evidence, stages, ownership, validation, versioning, or deprecation requirements.

**Why:** Leaving the old scenario would keep the ambiguous catalog reading in the durable spec. Rewriting the rest of the lifecycle would violate the non-goal of not changing the model.

**Alternatives considered:**
- ADDED-only: the ambiguous sentence survives archive.
- Rewrite creation or publish-stage requirements: reopens the model.

### Decision 3: Close catalog-as-backlog at entrypoints; leave type operating models alone

**Choice:** Fix catalog-status wording on `docs/architecture/overview.md`, `docs/architecture/cursor-integration.md`, `README.md`, and `AGENTS.md`. Leave skill, rule, agent, workflow, and human-AI pages unchanged: their “first assets are a later OpenSpec change” lines already mean per-asset work, not a catalog.

**Why:** Those type pages are out of scope. Their current catalog-status sections do not promise a catalog document. Entrypoints and overview do.

**Alternatives considered:**
- Edit every Catalog status heading: scope creep and a second copy of the policy.
- Change Cursor constitution spec: the constitution’s “no files required” requirement is still true; only prose needs the catalog-as-work reading closed.

### Decision 4: Adoption completeness is a pointer, not a new distribution model

**Choice:** Modify `Published baseline inventory` so a methodology snapshot with zero `sdd-*` files is a complete copy/pin subset. Keep inventory categories, vendor exclusion, landing paths, and installer deferral.

**Why:** The word “yet” on the current copyable-assets scenario implies incompleteness at the adoption boundary. Copy/pin itself does not change.

**Alternatives considered:**
- Docs-only sentence with no spec delta: the “yet” requirement would remain durable.
- New adoption inventory type: would look like a catalog.

### Decision 5: Example `sdd-*` names stay in place as illustrations

**Choice:** Keep existing non-normative examples on the constitution and type pages. Require that they stay labeled as illustrations and are not a backlog. Do not delete them in this change and do not add new example names.

**Why:** Deleting them is unrelated cleanup. Adding names would create the planned inventory.

**Alternatives considered:**
- Strip all example names now: larger, unrelated edit; naming shape would have no illustration.
- Replace Catalog status headings with a shared include: unnecessary coupling.

## Risks / Trade-offs

- [Remaining “catalog” in historical archive or type-page headings] → Accept leftover headings on out-of-scope pages; new policy owns the meaning. Apply only changes in-scope files plus the listed entrypoints.
- [Contributors still file a catalog change] → Spec forbids planned-name inventories; review against this contract.
- [Consuming projects expect Cursor files in the first pin] → Adoption delta states zero `sdd-*` is complete; methodology snapshot is the payload.

## Migration Plan

Documentation and spec deltas only. After archive, main specs carry the publication policy. No Cursor files to migrate, no consuming-project action, no rollback beyond reverting the change.

## Open Questions

None. Remaining apply work is prose, not deferred product decisions.
