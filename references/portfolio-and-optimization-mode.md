# portfolio-and-optimization-mode

## Purpose

Use this mode when one structured path is no longer enough and the task needs explicit comparison across multiple methods, routes, objectives, or constraint settings.

This mode is source-aligned with the original material on:

- five-direction approximate optimality,
- methodology branching,
- research plans,
- execution plans,
- explicit state-space matrices,
- and weighting that may come from humans first and only fall back to pairwise or AHP-style comparison when human weights are absent.

## Core Position

### 1. Approximate Best, Not Premature Single Best

The source logic is not to pretend one route is uniquely optimal when objectives conflict.

Prefer to preserve:

- multiple objectives,
- multiple routes,
- multiple weighting styles,
- and an approximate-best set before collapsing to one recommendation.

### 2. Methods Themselves Can Branch

Do not only branch the problem.

Also make explicit:

- which method family each branch uses,
- which constraints changed,
- which weights changed,
- and which route exists only because of that methodological shift.

### 3. State-Space Matrices Are Decomposition Devices

The matrix layer should not be treated as decoration.

It should clarify:

- what decomposition basis is being used,
- which observation surface each matrix represents,
- and which cells are high-priority, blocked, or deferred.

### 4. Research And Execution Must Be Layered

Keep these separate:

- research plan,
- execution roadmap.

The split is structural:

- `research-plan.json` answers what must still be learned,
- `execution-roadmap.json` answers what to do in what order once action is justified.

### 5. Weighting Priority

If explicit human weights exist, use them first.

If not, a lightweight pairwise or AHP-style fallback is acceptable, but it must remain explicit:

- what criteria were compared,
- whether the comparison was consistent enough,
- and why the resulting ranking should be trusted only as an approximate decision aid.

## Recommended Artifacts

### `state-space-matrix.json`

Required top-level fields:

- `matrix_count`
- `matrices`
- `decomposition_basis`
- `priority_view`

Useful optional structure:

- `matrix_axes`
- `observation_surfaces`
- `blocked_cells`
- `deferred_cells`

### `methodology-portfolio.json`

Required top-level fields:

- `methods`
- `target_objectives`
- `tradeoff_styles`
- `selection_notes`

Useful optional structure:

- `method_families`
- `applicable_constraints`
- `excluded_methods`
- `fallback_weight_method`

### `method-branch-map.json`

Required top-level fields:

- `branches`
- `method_per_branch`
- `changed_constraints`
- `changed_weights`

Useful optional structure:

- `changed_assumptions`
- `shared_invariants`
- `branch_rationale`

### `research-plan.json`

Required top-level fields:

- `research_questions`
- `evidence_to_collect`
- `branch_goals`
- `success_checks`

Useful optional structure:

- `evidence_priority`
- `dependency_layers`
- `decision_gates`

### `execution-roadmap.json`

Required top-level fields:

- `execution_steps`
- `dependencies`
- `parallelizable_groups`
- `milestones`

Useful optional structure:

- `decision_gates`
- `fallback_routes`
- `scope_guard`

### `optimization-report.json`

Required top-level fields:

- `candidate_paths`
- `dominant_tradeoffs`
- `approximate_best_set`
- `why_not_single_best`

Useful optional structure:

- `ranking_basis`
- `non_dominated_set`
- `human_weight_override`
- `fallback_weight_method`
- `consistency_check`

## Activation

Enable this mode when:

- the user explicitly asks for approximate-best multi-path comparison,
- the user explicitly asks for methodology branching,
- the user explicitly asks for research and execution plans to be separated,
- the user explicitly asks for five-direction approximate optimality or AHP-like ranking,
- or the current problem already has multiple objectives, routes, and constraints that cannot be represented honestly as one linear plan.

Do not enable it just because there are two candidate ideas. Use it when comparison, tradeoff management, and staged commitment are first-class needs.
