# branch-topology-decision-table

## Purpose

This file normalizes how branch topology should be chosen at the abstract method layer.

It exists because the OPML contains several overlapping topology ideas:

- parallel worker
- parallel branch
- serial branch
- suspended traversal
- parallel fork
- split / fracture / candidate-generation imagery

Without one decision table, topology selection stays intuitive rather than auditable.

## Decision Axes

Judge branch topology by these axes:

- whether the problem space changes,
- whether full history is shared,
- whether merge is expected,
- whether execution order is constrained,
- and whether paths are temporarily suspended versus structurally detached.

## Topology Classes

### `parallel_worker`

Use when:

- the problem definition is unchanged,
- full history is shared,
- multiple execution units handle different todo items in parallel,
- and results remain part of one merged execution surface.

### `parallel_branch`

Use when:

- paths may change assumptions or constraints,
- full history is shared,
- and the branch explores different problem-space interpretations.

### `serial_branch`

Use when:

- branching still exists,
- but each branch has an internal strict order or dependency chain.

### `suspended_traversal`

Use when:

- a path is postponed,
- not permanently rejected,
- and may later be reactivated under explicit conditions.

### `parallel_fork`

Use only when:

- full history is not shared,
- later holistic merge is not expected by default,
- and the path behaves like a detached exploration topology rather than an ordinary branch class.

## Default Non-Promotion Rule For `parallel_fork`

Do not promote `parallel_fork` into a stronger default contract merely because the source names it.

Promote it further only when a real execution case proves that:

- `parallel_worker`
- `parallel_branch`
- and `serial_branch`

cannot express the needed topology cleanly.

Until then:

- keep it as a deferred candidate concept,
- and treat the decision to defer as complete rather than as unfinished architecture work.
