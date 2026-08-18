# sdd-asset-lifecycle-architecture Specification

## Purpose

Defines the SDD Framework asset lifecycle operating model — what a framework-owned asset is, how a need is classified before a file exists, and how those assets are created, validated, published, adopted, maintained, deprecated, and retired — without creating Cursor files or restating primitive, workflow, or adoption operating models.

## Requirements

### Requirement: Asset identity is a framework-owned Cursor primitive
The documented asset lifecycle SHALL describe an SDD Framework asset as a framework-owned Cursor reusable primitive in the `sdd-*` namespace. Supported categories SHALL be rules, skills, agents, and optional thin commands. Source paths SHALL be `assets/cursor/rules/sdd-*`, `assets/cursor/skills/sdd-*`, `assets/cursor/agents/sdd-*`, and `assets/cursor/commands/sdd-*`. Installed paths after copy/pin SHALL be `.cursor/rules/sdd-*`, `.cursor/skills/sdd-*`, `.cursor/agents/sdd-*`, and `.cursor/commands/sdd-*`. The lifecycle SHALL distinguish those assets from documentation, OpenSpec specifications, `AGENTS.md`, prompts, vendor OpenSpec Cursor files, and consuming-project Cursor extensions, without redefining those artifacts. The asset lifecycle SHALL NOT be described as a fifth architecture layer, a workflow engine, an asset-management runtime, a catalog, or a replacement for OpenSpec.

#### Scenario: Operating model names Cursor assets only
- **WHEN** a reader consults the asset-lifecycle architecture documentation
- **THEN** an SDD Framework asset is described as a framework-owned `sdd-*` Cursor primitive
- **AND** the supported categories are rules, skills, agents, and optional thin commands

#### Scenario: Source and installed paths are named
- **WHEN** documentation names where framework assets live
- **THEN** it names `assets/cursor/` as the source tree in this repository
- **AND** it names project-root `.cursor/` as the installed Cursor load path after copy/pin

#### Scenario: Non-assets are excluded
- **WHEN** documentation describes what is not an SDD Framework asset
- **THEN** it states that documentation, OpenSpec specifications, `AGENTS.md`, prompts, vendor `opsx-*` / `openspec-*` files, and consuming-project Cursor extensions are not framework assets

#### Scenario: Lifecycle is not a layer or engine
- **WHEN** documentation describes what the asset lifecycle is not
- **THEN** it states that the lifecycle is not a fifth architecture layer, a workflow engine, an asset-management runtime, a catalog, or a replacement for OpenSpec

### Requirement: Optional commands are dependent assets
A framework-owned command SHALL exist only as an optional thin trigger for a canonical skill and SHALL share that skill's `sdd-*` name. A command SHALL NOT be proposed or implemented without that skill. Deprecation or retirement of a skill SHALL include its optional command. Type meaning of commands SHALL remain defined by the Cursor component constitution; this capability SHALL NOT reopen that constitution.

#### Scenario: Command requires a skill
- **WHEN** a contributor plans a framework-owned command
- **THEN** documentation requires an existing or same-change `sdd-*` skill as the canonical procedure
- **AND** it forbids proposing a command as a standalone asset

#### Scenario: Command follows the skill through retirement
- **WHEN** a framework-owned skill with an optional command is deprecated or retired
- **THEN** documentation requires the command to be deprecated or retired with that skill
- **AND** it does not allow the command to remain after the skill is removed

### Requirement: Classification happens before asset creation
Before a framework-owned Cursor asset is created, the documented lifecycle SHALL require classification of the need. Classification SHALL apply to framework work; product, domain, or stack needs SHALL remain consuming-project assets outside reserved prefixes. Classification SHALL ask, in this order, whether the need is a session-only prompt, methodology documentation, a specification requirement, repository identity or navigation, a vendor OpenSpec lifecycle operation, a rule, a skill, an agent, or an optional command. Classification SHALL stop at the first home that fits. The cheapest valid home SHALL win. Type-specific tests for rules, skills, agents, and commands SHALL remain defined by the existing operating models and constitution; this capability SHALL NOT restate those tests in full.

#### Scenario: Classification can exit without an asset
- **WHEN** a need is classified as a prompt, documentation, OpenSpec specification, `AGENTS.md` content, or vendor OpenSpec lifecycle work
- **THEN** the documented model does not classify that need as a framework Cursor asset
- **AND** it does not require creating an `sdd-*` file

#### Scenario: Product work is not a framework asset
- **WHEN** a need is product, domain, or stack behavior
- **THEN** documentation classifies it as consuming-project work
- **AND** it forbids naming that work as an `sdd-*` asset

