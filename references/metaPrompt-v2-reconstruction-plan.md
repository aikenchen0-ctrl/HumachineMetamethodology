# metaPrompt-v2-reconstruction-plan

## Purpose

This file records the repository-side reconstruction plan after the maintained source moved to the chapter-based `metaPrompt v2`.

The goal is not only to copy the new source file into `references/`, but to progressively realign:

- source references,
- typed source companions,
- skill entry points,
- contracts,
- and later the runtime-facing skill shell.

## HMM-Style Maintenance States

### `P0` Source Drift Detected

The maintained source in `/整合/metaPrompt.md` has diverged from the repo-side `references/metaPrompt.md`.

### `P1` Source And Index Sync

The repo-side source file plus its typed companion files are synchronized to the new maintained scaffold.

### `P2` Skill Entry Sync

`README.md`, `SKILL.md`, `agents/openai.yaml`, and close entry references no longer talk as if the source were still the old `步骤1-步骤8` draft.

### `P3` Contract Sync

`state-machine.yaml`, `state-contracts.yaml`, and nearby policy files interpret the new source correctly enough to avoid source-alignment drift.

### `P4` Shell Refactor

The runtime-facing skill shell itself is updated where necessary to reflect the maintained chapter-based source without losing the useful MVP compression.

### `P5` Consolidation And Commit Preparation

After source, entry, contract, and shell alignment are stable, the repository moves into:

- consolidation review,
- commit grouping,
- release-truth synchronization,
- and real-task validation.

## Current Status

Current repository status should be treated as:

- `P1` completed
- `P2` completed
- `P3` completed
- `P4` completed as bounded compression rather than shell explosion
- `P5` active

More concretely:

- repo-side `references/metaPrompt.md` has already been replaced by the maintained chapter-based `metaPrompt v2`
- typed companion files now point to chapter order instead of the old linear step draft
- `README.md`, `SKILL.md`, `agents/openai.yaml`, and key source-alignment references now acknowledge the new source scaffold
- `state-machine.yaml` and `state-contracts.yaml` now explicitly interpret the six-state shell as runtime compression of the maintained source
- release-facing files now state active reconstruction rather than false release readiness
- the current frontier is no longer source replacement, but controlled consolidation

## Batch Strategy

### Batch 1

- sync `references/metaPrompt.md`
- sync `references/metaPrompt-step-index.md`
- sync `references/metaPrompt-step-index.json`
- update `references/core-method.md`
- update `references/source-alignment-policy.md`
- update `references/advanced-mode.md`

Status:

- completed

### Batch 2

- update `README.md`
- update `SKILL.md`
- update `agents/openai.yaml`
- patch explicit old step references in contracts

Status:

- completed for entry files
- completed for the most explicit old-step contract triggers
- not yet a full contract reinterpretation

### Batch 3

- inspect whether `state-machine.yaml` and `state-contracts.yaml` still compress the new source correctly
- decide what should remain as MVP shell compression
- decide what should be promoted into explicit chapter-aware contracts

Status:

- completed

Current risk:

- the shell is still expressed in the old six-state runtime compression
- this is acceptable only because it is now explicitly documented as “compression versus source chapter” rather than silent inheritance

### Batch 4

- decide whether to update remaining reference assets that still implicitly assume the old source order
- prepare repository-side validation and packaging notes

Candidate files for this batch currently include:

- `references/scope-boundary.md`
- `references/output-and-evaluation.md`
- `references/discovery-and-hypothesis-mode.md`
- `references/orchestration-and-memory-mode.md`
- `references/release-consolidation-checklist.*`

These files are not necessarily broken, but they still need a pass to confirm they are speaking about the maintained source rather than the historical draft.

Status:

- high-signal files completed
- `references/orchestration-and-memory-mode.md` has received a boundary-guard tightening pass; further elaboration remains deferred unless real operational scope appears
- low-priority residue deferred unless a real contradiction appears

## Current Decision Rule

Do not widen into full runtime/provider/governance refactors while source alignment is still active.

Prefer:

1. source sync
2. entry sync
3. contract sync
4. only then shell refactor

Also:

5. only after shell refactor should remaining low-priority references be mass-updated

## Current HMM View

The repository-side reconstruction is best read as:

- `P0` cleared
- `P1` cleared
- `P2` cleared
- `P3` cleared
- `P4` cleared in bounded form
- `P5` active

That means the current frontier is no longer “copy the new source into the repo”.

The current frontier is:

- keeping source / shell / contract / release truth synchronized,
- grouping the current change surface for commit preparation,
- and validating the aligned structure against real tasks rather than widening architecture again.

## Next Action

After the current source-alignment wave, the next safe actions are:

1. keep `/整合/metaPrompt.md` and `references/metaPrompt.md` hash-aligned
2. preserve the six-state shell as explicit runtime compression instead of expanding it blindly
3. treat release-facing truth and commit grouping as the current maintenance foreground
4. use real tasks to pressure-test retrieval, generation, evaluation, and pluginization writeback
5. reopen broad boundary work only if real downstream pressure or source drift appears
