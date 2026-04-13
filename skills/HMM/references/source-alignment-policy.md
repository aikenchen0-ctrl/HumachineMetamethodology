# source-alignment-policy

## Purpose

This file prevents scope drift when the skill is being aligned to the maintained source materials:

- `references/metaPrompt.md`
- `references/agentic-nested-state-machine.opml`

The maintained source is primarily about:

- chapter-based problem structuring,
- shared symbol control,
- Six-Box mainline reasoning,
- ANT / EAFC modeling,
- state / constraint / ideal-direction analysis,
- retrieval and evidence writeback,
- candidate generation,
- evaluation and fallback,
- pluginization and self-upgrade.

It is not primarily about long-lived runtime operations engineering.

## Dual-Source Arbitration

The source is not one document.

It is two cooperating but non-identical source layers:

- `references/metaPrompt.md`
- `references/agentic-nested-state-machine.opml`

Use this default arbitration rule:

### `references/metaPrompt.md` Is Authoritative For

- the chapter order,
- the main method chain,
- the placement of retrieval, generation, evaluation, and pluginization,
- the shared symbol system,
- and what counts as the maintained source scaffold.

### `references/agentic-nested-state-machine.opml` Is Authoritative For

- the mother-structure around branching,
- workflow shell context,
- orchestration imagination,
- archive and product interaction residue,
- and the larger source ecology around collaboration, evaluation, and execution imagination.

### When They Overlap

- use `references/metaPrompt.md` to decide chapter order, mainline semantics, and layer placement,
- use `references/agentic-nested-state-machine.opml` to decide mother-structure, branch semantics, and surrounding source planes,
- and use typed source assets only to normalize that relation, not to replace it.

### Practical Conflict Rule

If a conflict appears:

1. ask whether it is about chapter order / mainline semantics or about mother-structure
2. if it is about chapter order / mainline semantics, prefer `references/metaPrompt.md`
3. if it is about branch / orchestration / archive / interaction structure, prefer `references/agentic-nested-state-machine.opml`
4. if the conflict remains mixed, record it explicitly rather than silently blending the two interpretations

## Typed Dual-Source Entry

For maintenance work, prefer these typed entry points:

- `references/metaPrompt-step-index.json`
  for the chapter scaffold
- `references/typed-source-node-index.yaml`
  for the OPML mother-structure

## Two Rings

### Ring 1: Source-Aligned Core

These capabilities are directly grounded in the maintained source and may be activated by default when the task is about:

- problem clarification
- chapter alignment
- demand and constraint modeling
- retrieval and evidence writeback
- candidate generation
- pluginization and skill exteriorization
- branch planning
- evaluation and loopback

### Ring 2: Derived Runtime Operations Extension

These capabilities are valid engineering extensions, but they are not direct defaults from the maintained source. They must stay opt-in and scope-guarded.

This ring includes artifacts for:

- runtime hooks
- event source contracts
- schema registries
- consumer compatibility probes
- provider failover
- health telemetry
- adaptive thresholds
- long-term threshold governance

## Activation Rule

When the current task is:

- aligning the skill back to the maintained source
- refining prompt methods
- refining chapter boundaries
- refining problem-structuring workflows
- refining plugin / retrieval / generation / evaluation interfaces

then Ring 2 must remain inactive unless the user explicitly asks for real runtime operations behavior.

## Scope Guard

Do not activate Ring 2 just because the user mentions:

- branching
- shared files
- execution supervision
- memory pruning
- feedback
- governance

Ring 2 may activate only when the task explicitly includes at least one of:

- real runtime signal intake
- external service hooks
- registry version compatibility
- provider topology
- failover or recovery switching
- continuous drift monitoring
- long-lived governance operations

## Mode-Resolution Requirement

When the current task is source alignment, `mode-resolution.json` should make the distinction explicit:

- what is active in the source-aligned core
- what is blocked as a derived runtime extension
- why the blocked outputs are out of scope for the current round

## Repair Rule

If the skill has already drifted into Ring 2 while the task is still source alignment:

1. do not add more runtime artifacts
2. record the drift explicitly
3. block the non-source outputs in `mode-resolution.json`
4. route repair back to the earliest scope-definition layer rather than patching downstream artifacts only
