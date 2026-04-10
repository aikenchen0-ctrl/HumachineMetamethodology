# metaPrompt-v2-consolidation-checklist

## Purpose

This file turns the current reconstruction state into a controlled consolidation checklist.

It exists because the repository is no longer in “open architecture expansion”.

It is now in:

- source-aligned reconstruction already mostly complete,
- boundary review already largely stabilized,
- and broad capability-boundary expansion already at a practical stop point.

So the next question is no longer:

- what else could be redesigned?

It is:

- what still must be cleaned up now,
- what can safely wait,
- and what work should explicitly stop.

## Current HMM Consolidation State

Use this small consolidation state chain:

### `L0` Open Reconstruction

- source and shell are still drifting

### `L1` Aligned But Unsettled

- source is aligned, but key boundary and contract conflicts remain

### `L2` Consolidation Ready

- source, boundary, contract, and shell are broadly aligned
- remaining work is mostly cleanup and release-facing truth maintenance

### `L3` Commit / Packaging Gate

- only final sanity checks and release/commit decisions remain

### Current State

Current repository is best read as:

- `L2`

Reason:

1. source-aligned reconstruction is already broad and real
2. boundary work is no longer on the critical path
3. remaining work is mostly cleanup, explicit review, and release-truth synchronization

## Current Change Surface

Current modified / new areas are concentrated in:

### Source And Core References

- `references/metaPrompt.md`
- `references/core-method.md`
- `references/source-alignment-policy.md`
- `references/advanced-mode.md`

### Typed Companion And Source Indexing

- `references/metaPrompt-step-index.md`
- `references/metaPrompt-step-index.json`

### Skill Entry And Public Surface

- `SKILL.md`
- `README.md`
- `agents/openai.yaml`
- `PORTABLE-PACKAGE-NOTES.md`

### Boundary / Contract / Review

- `references/scope-boundary.md`
- `references/state-machine.yaml`
- `references/state-contracts.yaml`
- `references/output-and-evaluation.md`
- `references/discovery-and-hypothesis-mode.md`
- release review artifacts
- newly added review and reconstruction notes

## Must-Do Now

These are the highest-value remaining items before any commit or packaging decision.

### 1. Ensure release-facing truth is internally consistent

Check these together:

- `references/release-consolidation-checklist.md`
- `references/release-consolidation-checklist.json`
- `references/release-final-review.md`
- `references/release-final-review.json`

Goal:

- they should all tell the same truth:
  - active reconstruction,
  - not release-ready,
  - source copies aligned,
  - packaging intentionally deferred.

### 2. Ensure `SKILL.md` and shell contracts tell the same boundary story

Check these together:

- `SKILL.md`
- `references/state-machine.yaml`
- `references/state-contracts.yaml`
- `references/skill-capability-boundary-review.md`
- `references/skill-capability-boundary-limit-review.md`

Goal:

- default core
- first-class conditional layers
- optional extension planes
- out-of-core planes

must all be described consistently.

### 3. Remove only high-signal residual naming conflicts

Examples:

- authority fields still phrased as if the old linear scaffold were the active source
- wording that could make maintainers think compatibility fields still outrank chapter-based source authority

Rule:

- only clean names that still create semantic ambiguity
- do not perform style-only churn

## Good-To-Do Next Round

These are useful, but not required before the repository reaches a stable consolidation point.

### 1. Review remaining low-priority references

Candidates:

- `references/orchestration-and-memory-mode.md`
- release-support examples
- roadmap / maintenance-note files

Only touch them if they still create real semantic confusion.

### 2. Decide whether to normalize contract naming further

Examples:

- whether `linear_step_order_authority` should stay forever as compatibility naming
- whether more chapter-aware aliases are needed

This is a low/medium risk cleanup topic, not a current blocker.

### 3. Run a future packaging pass

Only after consolidation is complete.

## Explicit Stop List

The following should now stop by default.

### Stop 1

Do not add new architecture planes.

### Stop 2

Do not explode the six-state shell into a 12-state runtime machine.

### Stop 3

Do not mass-rewrite remaining reference files just because they are old.

### Stop 4

Do not reopen runtime/provider/governance expansion unless a real task explicitly requires it.

### Stop 5

Do not keep polishing wording that no longer affects boundary meaning.

## Decision Table

| Situation | Action |
| --- | --- |
| A file still causes real source-authority ambiguity | fix now |
| A file is old but semantically harmless | defer |
| A change only improves wording style | stop |
| A downstream consumer now needs a missing distinction | reopen targeted reconstruction |
| The repository is still marked release-ready while active reconstruction continues | fix now |

## Recommended Immediate Sequence

1. Verify release-facing truth consistency.
2. Verify `SKILL` / shell / contract boundary consistency.
3. Apply only high-signal cleanup.
4. Re-evaluate whether the repo is still in `L2` or ready to move toward `L3`.

## Final Conclusion

The repository does not need another wide reconstruction wave.

It now needs:

- selective cleanup,
- internal consistency checks,
- and a controlled decision about when to stop editing and prepare for commit-level review.
