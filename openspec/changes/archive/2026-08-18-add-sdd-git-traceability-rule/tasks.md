## 1. Document Git ↔ OpenSpec traceability in the workflow page

- [x] 1.1 Add a Git ↔ OpenSpec traceability section to `docs/architecture/workflow-system.md` that describes Git as the history of landed change work, keeps OpenSpec as the requirement contract, requires change-related Git work to be attributable to the current repository's OpenSpec change, and forbids mixing distinct OpenSpec changes in one commit
- [x] 1.2 Verify that section does not add a fifth architecture layer, a new documentation page, Conventional Commits, commit-message grammar, branching, hooks, Git tooling, or Git procedure (staging, rebase, squash, push, pull request), and does not require every commit to reference an OpenSpec change

## 2. Create the Git traceability rule

- [x] 2.1 Create `assets/cursor/rules/sdd-git-traceability.mdc` with YAML frontmatter that includes `description` and `alwaysApply: true`, and that does not include `globs` or description-only activation
- [x] 2.2 Write the rule body as the operational must-not: Git work associated with an OpenSpec change in this repository's OpenSpec workspace must be attributable to that change; a single commit must not mix work from different OpenSpec changes; Git history is not the specification; propose, apply, sync, and archive commits for a change are allowed when attributable
- [x] 2.3 Add copy-valid methodology pointers by page title that name both documentation roots (`docs/` here, `docs/sdd-framework/` after copy/pin). Do not paste the workflow page or Spec First into the file

## 3. Validate the rule file

- [x] 3.1 Verify the constraint is scoped to the current project's OpenSpec workspace and Git history, remains true if OpenSpec is not initialized yet (Git is still not the spec), and does not encode this repository's "not a product" identity or a ban on product specifications
- [x] 3.2 Verify the file does not wrap, rename, or sequence vendor `/opsx-*` or `openspec-*` assets, and does not include staging, rebase, squash, amend, push, pull-request, or commit-message-grammar steps
- [x] 3.3 Verify the file is one concern, does not invoke other rules, does not require every commit to name a change, and does not introduce Git conventions that are not in this change's specifications

## 4. Boundary verification

- [x] 4.1 Verify this change did not add any other `sdd-*` rule, skill, agent, or command, including empty stubs, and did not install `sdd-git-traceability.mdc` under this repository's `.cursor/`
- [x] 4.2 Verify `AGENTS.md`, `README.md`, `assets/cursor/rules/sdd-spec-first.mdc`, and vendor `.cursor/commands/opsx-*` plus `.cursor/skills/openspec-*` files are unchanged
- [x] 4.3 Run `openspec validate add-sdd-git-traceability-rule --type change --strict` and resolve any validation issues in the change artifacts