#### Scenario: Requirement is not left as documentation or as an asset
- **WHEN** a need is behavior the framework must guarantee
- **THEN** the documented model classifies it as an OpenSpec specification
- **AND** it does not classify that requirement as documentation alone or as a Cursor asset that replaces the specification

#### Scenario: Cheapest Cursor primitive wins
- **WHEN** a classified framework need could fit more than one Cursor primitive
- **THEN** documentation requires the cheapest valid primitive
- **AND** it forbids creating a heavier primitive when a cheaper one fits

#### Scenario: OpenSpec lifecycle is not wrapped as an sdd asset
- **WHEN** a contributor plans a framework-owned asset whose purpose is explore, propose, apply, update, sync, or archive
- **THEN** documentation forbids creating that asset
- **AND** it directs the contributor to the vendor `opsx-*` / `openspec-*` surface

### Requirement: Creation requires evidence and an approved change
A framework-owned asset SHALL be created only when all of the following are true: the need is reusable methodology with framework-wide applicability; the asset remains valid after copy/pin into a consuming project; the behavior is stable rather than exploratory; evidence of repetition exists; the classified primitive is correct using the existing type operating models; and a human has accepted an OpenSpec change in this repository as the contract. Evidence of repetition SHALL be recorded in that change's proposal. A hypothetical or one-time need SHALL NOT justify an asset. Absence of `sdd-*` files SHALL remain valid. Empty stubs SHALL NOT be treated as a catalog.

#### Scenario: Repeated stable methodology meets the bar
- **WHEN** a contributor records more than one occurrence of a copy-valid, stable, framework-wide procedure, constraint, or specialist stance, and the cheapest primitive is a Cursor asset
- **THEN** the documented model allows proposing that asset through OpenSpec
- **AND** it requires the proposal to record the type justification and the repetition evidence

#### Scenario: Hypothetical need is rejected
- **WHEN** a contributor wants a framework asset because it might be useful later
- **THEN** documentation forbids creating that asset
- **AND** it directs the need to remain a prompt, documentation, or later proposal until repetition is observed

#### Scenario: Premature catalog is rejected
- **WHEN** a change would add empty `sdd-*` stubs or a catalog so adoption has files to copy
- **THEN** documentation forbids those files
- **AND** it states that absence of framework-owned Cursor assets remains valid

#### Scenario: Unapproved implementation is rejected
- **WHEN** a prompt asks to add an `sdd-*` Cursor file with no approved OpenSpec change
- **THEN** the documented lifecycle classifies that request as incorrect
- **AND** it directs the work to propose rather than treating the prompt as permission to create the asset

### Requirement: Lifecycle stages are conceptual not commands
The documented lifecycle SHALL describe conceptual stages: need, classify, propose, implement, validate, publish, adopt, maintain, deprecate, and retire. Those stages SHALL NOT be presented as a mandatory command sequence or as new Cursor commands. The framework SHALL NOT introduce `/sdd-publish`, `/sdd-validate`, `/sdd-retire`, or any `sdd-*` command or skill whose purpose is to own this lifecycle. Mutation of assets SHALL use the existing OpenSpec change lifecycle. Collaboration stages SHALL remain defined by the workflow operating model; this capability SHALL NOT restate that model.

#### Scenario: Stages are named as concepts
- **WHEN** a reader consults the asset lifecycle
- **THEN** need, classify, propose, implement, validate, publish, adopt, maintain, deprecate, and retire are named
- **AND** they are described as conceptual stages rather than vendor or framework commands

#### Scenario: No lifecycle commands are added
- **WHEN** a contributor looks for `/sdd-publish`, `/sdd-validate`, or `/sdd-retire`
- **THEN** documentation states that those commands MUST NOT be created
- **AND** it directs validation to the existing review stage and mutation to OpenSpec

### Requirement: Stage boundaries define start, end, and durable output
The documented lifecycle SHALL state when each conceptual stage begins and ends and what durable output, if any, that stage produces. Need SHALL begin with an observed pattern and MAY produce no durable artifacts. Classify SHALL end when a home is chosen or the need is discarded. Propose SHALL produce human-accepted OpenSpec artifacts that record type justification. Implement SHALL write the asset only for an approved change, and that durable output SHALL be the source file under `assets/cursor/`. Validate SHALL judge the implementation against that contract. Publish SHALL mean the archived asset is eligible for the published baseline subset from the source tree. Adopt and subsequent updates SHALL follow the existing copy/pin adoption contract from source to installed path. Maintain SHALL be a new OpenSpec change. Deprecate SHALL mark the asset while it remains available. Retire SHALL remove it from the published subset.

