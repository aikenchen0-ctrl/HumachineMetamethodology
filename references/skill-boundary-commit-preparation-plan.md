# skill-boundary-commit-preparation-plan

## Purpose

This file turns the current boundary-reconstruction outcome into a commit-preparation plan.

It does not decide whether a commit must happen immediately.

It defines:

1. the current closeout state,
2. the safest logical commit grouping,
3. the review gates before committing,
4. and the stop conditions that should delay commit preparation.

## HMM Commit Position

Use this simple state chain:

- `CP0`
  raw reconstruction, not grouped
- `CP1`
  groups identified
- `CP2`
  high-risk group reviewed
- `CP3`
  release-facing truth reviewed
- `CP4`
  commit-ready decision possible

### Current State

Current repository should be treated as:

- `CP4`

Reason:

1. the major reconstruction wave is already bounded,
2. the change surface and logical grouping are known,
3. high-risk source / shell / contract / release surfaces have been reviewed,
4. a commit-ready decision is now possible even though no commit is required yet.

## Commit Grouping Principle

Do not commit this reconstruction as one undifferentiated mass unless there is a compelling reason.

Prefer grouping by semantic dependency:

1. source and typed source
2. shell and contract boundary
3. optional extension boundary tightening
4. release and closeout truth
5. review/control surfaces

## Recommended Commit Groups

## Group A: Maintained Source And Source Interpretation

Purpose:

- establish the new chapter-based source authority

Files:

- `references/metaPrompt.md`
- `references/metaPrompt-step-index.md`
- `references/metaPrompt-step-index.json`
- `references/core-method.md`
- `references/source-alignment-policy.md`
- `references/advanced-mode.md`

Why they belong together:

- they define what the maintained source is and how it should be interpreted

## Group B: Skill Shell And Contract Boundary

Purpose:

- align runtime shell and contract language to the new source without exploding the shell

Files:

- `SKILL.md`
- `references/state-machine.yaml`
- `references/state-contracts.yaml`
- `references/scope-boundary.md`
- `references/output-and-evaluation.md`
- `references/discovery-and-hypothesis-mode.md`

Why they belong together:

- they jointly determine what the skill does by default, what stays conditional, and how the runtime shell compresses the maintained source

## Group C: Entry Surface Sync

Purpose:

- keep public-facing entry surfaces consistent with the new source and shell

Files:

- `README.md`
- `PORTABLE-PACKAGE-NOTES.md`
- `agents/openai.yaml`

Why they belong together:

- they are the external entry surfaces and should not drift from the new core

## Group D: Optional Extension Boundary Tightening

Purpose:

- keep optional planes explicit, bounded, and non-default without promoting them into the neutral core

Files:

- `references/orchestration-and-memory-mode.md`
- `references/governance-and-feedback-mode.md`
- `references/template-mode.md`
- `references/representation-and-serialization-mode.md`
- `references/portfolio-and-optimization-mode.md`
- `references/variant-and-composition-mode.md`

Why they belong together:

- they are not the neutral shell itself,
- but they are the highest-signal optional planes that received explicit boundary-tightening passes during closeout,
- and committing them together makes the optional-plane stop rules auditable.

## Group E: Reconstruction / Boundary Review Surfaces

Purpose:

- preserve the reconstruction reasoning and stop-rule surfaces

Files:

- `references/metaPrompt-v2-reconstruction-plan.md`
- `references/metaPrompt-v2-shell-review.md`
- `references/metaPrompt-v2-contract-gap-review.md`
- `references/metaPrompt-v2-third-batch-review.md`
- `references/metaPrompt-v2-consistency-review.md`
- `references/metaPrompt-v2-consolidation-checklist.md`
- `references/skill-capability-boundary-review.md`
- `references/skill-capability-boundary-limit-review.md`
- `references/skill-boundary-convergence-review.md`
- `references/skill-boundary-final-closeout-checklist.md`
- `references/metaPrompt-v2-final-manual-review-plan.md`
- `references/metaPrompt-v2-commit-ready-summary.md`
- `references/skill-boundary-commit-preparation-plan.md`

Why they belong together:

- they are control surfaces for maintenance, not runtime core semantics

## Group F: Release-Facing Truth

Purpose:

- make release-facing status match actual reconstruction status

Files:

