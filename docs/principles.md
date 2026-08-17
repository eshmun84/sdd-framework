# Principles

The SDD Framework is a reusable Spec-Driven Development baseline for professional software projects. These principles govern how this repository is evolved and how consuming projects should treat it.

## Spec-driven lifecycle

Framework changes are specified before they are implemented. OpenSpec owns the change lifecycle, specification artifacts, deltas, archive, and spec synchronization. This repository uses the native `spec-driven` schema and does not redefine OpenSpec command semantics.

## Cursor as execution environment

Cursor is where agents and humans execute the workflow. Commands, skills, rules, and agents run in Cursor. They are not a substitute for specifications, and vendor OpenSpec assets are not SDD Framework-owned methodology.

## Reusable baseline

This repository is methodology and tooling, not a product. It is independent of any business domain, programming language, or application framework. Consuming projects use it as a common engineering baseline; they do not embed it in production runtimes.

## Spec-universe isolation

This repository's OpenSpec workspace specifies the framework. A consuming project's OpenSpec workspace specifies that product. Those universes are never mixed. Product features are not added to `openspec/specs/` here.

## Dual identity

This repository is both the product being evolved (the framework) and a distribution baseline for other repositories. Evolving the framework happens here through OpenSpec. Adopting the framework happens in consuming projects under the [adoption contract](architecture/adoption.md).