#### Scenario: Need may produce nothing durable
- **WHEN** a repeated pattern is observed but not yet classified as framework asset work
- **THEN** documentation allows that observation to remain session-only
- **AND** it does not require an OpenSpec change from observation alone

#### Scenario: Implement follows an approved contract
- **WHEN** documentation describes implementing a framework asset
- **THEN** it states that implement begins only after a human has accepted the OpenSpec change as the contract
- **AND** it forbids writing the Cursor file from classification or chat history alone
- **AND** it states that the durable implement output is the source file under `assets/cursor/`

#### Scenario: Publish is eligibility after archive
- **WHEN** documentation describes publication
- **THEN** it states that an archived asset in the published inventory paths under `assets/cursor/` is eligible for copy/pin
- **AND** it does not require git tags, releases, or publication tooling to exist for this capability

### Requirement: Humans own lifecycle decisions; Cursor executes; OpenSpec mutates
The documented lifecycle SHALL assign classification approval, creation approval, adoption decisions, and retirement decisions to the human. It SHALL assign execution of assets to Cursor. It SHALL assign mutation history and requirements to OpenSpec. This repository SHALL own source `sdd-*` assets, framework OpenSpec changes, and methodology evolution. Consuming projects SHALL receive approved baseline assets, SHALL NOT modify `sdd-*` assets in place, SHALL own project-specific extensions outside reserved prefixes, and SHALL return reusable improvements through this repository's OpenSpec lifecycle. Cursor SHALL NOT own lifecycle decisions.

#### Scenario: Human owns creation and retirement
- **WHEN** a reader consults lifecycle ownership
- **THEN** the human is described as approving classification, creation, adoption, and retirement
- **AND** Cursor is not described as the owner of those decisions

#### Scenario: Framework owns source assets
- **WHEN** documentation assigns asset ownership
- **THEN** this repository is described as the source of truth for `sdd-*` files
- **AND** OpenSpec is described as owning the mutation history and requirements

#### Scenario: Consuming projects do not fork sdd assets
- **WHEN** a consuming project has copied framework `sdd-*` assets
- **THEN** documentation forbids modifying those files in place
- **AND** it requires reusable improvements to be proposed in this repository

### Requirement: Validation is review against the contract
Validation of a framework asset SHALL be the existing review collaboration stage judging implementation against the approved OpenSpec change. Validation SHALL include type justification, file-contract fit, cheapest-primitive fit, copy-validity after adoption, absence of hidden specifications, absence of documentation dumps, and absence of OpenSpec wrappers. Validation SHALL NOT be a new command. Findings SHALL NOT invent a second acceptance list.

#### Scenario: Validation uses existing review
- **WHEN** a framework asset implementation is claimed done
- **THEN** documentation requires review against the approved change
- **AND** it forbids creating a `/sdd-validate` command

#### Scenario: Copy-validity is checked
- **WHEN** a planned `sdd-*` asset is validated
- **THEN** documentation requires that the asset remain correct after copy/pin, including methodology pointers that land at `docs/sdd-framework/` in a consuming project
- **AND** it forbids publishing an asset that is true only inside this repository

#### Scenario: Hidden specification is rejected
- **WHEN** a planned asset would introduce framework behavior that is not already specified
- **THEN** the documented model forbids publishing that asset
- **AND** it requires the behavior to be specified in OpenSpec before any later asset may execute or remind of it

### Requirement: Assets version with the framework baseline
Framework assets SHALL be versioned through the existing versioned baseline, whose primary identifier is a git tag. The lifecycle SHALL NOT introduce per-asset versions, a version catalog, manifests, sync tools, or release automation. An additive asset SHALL appear in consuming projects on the next baseline update. A compatible change SHALL replace the copied file on that update. A breaking change — meaning change, rename, or removal — SHALL use deprecation before retirement when the asset has been eligible for the published subset. Partial updates that keep some copied `sdd-*` files while replacing others SHALL NOT be the model.

#### Scenario: No per-asset version system
- **WHEN** a reader looks for a version identifier on an individual skill, rule, agent, or command
- **THEN** documentation states that assets ride the framework baseline version
- **AND** it does not require a per-asset version, manifest, or release tool

#### Scenario: Projects receive assets by whole-subset update
- **WHEN** a consuming project updates to a newer framework baseline
- **THEN** documentation describes replacement of framework-owned copied assets as already specified by adoption
- **AND** it does not describe selecting individual assets to skip

