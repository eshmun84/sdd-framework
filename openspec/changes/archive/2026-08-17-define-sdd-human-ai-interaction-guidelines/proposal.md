## Why

The framework already defines OpenSpec as the requirement contract, Cursor as the execution environment, and `AGENTS.md`, rules, skills, and agents as Cursor primitives. It does not define how humans communicate intent, context, constraints, and expected outcomes to AI tools. Without that practice, teams treat chat as a hidden specification system, paste durable knowledge into prompts, and skip OpenSpec because the prompt felt complete.

## What Changes

- Add a **human-to-AI interaction practice**: prompts are session-scoped instructions that initiate work; they are not requirements, durable knowledge, methodology storage, or a replacement for OpenSpec.
- Create `docs/practices/human-ai-interaction.md` as the single authoritative page for prompt identity, intent flow, conceptual prompt stages, adaptive structure, context management, planning-assistant vs Cursor vs OpenSpec boundaries, quality guidelines, and storage/reuse.
- Keep the four-layer architecture unchanged. Do not add an AI integration layer. Entrypoints and the OpenSpec lifecycle page summarize or link; they do not own a second copy.
- Record that an external planning assistant may produce an execution brief, and that the brief remains a disposable prompt, not a stored artifact type.

This change is documentation and specification only. It does **not** create prompt templates, a prompt library, `sdd-*` catalog files, or tool integrations.

## Capabilities

### New Capabilities

- `human-ai-interaction`: Prompt identity (session instruction vs requirement vs docs vs skill vs rule vs agent); prompt/spec separation and intent flow; context management (reference, do not copy); external planning assistant vs Cursor vs OpenSpec boundaries; adaptive prompt structure without a mandatory template; quality bar; storage/reuse (prompts are not framework assets; repeated patterns promote to docs, rules, skills, or agents).

### Modified Capabilities

- `documentation-architecture`: Require a practices area whose first page is the human-AI interaction methodology document; the documentation index MUST link to it; `docs/architecture/overview.md` remains the four-layer summary and MUST NOT own this practice; `README.md` and `AGENTS.md` summarize or link rather than copying it.

## Impact

- Documentation and specs only: new `docs/practices/human-ai-interaction.md`; index and thin pointers in `docs/README.md`, `AGENTS.md`, `README.md`, `docs/lifecycle/openspec-workflow.md`, and a one-line pointer from `docs/architecture/overview.md`; delta specs as listed above.
- No application code, installer, CLI, MCP, plugins, hooks, prompt folders, templates, or Cursor asset files.
- Vendor OpenSpec `opsx-*` commands and `openspec-*` skills stay untouched.
- Cursor component, agent, and skill operating models are not reopened.
- Consuming projects receive the practice later via the methodology snapshot (`docs/sdd-framework/`). They do not receive this repository's OpenSpec universe.

## Non-goals

- Prompt marketplace, prompt library, prompt folders, or a prompt templates catalog.
- Example prompt files stored as framework assets.
- Automatic prompt generation or an AI orchestration runtime.
- ChatGPT product integration.
- Cursor plugins, MCP, or hooks.
- Creating `sdd-*` catalog assets, including empty stubs.
- Wrapping, renaming, or redefining vendor OpenSpec commands (`/opsx-*`).
- Reopening Cursor component, agent, skill, or adoption constitutions except for navigation pointers.
- Changing the OpenSpec schema or adding consuming-project product requirements.
- Installer, bootstrap CLI, or application code.
