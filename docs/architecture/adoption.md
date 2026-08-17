# Project adoption

This document is the authoritative adoption contract. It is architectural. No installer, CLI, or synchronization mechanism is implemented here.

Consuming projects take a **versioned baseline by copy/pin of a controlled subset**. They do not consume this repository as a git submodule, git subtree, package, or runtime dependency. An OpenSpec store is not the Cursor-asset distribution model; it may be considered later for spec referencing only.

Manual copy of the published subset is valid until a later change automates the same inventory.

## Official model

```
sdd-framework @ git tag
        │
        │  published subset (not the whole repository)
        ▼
consuming project
  .cursor/**/sdd-*          framework-owned after copy
  docs/sdd-framework/       methodology snapshot
  sdd-manifest.yaml         version pin (contract; not created here)
```

The adopted unit is that subset, not `sdd-framework` as a whole. Cursor loads project-root `.cursor/`. A nested clone is not a Cursor load path.

Rejected as the Cursor-asset channel:

- git submodule
- git subtree
- package distribution
- runtime or production dependency

## Ownership

| Concern | This repository | Consuming project |
|---|---|---|
| Methodology requirements | Owns (`openspec/specs/`) | Does not import them as product specs |
| Canonical methodology prose | Owns (`docs/`) | Read-only snapshot at `docs/sdd-framework/` |
| `sdd-*` Cursor assets | Source of truth | Copied; remain **framework-owned** |
| `opsx-*` / `openspec-*` | Vendor (OpenSpec in this repo) | Vendor (OpenSpec in **that** repo) |
| `AGENTS.md` | Router for the framework repo | Router for the **product** repo |
| Product domain, specs, code | Forbidden | Owns |
| Project Cursor extensions | Only if promoted here | Owns; names outside reserved prefixes |

A consuming project retains ownership of product requirements, application architecture, business domain, source code, its OpenSpec workspace, project-specific Cursor extensions, and its `AGENTS.md`.

Product behavior is recorded in the consuming project's OpenSpec workspace. It is not recorded here.

This repository's `AGENTS.md` and `README.md` are **never copied verbatim**. A consuming-project `AGENTS.md` must identify that product repository. Copied `sdd-*` names stay framework-owned; the project must not overwrite them in place with product behavior. Project extensions stay in the consuming project until promoted through this repository's OpenSpec lifecycle.

## Published baseline inventory

Absence of a `sdd-*` catalog in this repository is valid. Do not invent stubs in order to adopt.

**May be copied** (when the files exist):

- `.cursor/rules/sdd-*`
- `.cursor/skills/sdd-*`
- `.cursor/agents/sdd-*`
- `.cursor/commands/sdd-*`
- methodology snapshot into the consuming project's `docs/sdd-framework/`

**Obtained locally in the consuming project (not copied from here):**

- `.cursor/commands/opsx-*`
- `.cursor/skills/openspec-*`
- the project's own `openspec/` workspace
- the project's `AGENTS.md`

**Must not be transferred** as adopted baseline:

- this repository's `openspec/specs/` and OpenSpec change history
- this repository's `AGENTS.md` and `README.md`
- this repository's git metadata

## Vendor OpenSpec

OpenSpec vendor Cursor assets (`opsx-*` commands, `openspec-*` skills) are **not distributed by the SDD Framework**. A consuming project that uses OpenSpec obtains them from OpenSpec in that project's workspace. This repository is not the distribution channel for those files.

## Cursor landing paths

Copied framework-owned Cursor assets land in the consuming project's **project-root** `.cursor/` tree, in the primitive-matched paths reserved for `sdd-*`. See [Cursor integration](cursor-integration.md) for reserved prefixes. Nested vendor directories are not a valid Cursor load path.

Canonical methodology stays under this repository's `docs/`. In a consuming project, a methodology snapshot lands at `docs/sdd-framework/`. That subtree is reserved. It is not product architecture and must not be merged into the product documentation root as if it were.

Later `sdd-*` assets must remain valid in a consuming project that has adopted the baseline, not only in this repository. They locate methodology through the adopted documentation root (`docs/` here, `docs/sdd-framework/` there). This page does not create those assets.

## OpenSpec universes

Two workspaces. They are independent.

- This repository's `openspec/` contains **framework** requirements only.
- A consuming project's `openspec/` contains **product** requirements only.

Do not copy `sdd-framework/openspec/` into a consuming project as adopted baseline or as product specifications. Do not add consuming-project product requirements here. A consuming project that uses OpenSpec creates and configures its own workspace for that product; it does not reuse this repository's OpenSpec configuration.

## Version pin

A consuming project that has adopted the baseline records which SDD Framework version it consumes:

- **git tag** — primary identifier
- **commit SHA** — reproducibility
- **`sdd-manifest.yaml`** — project record of that pin

This contract does not create tags, releases, or a manifest file. Those are later release and adoption-implementation changes.

## Update

A framework release is a versioned baseline. A project update is a **reviewed replacement of framework-owned adopted assets only**.

Replace on update:

- copied `.cursor/**/sdd-*`
- `docs/sdd-framework/`
- the version pin

Never overwrite:

- project `AGENTS.md`
- project OpenSpec workspace
- application code
- project-named Cursor assets

Vendor `opsx-*` / `openspec-*` stay on the OpenSpec upgrade path in that repository. Human review of the diff is required. Silent whole-tree overwrite is not the model.

## Lifecycle

Conceptual orientation, not implemented tooling:

```
discover → adopt → configure → develop → update
```

| Stage | Intent |
|---|---|
| **Discover** | Read this contract; choose a framework version (git tag). |
| **Adopt** | Copy the published subset into project-root Cursor paths and `docs/sdd-framework/`; record the pin. |
| **Configure** | Write a project-owned `AGENTS.md`; initialize product OpenSpec locally; add project Cursor extensions outside reserved prefixes. |
| **Develop** | Product work through that project's OpenSpec lifecycle. Copied `sdd-*` assets stay read-only. |
| **Update** | Take a newer tag; replace framework-owned copied paths; review the diff; update the pin. |

An installer may later automate this sequence. It must not invent a different distribution model.

## Development versus production

The SDD Framework is development-time engineering workflow. It is not a library, service, or production dependency.

Production deployments must not depend on:

- `.cursor/`
- OpenSpec artifacts
- the framework documentation snapshot (`docs/sdd-framework/`)
- `sdd-manifest.yaml`

Adoption affects specification practice and Cursor-assisted development. It does not ship inside production executables, services, or runtime configuration.

## What this repository does not do

- It does not host consuming-project product specifications.
- It does not require a bootstrap CLI, installer, or sync script in this change.
- It does not distribute vendor OpenSpec Cursor assets.
- It does not use Git submodules, git subtrees, packages, or OpenSpec stores as the Cursor-asset distribution model.
