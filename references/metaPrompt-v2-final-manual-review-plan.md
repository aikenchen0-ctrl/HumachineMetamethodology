# metaPrompt-v2-final-manual-review-plan

## Purpose

This file turns the current reconstructed working tree into a bounded manual-review plan.

It is not another architecture document.

It exists because the repository has already reached practical capability-boundary convergence, and the next high-value action is no longer broad redesign but disciplined review.

## HMM Review Position

Use the following review states:

- `RZ0`
  Raw modified tree, no review order
- `RZ1`
  Review order fixed
- `RZ2`
  High-risk files manually reviewed
- `RZ3`
  Low-risk files spot-checked
- `RZ4`
  Ready for commit-preparation decision

### Current State

Current repository should now be treated as:

- `RZ4`

Reason:

1. Tier A source / shell / contract / release files have been manually reviewed,
2. the boundary stop-rule is already explicit and stable,
3. no remaining high-signal contradiction is currently blocking commit-preparation judgment.

## Current Modified Surface

Current working tree contains:

### Modified Files

- `PORTABLE-PACKAGE-NOTES.md`
- `README.md`
- `SKILL.md`
- `agents/openai.yaml`
- `references/advanced-mode.md`
- `references/core-method.md`
- `references/discovery-and-hypothesis-mode.md`
- `references/governance-and-feedback-mode.md`
- `references/metaPrompt-step-index.json`
- `references/metaPrompt-step-index.md`
- `references/metaPrompt.md`
- `references/opml-architecture-optimization-roadmap.json`
- `references/orchestration-and-memory-mode.md`
- `references/output-and-evaluation.md`
- `references/portfolio-and-optimization-mode.md`
- `references/release-consolidation-checklist.json`
- `references/release-consolidation-checklist.md`
- `references/release-final-review.json`
- `references/release-final-review.md`
- `references/representation-and-serialization-mode.md`
- `references/scope-boundary.md`
- `references/source-alignment-policy.md`
- `references/state-contracts.yaml`
- `references/state-machine.yaml`
- `references/template-mode.md`
- `references/variant-and-composition-mode.md`

### Newly Added Files

- `references/metaPrompt-v2-commit-ready-summary.md`
- `references/metaPrompt-v2-consistency-review.md`
- `references/metaPrompt-v2-consolidation-checklist.md`
- `references/metaPrompt-v2-contract-gap-review.md`
- `references/metaPrompt-v2-final-manual-review-plan.md`
- `references/metaPrompt-v2-reconstruction-plan.md`
- `references/metaPrompt-v2-shell-review.md`
- `references/metaPrompt-v2-third-batch-review.md`
- `references/skill-boundary-commit-preparation-plan.md`
- `references/skill-boundary-convergence-review.md`
- `references/skill-boundary-final-closeout-checklist.md`
- `references/skill-capability-boundary-limit-review.md`
- `references/skill-capability-boundary-review.md`

## Review Goal

The goal is not to reread every line equally.

The goal is to answer four questions:

1. do source, shell, contracts, and release truth tell the same story,
2. is any remaining ambiguity still high-signal,
3. is any file silently reopening a closed boundary,
4. and is the repo ready to move from `Z2` closeout into commit-preparation.

## Latest Review Result

Current review result is:

1. Tier A complete
2. Tier B fast consistency review complete with no high-signal contradiction found
3. Tier B2 optional-extension boundary spot-check complete with no reopen-trigger found
4. Tier C presence / utility check complete enough for commit-preparation judgment
5. `references/state-contracts.yaml` parseability issue has been repaired and revalidated
6. recent optional-extension boundary spot-checks for orchestration / advanced / variant / governance have been completed without reopening broad redesign work
7. later optional-extension spot-checks for template / representation / portfolio have also been completed without reopening broad redesign work
8. current primary decision surface machine checks have reconfirmed JSON / YAML parse success and maintained source hash alignment

## Three Review Tiers

## Tier A: Deep Review Now

These files directly decide source authority, shell compression, and release truth.

Review them line-by-line.

### Source / Shell / Contract Core

- `references/metaPrompt.md`
- `SKILL.md`
- `references/state-machine.yaml`
- `references/state-contracts.yaml`

