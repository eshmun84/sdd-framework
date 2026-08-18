## 1. Create the Spec First rule

- [x] 1.1 Create `.cursor/rules/sdd-spec-first.mdc` with YAML frontmatter that includes `description` and `alwaysApply: true`, and that does not include `globs` or description-only activation
- [x] 1.2 Write the rule body as the operational must-not: do not implement repository work that is not in an approved OpenSpec change in this repository's OpenSpec workspace; a prompt and chat history are not the specification; unspecified surviving behavior goes to the existing OpenSpec change lifecycle, not the prompt; implementing an already approved change is allowed
- [x] 1.3 Add copy-valid methodology pointers by page title that name both documentation roots (`docs/` here, `docs/sdd-framework/` after copy/pin). Do not paste principles, workflow, human-AI, or governance pages into the file

## 2. Validate the rule file

- [x] 2.1 Verify the constraint is scoped to the current project's OpenSpec workspace, remains true if OpenSpec is not initialized yet, and does not encode this repository's "not a product" identity or a ban on product specifications
- [x] 2.2 Verify the file does not wrap, rename, or sequence vendor `/opsx-*` or `openspec-*` assets, and does not include spec-authoring steps, inputs, or outputs
- [x] 2.3 Verify the file is one concern, does not invoke other rules, and does not introduce Spec First behavior that is not already in archived OpenSpec specifications

## 3. Boundary verification

- [x] 3.1 Verify this change did not add any other `sdd-*` rule, skill, agent, or command, including empty stubs
- [x] 3.2 Verify `AGENTS.md`, `README.md`, archived architecture pages, and vendor `.cursor/commands/opsx-*` plus `.cursor/skills/openspec-*` files are unchanged
- [x] 3.3 Run `openspec validate add-sdd-spec-first-rule --type change --strict` and resolve any validation issues in the change artifacts
