# metaPrompt-v2-shell-review

## Purpose

This file reviews whether the current six-state `HMM` shell can still serve as a safe runtime compression of the maintained chapter-based `metaPrompt v2` source.

It does not yet rewrite the runtime shell.

It answers:

1. what the maintained source now looks like,
2. how the current shell compresses it,
3. where the compression is still acceptable,
4. and where the repository still carries meaningful drift risk.

## Maintained Source Shape

The maintained `references/metaPrompt.md` is no longer the old numbered `步骤1-步骤8` draft.

It is now a chapter-based source scaffold with these active method layers:

1. chapter 1: shared symbol system
2. chapter 2: Six-Box top scaffold
3. chapter 4: task intake and clarification
4. chapter 5: `E/A/F/Cond` modeling
5. chapter 6: `S0/Sg/IFR/C/TC/PC` analysis
6. chapter 7: resources and system levels
7. chapter 8: retrieval and evidence writeback
8. chapter 9: candidate generation
9. chapter 10: evaluation, validation, and implementation
10. chapter 11: pluginization and skill exteriorization
11. chapter 12: mainline and forced loopback

That means the maintained source is now:

- less like a short numbered method note,
- and more like a layered mother-method with a stable mainline.

## Current Runtime Shell

The current runtime shell is still:

1. `problem_intake`
2. `semantic_clarification`
3. `demand_constraint_modeling`
4. `branch_plan_generation`
5. `evaluation_validation`
6. `loop_or_finish`

This shell is still useful, but it is now clearly a compression rather than a direct mirror of the source.

## Compression Mapping

The safest current interpretation is:

### `problem_intake`

Compresses:

- the pre-entry part of chapter 4

### `semantic_clarification`

Compresses:

- the rest of chapter 4

### `demand_constraint_modeling`

Compresses:

- chapter 5
- chapter 6
- and lightweight chapter 7 awareness when resource notes are needed but no full advanced modeling is activated

### `branch_plan_generation`

Compresses:

- the bridge from chapter 6 into chapter 9
- target selection
- candidate routing
- and solution-space staging

It does **not** fully equal chapter 9, but it is currently the closest outer-shell state for that transition.

### `evaluation_validation`

Compresses:

- chapter 10
- and the finish-gating part of chapter 11 when pluginization remains advisory rather than fully materialized

### `loop_or_finish`

Compresses:

- chapter 12
- plus any explicit writeback-driven return to earlier states

## What Still Works

The current shell is still acceptable as MVP compression because:

1. it keeps one explicit mainline,
2. it already separates clarification, modeling, planning, evaluation, and loopback,
3. it does not force runtime expansion by default,
4. and the maintained source itself still supports a compressed operational reading.

In particular:

- the shell is still good enough for runtime execution guidance,
- provided the repo explicitly acknowledges that it is a compression of a richer source.

## What Is No Longer Safe To Leave Implicit

The following cannot safely remain implicit anymore:

1. chapter 8 retrieval is a first-class stage in the source
2. chapter 11 pluginization is a first-class stage in the source
3. chapter 1 symbol control now matters to almost every later chapter
4. chapter 2 Six-Box now carries stronger authority than before

So even if the runtime shell remains six-state, the repo should now say explicitly:

- retrieval is not just a side note,
- pluginization is not just an optional afterthought,
- and the maintained source chapter scaffold outranks any historical step numbering.

## Current Drift Risk

The repo now has three different levels of alignment:

### Low Drift

Already aligned:

- `references/metaPrompt.md`
- `references/metaPrompt-step-index.*`
- `references/core-method.md`
- `references/source-alignment-policy.md`
- `references/advanced-mode.md`

### Medium Drift

Partially aligned:

- `SKILL.md`
- `references/state-machine.yaml`
- `references/state-contracts.yaml`

These files now acknowledge the maintained source, but they still rely on older shell vocabulary and in some places still talk in terms that came from the older source arrangement.

### Higher Drift

Still likely to need review:

- `references/scope-boundary.md`
- `references/output-and-evaluation.md`
- `references/discovery-and-hypothesis-mode.md`
- `references/orchestration-and-memory-mode.md`
- release-facing consolidation references

These files may still be semantically correct, but they have not yet been deliberately reviewed against the chapter-based maintained source.

## Current Decision

The current six-state shell should be kept for now.

Reason:

1. replacing the shell too early would create a large second-order refactor,
2. the maintained source has already been restored at the source layer,
3. and the main risk now is not shell invalidity, but silent mismatch between shell contracts and source chapter semantics.

So the next safe move is:

- do not rewrite the runtime shell yet,
- first make the shell-to-source compression explicit in the contracts and boundary files.

## Second-Batch Refactor Focus

The second batch should focus on:

1. `state-machine.yaml`
2. `state-contracts.yaml`
3. `scope-boundary.md`

The goal is not to explode the six-state shell into chapter states immediately.

The goal is to ensure these files explicitly recognize:

- chapter-based source authority,
- retrieval as a first-class maintained source layer,
- pluginization as a first-class maintained source layer,
- and where the six-state shell is only a compressed operational proxy.

## Final Conclusion

The shell is still usable.

But from now on, the repository should treat it as:

- a runtime compression of `metaPrompt v2`,
- not as the source scaffold itself.

That distinction is the key to keeping the repository coherent during the next reconstruction batch.
