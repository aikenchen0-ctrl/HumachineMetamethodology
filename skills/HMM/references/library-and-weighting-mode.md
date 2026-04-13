# library-and-weighting-mode

## Purpose

Use this mode when the current method needs to become reusable as libraries, reusable guidance, or explicit weighting structures.

This mode is source-aligned with the original material on:

- noun and term variables,
- parameter libraries,
- effect libraries,
- temporary working libraries,
- reusable user-guidance prompts,
- graph-format choice,
- and weighting through pairwise comparison or AHP-style fallback when human weights are absent.

## Core Position

### 1. Different Libraries Should Stay Different

Do not collapse all reusable knowledge into one bucket.

Keep distinct:

- glossary terms,
- parameters,
- effects,
- temporary working knowledge,
- reusable prompts,
- graph-format choices,
- checklist compression,
- and weighting outputs.

### 2. Weighting Is Not Governance

`decision-weighting.json` belongs here because it computes or records ranking logic.

It should answer:

- what criteria were compared,
- what weighting source was used,
- whether a fallback method was used,
- and what the resulting ranking says.

It should not decide whether a human override wins.

That belongs to governance mode and `override-policy.json`.

### 3. Human Weights First, Automatic Weights Second

If explicit human weights exist:

- use them first,
- record that the source was human,
- and do not silently replace them with automatic weighting.

If human weights do not exist:

- pairwise comparison,
- AHP-style fallback,
- or another explicit fallback method may be used.

### 4. Stable Compression Matters

If a weighting or checklist decision will be reused later, compress it into stable reusable forms:

- `prompt-guidance.json`
- `checklist-summary.json`
- and stable `item_id` values where later references depend on them.

## Recommended Artifacts

### `glossary.json`

Required top-level fields:

- `terms`

### `parameter-library.json`

Required top-level fields:

- `parameters`
- `parameter_types`
- `ranges`
- `relations`

### `effect-library.json`

Required top-level fields:

- `effects`
- `domains`
- `applicability`
- `cautions`

### `temporary-library.json`

Required top-level fields:

- `temporary_terms`
- `temporary_assumptions`
- `temporary_variables`

### `prompt-guidance.json`

Required top-level fields:

- `guidance_entries`

### `graph-format-selection.json`

Required top-level fields:

- `problem_type`
- `recommended_format`
- `why`
- `fallback_format`

### `checklist-summary.json`

Required top-level fields:

- `checklist_name`
- `items`
- `entry_conditions`
- `exit_conditions`
- `fallback_paths`

### `decision-weighting.json`

Required top-level fields:

- `criteria`
- `pairwise_matrix`
- `consistency_check`
- `derived_weights`
- `ranking_result`

Useful optional structure:

- `human_weight_input`
- `weight_source`
- `fallback_used`
- `override_handoff_target`
- `ranking_scope`
- `ranked_subjects_ref`
- `default_selection_rule`
- `selection_evidence_ref`

## Cross-Mode Boundary

- `decision-weighting.json` belongs to library and weighting mode.
- `variant-set.json` belongs to variant and composition mode.
- `override-policy.json` belongs to governance and feedback mode.

The first computes or records a ranking.
The second holds the comparable candidate set and any default-variant pointer.
The third says whether a human can override that ranking, in what order, and how the override should be applied.

Default boundary:

- `decision-weighting.json` owns ranking semantics.
- `variant-set.json` owns candidate listing.
- `override-policy.json` owns final override authority.

Do not let UI list position, example numbering, or phrases such as "方案一提示词" become ranking logic.

If `variant-set.json` exists:

- `ranking_scope` or `ranked_subjects_ref` should bind ranking to stable variant ids,
- and `default_selection_rule` should explain how the final default is chosen without relying on presentation order.

Do not merge these responsibilities by default.

## Activation

Enable this mode when:

- the user asks for reusable terminology, parameters, effects, or prompt guidance,
- the user asks for graph-format selection,
- the user asks for explicit ranking or weighting,
- or multiple paths must be ranked and no explicit human weights have been supplied yet.

Do not activate governance mode just because weighting exists. Governance is for override authority and human review, not for the ranking computation itself.