### Requirement: Adoption distributes published assets without changing copy/pin
After publication, consuming projects SHALL receive framework assets through the existing versioned copy/pin adoption contract. Copy/pin SHALL copy FROM `assets/cursor/**/sdd-*` TO the consuming project's project-root `.cursor/**/sdd-*`. Copied `sdd-*` assets SHALL remain framework-owned. The asset lifecycle SHALL use that contract and SHALL NOT restate landing paths, never-transfer inventory, vendor OpenSpec exclusion, or installer deferral. A project-named Cursor extension that encodes reusable methodology MAY be proposed as a framework asset in this repository; that local file SHALL be evidence, not an in-place rename to `sdd-*`.

#### Scenario: Adoption path is unchanged
- **WHEN** documentation describes how a consuming project receives a new framework asset
- **THEN** it describes copy/pin of the published subset from the source tree into the consuming project's Cursor load path
- **AND** it does not introduce a new distribution model such as submodule, package, installer, or OpenSpec store

#### Scenario: Project extension is evidence for promotion
- **WHEN** a consuming project has a useful non-`sdd-*` Cursor asset that is reusable methodology
- **THEN** documentation allows proposing a framework `sdd-*` asset in this repository using that project file as evidence
- **AND** it forbids renaming the project file in place to an `sdd-*` name

### Requirement: Deprecation precedes retirement; silent deletion is forbidden
Creating, changing, deprecating, or retiring a framework-owned asset SHALL require an OpenSpec change in this repository. Silent addition, in-place product overwrite, or undocumented deletion SHALL NOT be permitted. A deprecated asset SHALL remain in the published subset during a transition and SHALL be marked so new work does not use it. Retirement SHALL be explicit removal from the published subset by a later OpenSpec change. This capability SHALL NOT define a release calendar or a numeric waiting period. An asset that was never eligible for the published subset MAY be removed by an OpenSpec change without a prior deprecation period.

#### Scenario: Deprecation needs a change and keeps the file
- **WHEN** a published framework asset is withdrawn or replaced
- **THEN** documentation requires an OpenSpec change that deprecates the asset
- **AND** it requires the file to remain available in the published subset during the transition
- **AND** it does not permit silent deletion as the deprecation path

#### Scenario: Retirement is explicit later removal
- **WHEN** a deprecated asset's transition is complete
- **THEN** documentation requires a distinct OpenSpec change that removes the asset from the published subset
- **AND** a consuming project's next baseline update drops that file as part of replacement of framework-owned copied assets

#### Scenario: Never-published removal still uses OpenSpec
- **WHEN** a framework asset was created and withdrawn before it was eligible for the published subset
- **THEN** documentation allows removal without a prior deprecation period
- **AND** it still requires an OpenSpec change and forbids silent deletion

### Requirement: Operating model without catalog implementation
This capability SHALL define the asset lifecycle without requiring any framework-owned `sdd-*` rule, skill, command, or agent file to exist. It SHALL NOT introduce an installer, synchronization tool, manifest file, release automation, workflow engine, asset-management runtime, MCP integration, hook, plugin, template catalog, example assets, or a planned-name catalog. Empty stubs SHALL NOT be a catalog. Later creation of framework-owned Cursor assets SHALL use per-asset OpenSpec changes that follow this lifecycle. This capability SHALL NOT require a catalog change.

#### Scenario: Architecture change adds no Cursor catalog
- **WHEN** this change is applied
- **THEN** no `sdd-*` Cursor rules, skills, commands, or agents are required to exist
- **AND** the documented lifecycle is sufficient for later per-asset OpenSpec changes to add them
- **AND** it does not require a catalog document or planned-name inventory

#### Scenario: No tooling or engine is specified
- **WHEN** a contributor looks for an installer, manifest, release tool, workflow engine, or asset-management runtime in this change
- **THEN** documentation states that those are out of scope
- **AND** it states that humans invoke OpenSpec stages and Cursor executes assets

### Requirement: Published baseline may contain zero Cursor assets
The documented asset lifecycle SHALL state that a published framework baseline MAY contain zero framework-owned `sdd-*` Cursor files. Publication of a baseline SHALL NOT require any `sdd-*` rule, skill, command, or agent to exist. The methodology, architecture, and OpenSpec governance SHALL remain sufficient as the published baseline when those Cursor files are absent.

#### Scenario: Empty Cursor subset is a published baseline
- **WHEN** a reader consults how a framework baseline is published
- **THEN** documentation states that the published baseline may contain zero `sdd-*` Cursor files
- **AND** it does not require Cursor assets to exist in order to publish

