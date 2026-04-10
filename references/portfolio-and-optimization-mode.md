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

### 6. Portfolio Consumes Weighting, It Does Not Automatically Own It

Portfolio mode may need weighting information, but that does not mean it automatically owns reusable ranking semantics.

Current boundary:

- `library_and_weighting_mode` owns reusable ranking logic and `decision-weighting.json`
- `portfolio_and_optimization_mode` owns multi-route comparison, tradeoff exposure, research/execution separation, and approximate-best reporting
- `governance_and_feedback_mode` owns human override authority when people overrule ranking or plan selection

Use portfolio-local weighting only when:

- no separate reusable weighting artifact is needed,
- the weighting stays local to the current optimization round,
- and the result is explicitly framed as approximate decision aid rather than durable ranking policy.

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

If ranking semantics already exist in `decision-weighting.json`, prefer referencing that basis rather than silently recomputing a second independent ranking logic inside `optimization-report.json`.

If the current round uses only a local approximate comparison, make that limitation explicit in `ranking_basis` or `fallback_weight_method`.

## Activation

Enable this mode when:

- the user explicitly asks for approximate-best multi-path comparison,
- the user explicitly asks for methodology branching,
- the user explicitly asks for research and execution plans to be separated,
- the user explicitly asks for five-direction approximate optimality or AHP-like ranking,
- or the current problem already has multiple objectives, routes, and constraints that cannot be represented honestly as one linear plan.

Do not enable it just because there are two candidate ideas. Use it when comparison, tradeoff management, and staged commitment are first-class needs.

Do not enable library-and-weighting mode automatically just because portfolio mode is active.
Only add reusable weighting artifacts when the ranking logic itself needs to be preserved, reused, or handed off outside the current optimization round.