- `references/release-consolidation-checklist.md`
- `references/release-consolidation-checklist.json`
- `references/release-final-review.md`
- `references/release-final-review.json`
- `references/opml-architecture-optimization-roadmap.json`

Why they belong together:

- these files must tell one coherent truth about whether the repo is still reconstructing or is actually ready for release

## Review Gates Before Commit

### Gate 1: Source Authority Gate

Must confirm:

- `references/metaPrompt.md` is clearly the maintained source
- compatibility fields do not outrank chapter authority

### Gate 2: Shell Compression Gate

Must confirm:

- `SKILL.md`
- `state-machine.yaml`
- `state-contracts.yaml`

all agree the six-state shell is runtime compression, not source truth

### Gate 3: Boundary Gate

Must confirm:

- retrieval and pluginization are first-class source layers
- orchestration remains a non-default expansion plane
- no file silently pulls strategy/runtime/UI back into the neutral core

### Gate 4: Release Truth Gate

Must confirm:

- release-facing files still say active reconstruction
- they do not falsely imply packaging readiness

## Latest Gate Status

- Gate 1: passed
- Gate 2: passed
- Gate 3: passed
- Gate 4: passed

## Latest Primary Decision Surface Check

The current closeout execution has already rechecked the primary decision surface:

- Group A
  - `/整合/metaPrompt.md` and `references/metaPrompt.md` still match by hash
- Group B
  - `references/state-machine.yaml` and `references/state-contracts.yaml` parse successfully
  - six-state shell remains explicitly documented as runtime compression
- Group D
  - optional extension boundary-tightening files have been spot-checked without triggering a reopen condition
- Group F
  - release-facing files still state active reconstruction and current dirty working-tree counts

## Stop Conditions For Commit Preparation

Pause commit preparation if any of these is true:

1. a file in Group B still contradicts source authority
2. release-facing files disagree on current reconstruction state
3. a remaining ambiguity still changes core boundary meaning
4. a reviewer cannot tell which group a changed file belongs to

## Good-To-Defer Before Commit

The following should not block commit preparation:

1. minor wording polish
2. low-priority historical references
3. compatibility names that no longer create semantic ambiguity

## Recommended Sequence

1. Review Group A
2. Review Group B
3. Review Group D
4. Review Group F
5. Spot-check Group C
6. Keep Group E as review rationale and maintenance memory
7. Then decide whether to commit in one wave or two

## Commit Strategy Recommendation

Default recommendation:

- broad boundary work should stop here,
- and commit preparation may now proceed once the user wants the history grouped.

Current closeout choice:

- the repository should now move into grouped commit preparation first
- real-task validation should be treated as a later pressure-test branch rather than a blocker for commit grouping

The safest path is:

1. keep Group A + Group B + Group D + Group F as the primary decision surface
2. then decide whether:
   - one consolidated source-alignment commit is acceptable,
   - or three commits are cleaner:
     - source/core alignment
     - optional extension boundary tightening
     - release/review truth alignment

## Current Group Coverage Check

Current `39 = 26 modified + 13 new` working-tree entries now map as follows:

- Group A: maintained source and typed source interpretation
- Group B: shell and contract boundary
- Group C: entry surfaces
- Group D: optional extension boundary tightening
- Group E: review/control surfaces
- Group F: release-facing truth

Current closeout judgment:

- no remaining modified file should be left outside a commit group on purpose
- if a file still appears uncategorized later, treat that as a real stop condition rather than a cosmetic issue

## Final Blocker Set

At the current closeout stage, the remaining blockers are no longer boundary-definition blockers.

They are execution blockers:

1. the working tree is still intentionally dirty
2. grouped commit preparation has been chosen but not yet executed
3. release packaging is still blocked until commit grouping and later consolidation are finished

What is no longer a blocker:

1. source authority ambiguity
2. shell/contract parseability
3. uncategorized changed files
4. high-signal optional-plane ownership drift

## Current Execution Status

Closeout sequence status:

1. step 7 commit grouping: active and materially completed
2. step 8 final commit-preparation review: in progress
3. step 9 exit decision: grouped commit preparation is the current recommended path
4. real-task validation remains a valid follow-up, but it is no longer the default next move for this closeout pass

## Final Conclusion

The repository is close enough to the skill capability boundary limit that commit preparation should now be governed by grouping and review discipline, not by more architecture invention.
