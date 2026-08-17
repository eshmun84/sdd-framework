# Architecture overview

This document is the authoritative description of the four-layer model and Cursor asset ownership. Root entrypoints summarize it; they do not own a second copy.

The SDD Framework is evolved in this repository and consumed by other project repositories. Those roles share assets, not specification universes.

```
┌─────────────────────────────────────────────────────────────┐
│                  SDD Framework (this repo)                   │
│     methodology, governance, docs, adoption contract         │
│     future sdd-* Cursor assets                               │
└────────────┬──────────────────────────────┬─────────────────┘
             │ dogfood                      │ consume (copy/pin
             │                              │ versioned subset)
             ▼                              ▼
┌────────────────────────┐      ┌─────────────────────────────┐
│ OpenSpec               │      │ Consuming project repos     │
│ change lifecycle       │      │ product specs, domain, code │
│ specs, deltas, archive │      │ own OpenSpec workspace      │
└────────────────────────┘      └──────────────┬──────────────┘
                                               │ execute
                                               ▼
                                    ┌─────────────────────┐
                                    │ Cursor              │
                                    │ commands, skills,   │
                                    │ rules, agents       │
                                    └─────────────────────┘
```

## Layer responsibilities

| Layer | Owns | Does not own |
|---|---|---|
| **OpenSpec** | Change lifecycle, specification artifacts, delta specifications, archival lifecycle, specification synchronization | Methodology prose, Cursor UX, product code |
| **Cursor** | Execution of commands, skills, rules, and agents | Canonical specs, project domain requirements |
| **SDD Framework** | Reusable methodology, governance, documentation standards, agent architecture, skill architecture, reusable rules, reusable templates, adoption contracts | Product features of consuming applications |
| **Consuming projects** | Product requirements, application architecture, business domain, source code, their own OpenSpec lifecycle and specifications, project-specific Cursor extensions | Framework methodology (they consume it) |

The framework does not redefine OpenSpec command semantics. Cursor does not replace OpenSpec. Consuming projects do not write product specifications into this repository.

## Cursor asset ownership

OpenSpec-generated Cursor assets are **vendor-managed**:

- Commands named `opsx-*` in `.cursor/commands/`
- Skills named `openspec-*` in `.cursor/skills/`

Those files keep their generated names. The framework does not rename them, wrap them, or mix SDD methodology into them. OpenSpec CLI upgrades may regenerate them.

Future SDD Framework-owned Cursor assets use an explicit **`sdd-*` namespace** for commands, skills, rules, and agents. Framework-owned behavior is never placed in `opsx-*` or `openspec-*` files.

How those primitives are classified, when each should exist, and how they interact is defined in [Cursor integration](cursor-integration.md). That page is the component constitution. This overview does not reproduce it.

How SDD agents are justified, what they must not own, and how they are evolved is defined in [agent system](agent-system.md). That page is the operating model. This overview does not reproduce it.

How SDD skills are justified, invoked, structured, and evolved is defined in [skill system](skill-system.md). That page is the operating model. This overview does not reproduce it.

How humans communicate intent to AI tools is defined in [human-AI interaction](../practices/human-ai-interaction.md). That page is a practice, not a fifth architecture layer. This overview does not reproduce it.

A custom `sdd-*` catalog is a later change; its absence is expected.

## Documentation vs specifications

| Location | Role |
|---|---|
| `docs/` | Human- and agent-readable methodology |
| `openspec/specs/` | Requirement contract for the framework (after archive) |
| `README.md` | Human entrypoint |
| `AGENTS.md` | AI-agent entrypoint |

See [Cursor integration](cursor-integration.md) for the component constitution, [agent system](agent-system.md) for the agent operating model, [skill system](skill-system.md) for the skill operating model, [adoption](adoption.md) for how other repositories consume this baseline, [lifecycle](../lifecycle/openspec-workflow.md) for how this repository uses OpenSpec, and [human-AI interaction](../practices/human-ai-interaction.md) for how humans instruct AI tools.
