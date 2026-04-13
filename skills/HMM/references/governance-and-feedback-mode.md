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

When execution profiles are active, interaction should also respect the current profile:

- `共创深探`
  - prefer stepwise or high-signal probe confirmation
- `共创稳推`
  - prefer milestone confirmation rather than every branch
- `自治深探`
  - stay silent during normal forward motion, but keep strong writeback and probe depth
- `自治稳推`
  - stay silent during normal forward motion and avoid unnecessary confirmation expansion

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

## Boundary Reading

This mode should be read in two layers rather than as a bridge into runtime governance systems by default.

### Layer 1: Human Review And Feedback Core

This is the default meaning of governance in this mode:

- guided questioning
- human review checkpoints
- human override priority
- artifact editability
- real-world feedback writeback

### Layer 2: Runtime Governance Systems Extension

This is not the default meaning of governance in this mode:

- threshold governance workflows
- external governance source-of-truth
- governance schedulers
- governance alert routing
- governance approval channels
- provider failover for governance delivery

Those concerns belong to real operational scope and should stay blocked unless the task explicitly widens into runtime/provider/governance operations.

### Reading Rule

- If the current task only needs human review, override logic, or feedback writeback, stay in Layer 1.
- Do not treat the word `governance` by itself as permission to activate runtime governance systems.
- If the user is still doing source alignment, skill review, or normal workflow control, Layer 2 should remain inactive.

## Recommended Artifacts

The artifacts below belong to Layer 1 human-review and feedback core.

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
- `execution_profile_bindings`
- `confirmation_cadence_map`
- `profile_default_style_bindings`

If execution profiles are active, prefer making these explicit:

- which question style belongs to each execution profile
- which confirmation cadence belongs to each execution profile
- which profiles should stay silent unless blocked

### `governance-checkpoints.json`

Required top-level fields:

- `checkpoints`
- `human_review_points`
- `modifiable_artifacts`
- `non_overridable_constraints`

Useful optional structure:

- `review_roles`
- `review_topology`
- `approval_order`
- `checkpoint_entry_conditions`
- `checkpoint_exit_conditions`
- `rejection_reentry_rules`
- `required_artifact_visibility`

### `override-policy.json`

Required top-level fields:

- `human_override_priority`
- `weight_override_rules`
- `fallback_when_no_human_input`

Useful optional structure:

- `plan_override_rules`
- `conflict_resolution_order`
- `reviewer_conflict_resolution`
- `fallback_weight_method`
- `consistency_check_requirement`
- `export_regeneration_rules`

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

Additional boundary:

- execution profiles set interaction cadence and probe aggressiveness
- governance mode owns the user-facing questioning policy and review surfaces
- do not let governance mode silently redefine mode ownership or source authority just because a profile is interactive

## Activation

Enable this mode when:

- the user explicitly asks for guided question styles,
- the user explicitly asks for human review or human-modifiable checkpoints,
- the user explicitly asks for override rules for plans or weights,
- the user explicitly asks for real-world feedback tracking,
- or the current workflow already contains human review points, override points, or feedback writeback requirements.

Do not activate runtime governance operations just because governance mode is active. This mode stays on the human-review and feedback side unless the task explicitly widens into real runtime governance systems.

## Default Boundary Rule

- The artifacts in this file are the default governance-and-feedback artifacts.
- They do not imply threshold governance, approval-channel integration, runtime scheduling, or provider-level governance delivery.
- If those runtime governance concerns become real requirements, treat them as operational-scope expansion rather than as ordinary governance-mode defaults.
