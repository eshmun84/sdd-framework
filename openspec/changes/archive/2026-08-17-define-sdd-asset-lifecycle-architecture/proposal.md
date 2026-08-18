## Why

The framework already defines Cursor primitives, agent/skill/rule operating models, workflow collaboration, adoption copy/pin, and prompt promotion. Each type model only says that creating, changing, or deprecating an asset requires an OpenSpec change. None of them owns how a need is classified before a file exists, what evidence justifies creation, how an asset is published into a versioned baseline, or how it is deprecated and retired without silent deletion. Without that operating model, the first catalog change will invent assets prematurely, skip cheaper homes (docs, specs, `AGENTS.md`, vendor OpenSpec), or let consuming projects fork `sdd-*` in place.

## What Changes

- Define the SDD **asset lifecycle architecture**: identity of a framework asset; classification before creation; creation and evidence criteria; conceptual stages from need through retirement; ownership; validation; publication as baseline eligibility; relationship to copy/pin adoption; maintenance; deprecation and retirement; versioning through framework releases rather than per-asset versions.
- Add architecture documentation at `docs/architecture/asset-lifecycle.md`. Keep the four-layer overview, Cursor constitution, agent/skill/rule operating models, workflow, and adoption in their current roles. Those pages gain thin pointers and do not own a second copy of the lifecycle.
- Point `docs/README.md`, `README.md`, and `AGENTS.md` at the new page without copying the operating model.

This change is documentation and specification only. It does **not** create `.cursor/` assets, an asset catalog, installer, manifest, or release automation. Lifecycle definition must precede catalog creation so later asset changes have a single creation and retirement contract.

## Capabilities

### New Capabilities

- `sdd-asset-lifecycle-architecture`: Operating model for how framework-owned Cursor assets evolve from a need through classification, creation, validation, publication, adoption, maintenance, deprecation, and retirement. Covers asset identity (and non-assets), classification order, creation and evidence criteria, conceptual stages, ownership, publication via the versioned baseline, and deprecation without silent deletion. Does not restate Cursor primitive definitions, type operating models, workflow stages, or adoption copy/pin.

### Modified Capabilities

- `documentation-architecture`: Architecture docs MUST include an asset-lifecycle page; the documentation index MUST link to it; `docs/architecture/overview.md` remains the four-layer summary and MUST NOT add a fifth architecture layer; Cursor constitution, agent/skill/rule, adoption, and workflow pages MUST point to the asset-lifecycle page rather than owning a second copy.

## Impact

- Documentation and specs only: new `docs/architecture/asset-lifecycle.md`; thin pointers from overview, Cursor integration, agent/skill/rule pages, adoption, workflow, docs index, `README.md`, and `AGENTS.md`; delta specs as listed above.
- No application code, installer, MCP, plugins, hooks, templates, manifests, release automation, or Cursor asset files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Cursor component, agent, skill, rule, adoption, workflow, and human-AI contracts are not reopened except for navigation pointers.
- Consuming projects are unaffected until a later catalog change creates framework assets. This change only defines the operating model those later assets must follow.

## Non-goals

- Creating `.cursor/` assets or any `sdd-*` rules, skills, agents, or commands, including empty stubs.
- An asset catalog, templates, or examples as framework assets.
- Installer, synchronization tooling, manifest files, release automation, or version-management tooling.
- `/sdd-publish`, `/sdd-validate`, `/sdd-retire`, or any new lifecycle command.
- A workflow engine, asset-management runtime, MCP integration, hooks, or plugins.
- Wrapping, renaming, or redefining vendor OpenSpec commands (`/opsx-*`) or skills (`openspec-*`).
- Reopening the Cursor component constitution (what a rule, skill, command, or agent *is*).
- Reopening the agent, skill, or rule operating models except thin lifecycle pointers.
- Reopening project adoption or workflow requirement contracts except navigation.
- Per-asset versioning or a release calendar.
- Product-specific assets or consuming-project repository changes.
- Changing the OpenSpec schema or mixing specification universes.
