# metaPrompt-v2-third-batch-review

## Purpose

This file records the review outcome for the current third-batch reference pass after:

- source sync,
- entry sync,
- boundary sync,
- and first contract sync

have already been completed.

Its job is to decide:

1. which remaining reference files still need active rewriting,
2. which ones are already sufficiently aligned,
3. and where to stop instead of over-expanding the reconstruction.

## Files Reviewed In This Batch

1. `references/output-and-evaluation.md`
2. `references/discovery-and-hypothesis-mode.md`
3. `references/orchestration-and-memory-mode.md`

## Review Result

### `output-and-evaluation.md`

Status:

- rewritten and aligned

Reason:

- it directly affects chapter 8, 9, 10, and 11 semantics
- it needed explicit chapter-aware embedding points and writeback semantics

### `discovery-and-hypothesis-mode.md`

Status:

- lightly rewritten and aligned

Reason:

- it was not structurally wrong,
- but it needed an explicit boundary to chapter 8 retrieval, chapter 9 generation, and chapter 11 pluginization

### `orchestration-and-memory-mode.md`

Status:

- reviewed, no immediate rewrite required

Reason:

- it already strongly separates source-aligned orchestration core from derived runtime/provider/governance operations
- its current main risk is not source misalignment, but scope over-activation, and that is already mostly controlled by `SKILL.md`, `state-machine.yaml`, and `state-contracts.yaml`

## Current Stop Rule

Do not rewrite a file in this batch merely because it is large or theoretically important.

Rewrite it only if at least one is true:

1. it still interprets the maintained source as the old numbered draft,
2. it still collapses chapter 8/9/10/11 semantics into vague side notes,
3. it silently expands runtime/provider/governance operations into the neutral core,
4. or it conflicts with already-updated source or contract files.

## Current Batch Conclusion

The third batch should now be treated as:

- substantially complete

because the two most source-sensitive files in this batch have already been aligned, and the third one is already structurally consistent with the current boundary.

## What Not To Do Next

Do not continue mass-rewriting every remaining reference file just because a new source exists.

That would create unnecessary scope expansion.

## Best Next Move

The next move should be one of these two, and only one should be chosen in the next round:

1. perform a focused second-pass contract review of `state-machine.yaml` and `state-contracts.yaml`
2. or prepare repository-side validation / packaging review now that source, entry, boundary, and key references are aligned

## Recommended Choice

Recommend:

- stop the broad reference rewrite wave here,
- and return to a focused contract/validation decision boundary in the next round.

That keeps the reconstruction slow, deep, and controlled, which matches the current HMM-style maintenance strategy.
