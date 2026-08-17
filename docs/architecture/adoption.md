# Project adoption

This document is the authoritative adoption contract. It is architectural. No installer or synchronization mechanism is implemented in this foundation.

## What consuming projects own

A consuming project retains ownership of:

- product requirements
- application architecture
- business domain
- source code
- its own OpenSpec lifecycle and specifications
- project-specific Cursor extensions

Product behavior is recorded in the consuming project's OpenSpec workspace. It is not recorded in this repository's OpenSpec specifications.

Project-local Cursor extensions stay in the consuming project. They become part of the SDD Framework only if promoted through this repository's OpenSpec lifecycle.

## Versioned Cursor-context baseline

Consuming projects will eventually **install or synchronize a versioned set of framework assets into their Cursor project context**.

That set is an engineering workflow baseline (documentation pointers, vendor OpenSpec Cursor assets, and later `sdd-*` assets). It is not a runtime library, service, or production dependency.

The installer or synchronization mechanism is a **future change**. Until then, this contract is the source of truth for later implementation.

## Runtime and production decoupling

The SDD Framework is not coupled to a consuming project's runtime application or production deployment.

Adoption affects specification practice and Cursor-assisted development. It does not ship inside production executables, services, or runtime configuration.

## What this repository does not do

- It does not host consuming-project product specifications.
- It does not require a bootstrap CLI in this foundation.
- It does not use Git submodules or OpenSpec stores as the Cursor-asset distribution model. An OpenSpec store may be considered later for spec referencing, not as a substitute for this contract.
