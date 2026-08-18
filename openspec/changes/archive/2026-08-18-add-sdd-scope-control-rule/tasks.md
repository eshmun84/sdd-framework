## 1. Document Apply-time scope control in the workflow page

- [x] 1.1 Add an Apply-time scope control section to `docs/architecture/workflow-system.md` after Incomplete, rejected, and evolving work, describing an approved change as the bound on allowed implementation work (proposal, specifications, design when present, tasks, and non-goals), forbidding new requirements or task items during Apply, treating checking off existing tasks as Apply, forbidding unsolicited improvements the contract does not oblige, allowing obligated mechanical edits, and sending surviving extra work to update or a new change
- [x] 1.2 Verify that section does not add a fifth architecture layer, a new documentation page, a file allowlist, path inventory, CODEOWNERS map, backlog, tickets, estimation, sprints, Git policy, or Apply procedure, does not rewrite catalog status to require this file, and does not replace the existing contract-drift bullet

## 2. Create the Scope control rule

- [x] 2.1 Create `assets/cursor/rules/sdd-scope-control.mdc` with YAML frontmatter that includes `description` and `alwaysApply: true`, and that does not include `globs` or description-only activation
- [x] 2.2 Write the rule body as the operational must-not: implementation of an approved OpenSpec change in this repository's OpenSpec workspace must stay inside that change's proposal, specifications, design when present, tasks, and non-goals; do not add requirements or new tasks during Apply; do not perform unsolicited improvements the contract does not oblige; obligated mechanical edits and checking off existing tasks remain allowed; work that would leave the bound goes through the existing OpenSpec change lifecycle
- [x] 2.3 Add copy-valid methodology pointers by page title that name both documentation roots (`docs/` here, `docs/sdd-framework/` after copy/pin). Do not paste the workflow page, Spec First, or Git traceability into the file

## 3. Validate the rule file

- [x] 3.1 Verify the constraint is scoped to the current project's OpenSpec workspace, remains true if OpenSpec is not initialized yet (the prompt still does not authorize expanding beyond an approved change), and does not encode this repository's "not a product" identity or a ban on product specifications
- [x] 3.2 Verify the file does not wrap, rename, or sequence vendor `/opsx-*` or `openspec-*` assets, and does not include steps for selecting a change, reading planning artifacts, or implementing tasks
- [x] 3.3 Verify the file is one concern, does not invoke other rules, does not encode a file allowlist or project-management methodology, and does not restate Spec First or Git traceability

## 4. Boundary verification

- [x] 4.1 Verify this change did not add any other `sdd-*` rule, skill, agent, or command, including empty stubs, and did not install `sdd-scope-control.mdc` under this repository's `.cursor/`
- [x] 4.2 Verify `AGENTS.md`, `README.md`, `assets/cursor/rules/sdd-spec-first.mdc`, `assets/cursor/rules/sdd-git-traceability.mdc`, and vendor `.cursor/commands/opsx-*` plus `.cursor/skills/openspec-*` files are unchanged
- [x] 4.3 Run `openspec validate add-sdd-scope-control-rule --type change --strict` and resolve any validation issues in the change artifacts