#### Scenario: Methodology-only baseline is sufficient
- **WHEN** the repository has complete methodology, architecture, and OpenSpec governance and no `sdd-*` Cursor files
- **THEN** documentation describes that state as a valid published baseline
- **AND** it does not describe Cursor assets as missing pieces of that baseline

### Requirement: Absence of Cursor assets is not incompleteness
The documented asset lifecycle SHALL state that absence of framework-owned `sdd-*` files is not an incomplete implementation of the framework. A contributor SHALL NOT treat empty `assets/cursor/` `sdd-*` paths as unfinished foundation work.

#### Scenario: Empty sdd paths are not a defect
- **WHEN** a contributor inspects the repository and finds no `sdd-*` Cursor files in the source tree
- **THEN** documentation classifies that absence as a valid complete state
- **AND** it forbids treating that absence as an implementation gap that must be filled to complete the framework

### Requirement: No planned asset catalog
The documented asset lifecycle SHALL forbid a planned-name catalog, future-asset inventory, or catalog document that lists `sdd-*` assets to create. The published inventory SHALL remain the path patterns of files that exist under `assets/cursor/` plus the adoption path patterns. This capability SHALL NOT introduce a catalog page, a backlog of asset names, or empty stubs so that a catalog appears populated.

#### Scenario: Planned-name inventory is rejected
- **WHEN** a contributor plans a document or change whose purpose is to list future `sdd-*` names to implement
- **THEN** documentation forbids that inventory
- **AND** it states that no planned asset catalog exists

#### Scenario: Existing files remain the inventory
- **WHEN** a reader looks for the current set of framework-owned Cursor assets
- **THEN** documentation directs them to existing `assets/cursor/**/sdd-*` files and the adoption path patterns
- **AND** it does not provide a separate catalog of intended names
- **AND** it does not direct them to this repository's `.cursor/**/sdd-*` as the published inventory

### Requirement: Example names are not creation intent
When architecture documentation uses `sdd-*` names as examples, those names SHALL be non-normative illustrations of naming shape. They SHALL NOT be described as assets to create, as a backlog, or as publication intent.

#### Scenario: Example name is not a work item
- **WHEN** a reader encounters an example such as a sample `sdd-*` skill, rule, or agent name in architecture documentation
- **THEN** documentation labels that name as a non-normative example
- **AND** it does not present that name as an asset the framework intends to create

### Requirement: Future assets are individual OpenSpec changes
Each framework-owned Cursor asset that is later created SHALL be justified by its own OpenSpec change that follows this lifecycle, including classification, evidence of repetition, and human acceptance. One change MAY create a skill and its optional command. A change SHALL NOT create a catalog of assets. This capability SHALL NOT change classification order, creation criteria, stages, ownership, validation, versioning, deprecation, or retirement already specified by this architecture.

#### Scenario: First asset is a per-asset change
- **WHEN** a contributor wants the first `sdd-*` Cursor file to exist
- **THEN** documentation requires a dedicated OpenSpec change for that asset that follows this lifecycle
- **AND** it forbids bundling a catalog of unrelated assets into that change

#### Scenario: Lifecycle model stays unchanged
- **WHEN** this publication policy is applied
- **THEN** classification, creation evidence, conceptual stages, ownership, validation, versioning, deprecation, and retirement remain as already specified
- **AND** documentation does not introduce a new lifecycle stage for catalogs

### Requirement: Source tree is the published inventory home
Implement of a framework-owned Cursor asset SHALL write the file under `assets/cursor/` in the primitive-matched source path. Publish SHALL mean the archived asset is eligible for copy/pin from that source tree. This repository SHALL NOT install published `sdd-*` files into its own `.cursor/` tree. Cursor SHALL execute assets only after they are installed under `.cursor/` in a repository that adopted them. A primitive directory under `assets/cursor/` SHALL be created only when a published file of that primitive exists.

#### Scenario: Implement writes the source path
- **WHEN** documentation describes implementing a framework-owned Cursor asset
- **THEN** it requires the file to be written under `assets/cursor/` in the matching primitive path
- **AND** it forbids treating this repository's `.cursor/` as the published source

#### Scenario: This repository does not self-install the subset
- **WHEN** a published `sdd-*` asset exists in the source tree
- **THEN** documentation does not require a copy, symlink, or dual-commit of that asset under this repository's `.cursor/`
- **AND** it states that consuming projects receive the file through copy/pin into their `.cursor/` tree
