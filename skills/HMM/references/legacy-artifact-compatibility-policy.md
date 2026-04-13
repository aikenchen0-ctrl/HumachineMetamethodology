# legacy-artifact-compatibility-policy

## Purpose

This file defines how to decide whether a source-derived concrete artifact name should stay:

- an active contract,
- a compatibility artifact,
- or an archived reference.

It exists because the OPML often names concrete files directly, while the current skill prefers semantic artifacts over historical filenames.

## Core Rule

Do not preserve a historical artifact filename as an active contract just because it once existed in the source.

Preserve it as an active contract only when:

- a current downstream consumer really needs that exact filename or identity,
- the filename still carries unique semantics that no current contract already absorbs,
- and the compatibility cost of removing it is higher than the complexity cost of keeping it.

Otherwise:

- keep the semantic successor active,
- and archive the historical filename as a reference.

## Artifact Classes

### 1. Active Semantic Successor

Use when:

- the semantic function survives,
- but the exact old filename is no longer required.

Example:

- `problem-brief.json`
  may absorb the semantic role once imagined for an initial prompt artifact.

### 2. Compatibility Artifact

Use when:

- an external workflow,
- preserved downstream consumer,
- or migration boundary

still needs the old artifact identity.

Compatibility artifacts are not default core contracts.
They exist only because a concrete consumer still depends on them.

### 3. Archived Reference

Use when:

- the source node is historically useful,
- but its concrete artifact identity is no longer required by the current architecture.

Archive status preserves traceability without forcing the old file back into the active workflow.

## Decision Tests

Ask in order:

1. Does a current downstream consumer require this exact artifact identity?
2. Does the artifact still carry unique semantics not already absorbed by a current contract?
3. Would reviving it improve clarity more than it increases duplication?
4. If not, is its remaining value historical, explanatory, or compatibility-only?

If the answers are:

- `no / no / no / yes`
  then archive it.
- `yes / maybe / yes / yes`
  then keep it only as an explicit compatibility artifact.

## Current Source-Aligned Decision

### `create_initial_prompt.md`

Current decision:

- do not keep it as an active default contract
- keep its semantic successor in active core artifacts
- archive the concrete filename unless a real compatibility requirement appears later

Why:

- the architecture already keeps the core semantic role through structured intake and problem brief artifacts,
- but no current contract requires this exact markdown filename as a default cross-round surface.

## Reactivation Gate

Only revive an archived historical artifact if:

- a real external consumer,
- a preserved legacy workflow,
- or an explicit compatibility test

requires that exact artifact identity.
