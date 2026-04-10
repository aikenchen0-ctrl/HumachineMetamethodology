# discovery-and-hypothesis-mode

## Purpose

Use this mode when the problem is not only unclear, but also still needs explicit demand discovery, visibility shaping, and open-assumption management.

This mode is source-aligned with the original material on:

- strict versus open clarification,
- repeated confirmation loops,
- early adopter and extreme-user signals,
- latent demand,
- field-created demand,
- cognitive-economy demand,
- visibility barriers,
- soft pruning,
- low-confidence demotion,
- and feedback hooks that preserve future writeback.

In the maintained chapter-based `metaPrompt v2`, this mode now sits closest to:

- chapter 4: task entry and clarification
- chapter 5: problem modeling
- chapter 6: state / constraint / ideal-direction analysis
- chapter 8: retrieval and evidence writeback
- chapter 11: pluginization and self-upgrade

## Boundary To The Base Chain

The base chain may already record lightweight fields such as:

- `visible_demand`
- `real_demand_hypothesis`
- `assumed_constraints`
- `real_constraint_hypothesis`

That is still not the same as activating discovery mode.

Activate this mode when you also need to model:

- latent demands that are not yet directly stated,
- demands that are created or amplified by a field,
- cognitive-economy or social-pressure drivers,
- visibility barriers that keep demand unspoken or unnamed,
- explicit open assumptions and reversible pruning,
- or feedback hooks that will later feed governance writeback.

## Clarification Modes

### Strict Mode

Use when:

- terminology must converge quickly,
- ambiguity is more dangerous than omission,
- and the workflow should move toward stable modeling soon.

### Open-Preserving Mode

Use when:

- the problem space is still forming,
- premature convergence would kill viable paths,
- or multiple interpretations still need to coexist temporarily.

Recommended fields at the base-chain boundary:

- `clarification_mode`
- `confirmation_loop_status`

## Demand Visibility

The source does not treat demand as only what the user already says explicitly.

You may need to distinguish:

- explicit demands,
- latent demands,
- field-created demands,
- cognitive-economy factors,
- visibility barriers,
- early adopter signals.

This is why `demand-visibility.json` exists.

### `demand-visibility.json`

Required top-level fields:

- `explicit_demands`
- `latent_demands`
- `field_created_demands`
- `cognitive_economy_factors`
- `visibility_barriers`
- `early_adopter_signals`

Useful optional structure:

- `base_chain_boundary`
- `promotion_rules`
- `scene_context`

## Hypothesis Management

The source keeps assumptions open longer than a normal planning workflow would.

Default stance:

- assume a path is possible before rejecting it,
- suspend or soft-prune before deleting,
- lower confidence before imposing hard exclusion,
- and avoid irreversible commitments too early.

### `hypothesis-register.json`

Required top-level fields:

- `open_assumptions`
- `confidence_levels`
- `soft_pruning_candidates`
- `hard_constraints_to_avoid`
- `irreversible_actions_to_avoid`

Useful optional structure:

- `reopen_conditions`
- `suspension_rules`
- `evidence_gaps`
- `demotion_rules`

## Feedback Hooks

Feedback hooks are not the same as a feedback ledger.

`feedback-hooks.json` is for:

- where feedback can re-enter,
- which triggers should cause a re-check,
- and what target later governance writeback should use.

`feedback-ledger.json` is for:

- what feedback actually happened,
- what correction was applied,
- and what is still pending.

### `feedback-hooks.json`

Required top-level fields:

- `human_override_points`
- `real_world_feedback_sources`
- `validation_triggers`

Useful optional structure:

- `writeback_targets`
- `handoff_to_feedback_ledger`
- `evidence_channels`
- `trigger_scope`

## Activation

Enable this mode when:

- the user explicitly asks for latent demand discovery,
- the user explicitly asks why demand is invisible, unnamed, or blocked,
- the user explicitly asks to preserve openness rather than collapse early,
- the current problem still depends on high-uncertainty assumptions,
- or the base-chain demand split is not enough because latent/visibility/open-hypothesis work is now first-class.

Do not activate this mode just because `problem-brief.json` contains lightweight visible or real demand hypotheses. Discovery mode is for the next layer beyond that.

Also do not let this mode silently absorb:

- chapter 8 retrieval itself,
- chapter 9 generation itself,
- or chapter 11 plugin decisions themselves.

Its job is to enrich demand visibility and open-assumption handling, not to replace those later layers.
