# SDD Framework

A reusable Spec-Driven Development (SDD) baseline for professional software projects.

This repository is methodology and tooling. It is not an application, a product, or a domain-specific system. It is independent of any programming language or application framework.

## Purpose

Provide a common engineering baseline so multiple projects can use the same Spec-Driven Development lifecycle, documentation standards, governance, and Cursor-assisted workflow.

Consuming projects keep their own product requirements, architecture, and source code. They take a versioned baseline by copy/pin of a controlled subset. They do not couple this framework to production runtimes.

## Principles

- Specify framework changes in OpenSpec before implementing them.
- Use Cursor as the execution environment, not as a replacement for specifications.
- Keep this repository reusable: no product, domain, or stack coupling.
- Keep framework specifications and consuming-project specifications in separate universes.

Full statement: [docs/principles.md](docs/principles.md).

## Architecture

Four layers stay distinct:

| Layer | Role |
|---|---|
| **SDD Framework** (this repo) | Methodology, governance, documentation, adoption contract |
| **OpenSpec** | Change lifecycle and specification artifacts |
| **Cursor** | Execution of commands, skills, rules, and agents |
| **Consuming projects** | Product specs, domain, and application code |

OpenSpec-generated Cursor assets (`opsx-*`, `openspec-*`) are vendor-managed. Future framework-owned Cursor assets use `sdd-*`.

Authoritative detail: [docs/architecture/overview.md](docs/architecture/overview.md). Cursor component model: [docs/architecture/cursor-integration.md](docs/architecture/cursor-integration.md). Agent operating model: [docs/architecture/agent-system.md](docs/architecture/agent-system.md). Skill operating model: [docs/architecture/skill-system.md](docs/architecture/skill-system.md). Adoption: [docs/architecture/adoption.md](docs/architecture/adoption.md).

## Repository navigation

| Path | What it is |
|---|---|
| [README.md](README.md) | Human entrypoint (this file) |
| [AGENTS.md](AGENTS.md) | AI-agent entrypoint |
| [docs/](docs/README.md) | Methodology documentation |
| `openspec/` | Framework specification lifecycle |
| `.cursor/commands/`, `.cursor/skills/` | Vendor OpenSpec Cursor assets |

## Documentation

Start at **[docs/README.md](docs/README.md)**.

That index links to architecture, adoption, lifecycle, and governance. Working agreements and quality rules live there, not in this README.

## Status

This repository is in **foundation**. Identity, documentation architecture, Cursor asset ownership, Cursor component architecture, agent operating model, skill operating model, adoption contract (copy/pin of a versioned subset), OpenSpec governance, and repository hygiene are in place.

The Cursor component constitution, agent operating model, and skill operating model exist. A skill, agent, or command catalog does not. Those catalogs, a multi-agent implementation, and a project installer are later OpenSpec changes. Vendor OpenSpec Cursor assets are obtained from OpenSpec in each repository; they are not part of the copied SDD baseline.
