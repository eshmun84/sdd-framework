# Working agreements

This document is the authoritative governance for changing the SDD Framework. Root entrypoints point here; they do not reproduce these agreements in full.

## What may change here

This repository specifies and implements the SDD Framework: methodology, governance, documentation, Cursor/OpenSpec tooling assets, and the adoption contract.

It does not specify consuming-project products, business domains, or application features. Those belong in the consuming project's OpenSpec workspace.

## How a framework change is specified

1. Explore if the problem or design is still open (`/opsx-explore`).
2. Propose a change with the native OpenSpec `spec-driven` artifacts (`/opsx-propose`): proposal, capability specs, design when architecture decisions are needed, and tasks.
3. Keep scope inside the framework. Every proposal includes non-goals. Product requirements for other repositories are out of scope.
4. Do not bypass OpenSpec. Do not implement framework behavior that has no change artifacts.

`openspec/config.yaml` carries repository context and artifact rules so later proposals inherit this identity.

## How a framework change is implemented

1. Apply only the approved tasks (`/opsx-apply`).
2. Keep vendor `opsx-*` / `openspec-*` Cursor assets unchanged unless a dedicated change requires otherwise.
3. Put framework-owned Cursor behavior in a future `sdd-*` namespace; do not mix it into vendor files.
4. Do not add application code, installers, or custom OpenSpec schemas unless a dedicated change specifies them.

## How a framework change is archived

1. Complete (or explicitly accept incomplete) planning artifacts and tasks.
2. Sync delta specs into `openspec/specs/` so main specs remain the durable contract (`/opsx-sync` or archive-time sync).
3. Archive the change (`/opsx-archive`).

After archive, `openspec/specs/` is the requirement source of truth for the framework. `docs/` remains the readable methodology. If they diverge, update them through a new OpenSpec change rather than editing only one side ad hoc.

## Review expectation

A foundation-scale or boundary-changing proposal should be reviewable as one coherent change: identity, docs, ownership, and adoption stay aligned. Prefer a new change over expanding an in-flight change past its non-goals.
