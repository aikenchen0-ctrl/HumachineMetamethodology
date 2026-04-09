# governance-and-feedback-mode

## Purpose

Use this mode when the workflow needs explicit human-in-the-loop control rather than treating the model's current output as final.

This mode is source-aligned with the original material on:

- bounded choice-style or heuristic questioning,
- human visibility across files and prompts,
- human ability to modify weights and artifacts,
- automatic weighting only when human weights are absent,
- and real-world feedback as a dedicated correction channel.

## Core Position

### 1. Interaction Is Designed, Not Casual

The source does not treat user questioning as open-ended chat by default.

Prefer:

- bounded choice prompts,
- heuristic prompts,
- explicit trigger conditions for asking,
- and explicit avoid-styles for low-value questioning.

### 2. Human Visibility And Editability Matter

Do not assume model outputs are untouchable.

Governance should make visible:

- which artifacts humans can inspect,
- which artifacts humans may modify,
- which checkpoints require review,
- and which constraints remain non-overridable.

### 3. Human Weights Override Automatic Weights

If a human specifies weights or priorities, use them first.

Only when human input is absent should the system fall back to:

- pairwise comparison,
- AHP-style ranking,
- or another explicit automatic weighting rule already declared elsewhere.

### 4. Feedback Is A Correction Channel

Real-world feedback is not an optional note.

It should record:

- where feedback came from,
- what changed because of it,
- what is still pending validation,
- and what remains unresolved even after a correction was applied.

## Recommended Artifacts

### `interaction-policy.json`

Required top-level fields:

- `question_styles`
- `default_style`
- `avoid_styles`
- `trigger_conditions`

Useful optional structure:

- `preferred_style_order`
- `bounded_prompt_templates`
- `heuristic_prompt_templates`
- `escalation_question_rules`

### `governance-checkpoints.json`

Required top-level fields:

- `checkpoints`
- `human_review_points`
- `modifiable_artifacts`
- `non_overridable_constraints`

Useful optional structure:

- `review_roles`
- `checkpoint_entry_conditions`
- `checkpoint_exit_conditions`
- `required_artifact_visibility`

### `override-policy.json`

Required top-level fields:

- `human_override_priority`
- `weight_override_rules`
- `fallback_when_no_human_input`

Useful optional structure:

- `plan_override_rules`
- `conflict_resolution_order`
- `fallback_weight_method`
- `consistency_check_requirement`

### `feedback-ledger.json`

Required top-level fields:

- `feedback_sources`
- `feedback_events`
- `applied_corrections`
- `pending_real_world_checks`

Useful optional structure:

- `rejected_feedback`
- `feedback_confidence`
- `writeback_targets`
- `reopen_triggers`

## Cross-Mode Boundary

- `decision-weighting.json` belongs to library and weighting mode.
- `override-policy.json` belongs to governance and feedback mode.

The first computes or records ranking logic.
The second decides what happens when human instruction conflicts with that ranking.

Do not merge them into one artifact unless the broader contract is redesigned.

## Activation

Enable this mode when:

- the user explicitly asks for guided question styles,
- the user explicitly asks for human review or human-modifiable checkpoints,
- the user explicitly asks for override rules for plans or weights,
- the user explicitly asks for real-world feedback tracking,
- or the current workflow already contains human review points, override points, or feedback writeback requirements.

Do not activate runtime governance operations just because governance mode is active. This mode stays on the human-review and feedback side unless the task explicitly widens into real runtime governance systems.
