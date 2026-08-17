# AGENTS.md

This is the AI-agent entrypoint for the SDD Framework repository. It is a routing contract. Authoritative methodology lives in `docs/`. Authoritative requirements live in `openspec/specs/` after archive.

## What this repository is

This is the **SDD Framework**: a reusable Spec-Driven Development methodology and tooling baseline.

It is **not** a product codebase. Do not treat it as an application. Do not introduce product, business-domain, language, or application-stack work here unless a future OpenSpec change explicitly expands that scope.

## Where to read next

| Need | Go here |
|---|---|
| Documentation index | [docs/README.md](docs/README.md) |
| Principles | [docs/principles.md](docs/principles.md) |
| Four-layer model and Cursor ownership | [docs/architecture/overview.md](docs/architecture/overview.md) |
| How other repos adopt this | [docs/architecture/adoption.md](docs/architecture/adoption.md) |
| OpenSpec workflow | [docs/lifecycle/openspec-workflow.md](docs/lifecycle/openspec-workflow.md) |
| How to change the framework | [docs/governance/working-agreements.md](docs/governance/working-agreements.md) |

## How OpenSpec is used

Framework changes **must** follow the native OpenSpec lifecycle: explore → propose → apply → sync → archive. Use the installed `/opsx-*` commands. Do not bypass proposal, specification, and task artifacts. Do not redefine OpenSpec command semantics.

This repository's OpenSpec specifications describe the **framework only**. Consuming-project product specifications **must not** be written here.

## Boundaries you must respect

- Do not rename, wrap, or edit vendor OpenSpec Cursor assets (`opsx-*` commands, `openspec-*` skills) to add framework methodology.
- Future framework-owned Cursor assets use the `sdd-*` namespace. Do not invent that catalog unless the current change specifies it.
- Do not add an installer, custom schema, or application code unless the current change specifies it.
- Do not couple this framework to a consuming project's runtime or production deployment.

## Config

`openspec/config.yaml` carries repository context and artifact rules. Follow them when creating OpenSpec artifacts.
