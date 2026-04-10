# metaPrompt-v2-consistency-review

## Purpose

This file records the current consistency review after the repository has been aligned to the maintained chapter-based `metaPrompt v2`.

The review does not ask whether everything is perfect.

It asks:

1. whether the main layers now speak the same source language,
2. whether any remaining mismatch is severe enough to block further work,
3. and what the safest next move is.

## Layers Reviewed

This review checks five layers:

1. source layer
2. typed companion layer
3. boundary layer
4. contract layer
5. shell / entry layer

## Current Review Result

### 1. Source Layer

Status:

- aligned

Evidence:

- `references/metaPrompt.md` now carries the maintained `metaPrompt v2` chapter scaffold
- `references/core-method.md` and `references/source-alignment-policy.md` now interpret that scaffold correctly

### 2. Typed Companion Layer

Status:

- aligned

Evidence:

- `references/metaPrompt-step-index.md`
- `references/metaPrompt-step-index.json`

now describe the chapter-based source and treat older step-oriented language as compatibility rather than authority.

### 3. Boundary Layer

Status:

- aligned

Evidence:

- `references/scope-boundary.md`
- `references/skill-capability-boundary-review.md`
- `references/metaPrompt-v2-shell-review.md`
- `references/metaPrompt-v2-contract-gap-review.md`

now all agree that:

- the maintained source is richer than the old shell,
- retrieval / generation / evaluation / pluginization are first-class source layers,
- but the runtime shell may still compress them conditionally.

### 4. Contract Layer

Status:

- partially aligned but stable

Evidence:

- `references/state-machine.yaml`
- `references/state-contracts.yaml`

now explicitly say that:

- the six-state shell is a runtime compression of `metaPrompt v2`
- chapter-based authority is the maintained source truth
- old `derived_from_metaPrompt_step` fields remain only as compatibility metadata

Residual issue:

- the contract layer still carries some historical naming such as `linear_step_order_authority` and `meta_prompt_linear_scaffold`
- but these are now clearly downgraded by companion fields and notes, so they are not currently severe blockers

### 5. Shell / Entry Layer

Status:

- aligned enough for controlled continuation

Evidence:

- `SKILL.md`
- `README.md`
- `agents/openai.yaml`

now all acknowledge:

- the maintained source is chapter-based
- the six-state shell is a compression
- retrieval and pluginization are first-class source layers even when conditionally expanded in runtime

## Critical Conflict Check

The following high-risk conflicts were checked:

1. source still pretending to be the old numbered draft
2. shell still pretending to be the source itself
3. boundary files still treating retrieval and pluginization as optional folklore only
4. contracts still silently using old step numbers as source truth

Current result:

- none of these remain as critical active conflicts

## Residual Low / Medium Risks

### Low Risk

1. some compatibility-oriented names still contain the word `linear`
2. several review files still mention the old draft explicitly as a historical contrast

These are not current blockers.

### Medium Risk

1. `state-contracts.yaml` still has a large surface and may hide further low-signal historical residue
2. release-facing files now correctly say “active reconstruction”, but they will need another pass once the repo moves from reconstruction to consolidation

These are review debts, not structural blockers.

## What This Means Practically

The repository is now in a good state for one of two controlled next moves:

1. continue with targeted contract clean-up only when a real ambiguity is discovered
2. or stop architecture expansion here and move into consolidation, verification, and commit preparation

What it does **not** justify:

1. exploding the shell into a full 12-state runtime machine
2. mass-rewriting every remaining reference file
3. reopening runtime/provider/governance expansion by default

## Current HMM Interpretation

If the repository-side reconstruction states are:

- `P1` source/index sync
- `P2` entry sync
- `P3` contract sync
- `P4` shell refactor

then the current review suggests:

- `P1` completed
- `P2` completed
- `P3` sufficiently completed for now
- `P4` partially completed, but intentionally not expanded further

That is enough to stop broad reconstruction and switch to controlled consolidation work.

## Recommended Next Move

The safest next move is now:

- stop broad architecture rewriting,
- and perform a small-scope consolidation round:
  - review modified files,
  - confirm what remains intentionally provisional,
  - then decide between commit preparation or one final tiny cleanup batch.

## Final Conclusion

The repository is no longer in “new source plus old interpretation” drift.

It is now in:

- “new source plus mostly aligned interpretation with bounded compatibility residue”.

That is a stable enough state to stop expanding the reconstruction surface and move into consolidation-oriented work.