### Release Truth

- `references/release-consolidation-checklist.md`
- `references/release-consolidation-checklist.json`
- `references/release-final-review.md`
- `references/release-final-review.json`

### Review Questions

1. Do they all agree that `metaPrompt v2` is the maintained source authority?
2. Do they all agree that the six-state shell is runtime compression?
3. Do they all agree that retrieval and pluginization are first-class source layers?
4. Do they all agree that current state is active reconstruction, not release-ready?

## Tier B: Fast Consistency Review

These files are important, but they should only be checked for semantic alignment, not rewritten unless a real conflict appears.

- `references/core-method.md`
- `references/source-alignment-policy.md`
- `references/scope-boundary.md`
- `references/output-and-evaluation.md`
- `references/discovery-and-hypothesis-mode.md`
- `references/advanced-mode.md`
- `README.md`
- `PORTABLE-PACKAGE-NOTES.md`
- `agents/openai.yaml`
- `references/metaPrompt-step-index.md`
- `references/metaPrompt-step-index.json`

### Review Questions

1. Do they still point to the maintained chapter-based source?
2. Do they still respect the default-core / conditional-expansion boundary?
3. Do they contain any old wording that now changes meaning rather than just historical framing?

## Tier B2: Optional Extension Boundary Spot-Check

These files are optional planes, but they have received explicit boundary-tightening passes and should be checked together as one bounded spot-check set rather than as open-ended redesign work.

- `references/orchestration-and-memory-mode.md`
- `references/governance-and-feedback-mode.md`
- `references/template-mode.md`
- `references/representation-and-serialization-mode.md`
- `references/portfolio-and-optimization-mode.md`
- `references/variant-and-composition-mode.md`

### Review Questions

1. Does each file keep its optional plane out of the neutral default core?
2. Does each file make ownership boundaries explicit instead of silently stealing authority from another mode?
3. Does any file reopen runtime/provider/governance or export/ranking/template orchestration scope without a real trigger?
4. If not, stop after the spot-check and defer deeper polishing.

## Tier C: Presence / Utility Check Only

These files should not be deeply edited now unless Tier A or B reveals a real contradiction.

- `references/opml-architecture-optimization-roadmap.json`
- all newly added `metaPrompt-v2-*` review files
- all newly added `skill-*` review files

### Review Questions

1. Are they still useful as review/control surfaces?
2. Do they say anything that contradicts Tier A truth?
3. If not, stop touching them.

## Explicit Review Stop Rule

Stop reviewing deeper when all of the following are true:

1. Tier A files agree on source authority, shell compression, and release truth.
2. Tier B files contain no high-signal semantic contradictions.
3. Tier B2 files contain no high-signal optional-plane boundary contradiction.
4. Tier C files are merely supportive and not contradictory.

When those conditions hold, do not continue editing for style alone.

## Immediate Review Sequence

1. Deep review Tier A source/shell/contract core
2. Deep review Tier A release-truth files
3. Fast review Tier B
4. Spot-check Tier B2 optional extension boundaries
5. Presence check Tier C
6. Decide whether any final cleanup is still justified

## Commit-Preparation Threshold

Move from `RZ1` to `RZ4` only if:

1. Tier A review is complete
2. Tier B and Tier B2 reveal no high-signal contradiction
3. any remaining issues are explicitly downgraded to low-risk or deferred

Current assessment:

- threshold satisfied

## Final Review Residue

At this point, remaining residue is operational rather than analytical:

1. the working tree is still dirty by design
2. grouped commit preparation still needs to be carried out
3. release packaging still remains deferred

No remaining residue currently requires another broad review expansion.

## Current Execution Status

The review plan is no longer only theoretical.

Current execution state:

1. Tier A: complete
2. Tier B: complete
3. Tier B2: complete
4. Tier C: sufficient for commit-preparation judgment
5. current frontier: grouped closeout execution rather than more review expansion

## Final Rule

If a potential edit does not change:

- source authority,
- shell compression meaning,
- default-core boundary,
- conditional expansion boundary,
- or release truth,

then it is not Tier A work and should probably be deferred.
