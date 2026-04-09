# traversal-and-invention-mode

## Purpose

Use this mode after a main contradiction is already known but the solution space still needs ordered divergence rather than free-form brainstorming.

This mode is source-aligned with the original material on:

- micro divergence followed by ordered convergence,
- relation traversal,
- parameter traversal,
- granularity / containment traversal,
- dimension anchoring,
- spacetime intersection filtering,
- causal terminal anchoring,
- blackbox conversion,
- IFR elimination,
- invention measures,
- and measure combinations that cause a system-level change.

## Default Sequence

1. Build `traversal-plan.json`.
2. Apply `heuristic-filters.json`.
3. Generate `invention-measures.json`.
4. Synthesize `measure-combinations.json`.

Do not start with measure generation before the traversal focus and the heuristic filters are explicit.

## Ordered Traversal

### 1. Relation Dimensions

Start from interaction relations, not from a product part list.

At minimum, relation traversal should consider:

- attribution or role relation,
- variation relation,
- comparison relation.

Add more relation types only when the current contradiction actually needs them.

Each relation dimension should prefer:

- the centered tension,
- the source anchor,
- the key traversal questions,
- candidate moves,
- and expected payoff.

### 2. Parameter Dimensions

List the parameters that actually carry the contradiction.

For each parameter dimension, make explicit:

- the current tension,
- the allowed traversal directions,
- the stop rule or threshold boundary,
- and any linked routes that depend on this dimension.

### 3. Granularity / Containment Dimensions

Do not jump across many levels at once.

Traverse one containment move at a time:

- current layer,
- one level more macro,
- one level more micro.

Use granularity traversal to expose where the contradiction truly lives, not to reopen the whole surrounding system.

## Dimension Anchoring And Razor

Treat the source razor as a default rule.

- Anchor on the dominant harmful interaction or deficient function chain.
- Stay on the narrowest dimension that can still change that interaction.
- Do not start from visible product structure or backend inventory.
- If the contradiction is about how a capability acts, not how it is internally produced, black-box the producing subsystem as a field.
- Defer wider dimensions explicitly instead of mixing them back into the active focus.

## Four Core Heuristics

### 1. Spacetime Intersection Rule

Keep only the elements that directly interact inside the exact failure slice.

Useful fields:

- `focus_time_slice`
- `focus_space_slice`
- `keep_elements`
- `pruned_elements`
- `pass_rule`

### 2. Causal Terminal Anchoring Rule

Separate background states from terminal operators.

Do not confuse:

- state dependency,
- action trigger,
- and immediate contradiction carrier.

Useful fields:

- `terminal_actions`
- `background_states`
- `filtered_out_as_non_terminal`
- `chosen_terminal_targets`

### 3. Blackbox Conversion Rule

If a subsystem only supplies a capability or field, and the current contradiction is not about that subsystem's internal generation logic, convert it into a black box.

Useful fields:

- `from_component`
- `to_abstraction`
- `conversion_reason`

### 4. IFR Elimination

Ask whether removing a component makes the core contradiction disappear.

- If the contradiction persists, prune or black-box the component.
- If the contradiction disappears but the goal also collapses, reconstruct rather than delete it.
- If the contradiction disappears and the goal survives, the component was likely unnecessary complexity.

Useful fields:

- `tests`
- `retained_core_operators`
- `removed_from_focus`
- `summary`

## Invention Measures

Do not flatten all moves into one list.

Generate measures in layers:

1. `single_measures`
2. `paired_measures`
3. `complex_measures`

Prefer each measure entry to expose:

- identity,
- measure family,
- target contradiction,
- description,
- expected effects,
- and guardrails.

## Measure Combinations

A measure combination is not just `A + B + C`.

It must explain:

- why the combination becomes a new mechanism,
- what system-level change follows,
- when it should be used,
- and what new risks appear.

If the high-level direction stays fixed while the path can vary, keep the goal lock explicit in the combination entry.

## Recommended Artifacts

### `traversal-plan.json`

Required top-level fields:

- `relation_dimensions`
- `parameter_dimensions`
- `granularity_dimensions`
- `anchor_rules`
- `selected_focus`

Useful optional structure:

- `relation_type_taxonomy`
- `scope_guard`
- relation entry fields such as `traversal_questions`, `candidate_moves`, `expected_payoff`
- selected-focus fields such as `primary_dimensions`, `secondary_dimensions`, `deferred_dimensions`, `why_this_focus`, `next_artifact_targets`

### `heuristic-filters.json`

Required top-level fields:

- `spacetime_filter`
- `causal_terminal_filter`
- `blackbox_conversion_rules`
- `ifr_elimination_results`

Useful optional structure:

- spacetime filter details such as `keep_elements` and `pruned_elements`
- causal terminal details such as `terminal_actions` and `background_states`
- IFR details such as `retained_core_operators` and `removed_from_focus`

### `invention-measures.json`

Required top-level fields:

- `single_measures`
- `paired_measures`
- `complex_measures`
- `selection_rationale`

Useful optional structure:

- `measure_family`
- `target_contradictions`
- `expected_effects`
- `guardrails`
- route-fit fields such as `best_fit_routes` or `best_fit_route`

### `measure-combinations.json`

Required top-level fields:

- `combinations`
- `combined_mechanism`
- `system_level_change`
- `risks`

Useful optional structure:

- `goal_lock`
- `when_to_use`
- `status`
- `why_this_is_new`
- `change_type`

## Activation

Enable this mode when:

- the user explicitly asks for systematic traversal, heuristic filtering, IFR, invention measures, or measure combinations,
- the problem already has a main contradiction,
- and the current gap is not contradiction discovery but ordered solution-space expansion.

Do not enable it just because the user wants more ideas in general. This mode is for structured divergence under bounds.
