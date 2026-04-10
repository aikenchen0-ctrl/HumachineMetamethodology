# release-consolidation-checklist

## Purpose

This file defines the current release-ready consolidation view of the `HMM` reference stack.

It is not another architecture plane.
It is the maintenance-facing map for:

- which assets are core,
- which are optional mode references,
- which are source-review maintenance assets,
- and which are frozen archive/boundary assets.

## Current Operating Mode

The architecture is now in:

- maintenance-consolidation mode

That means:

- do not keep adding new planes by default,
- keep typed source and source-review assets synchronized,
- and only reopen frozen archive planes when a real downstream consumer appears.

## Loading Tiers

### Tier 1: Core Runtime Boundary

Read first when maintaining or executing the skill core:

- `references/scope-boundary.md`
- `references/node-taxonomy.md`
- `references/terminology-policy.md`
- `references/state-contracts.yaml`
- `references/state-machine.yaml`
- `references/core-method.md`
- `references/source-alignment-policy.md`

### Tier 2: Optional Mode References

Read only when the corresponding extension mode is actually needed:

- `references/advanced-mode.md`
- `references/template-mode.md`
- `references/output-and-evaluation.md`
- `references/screen-and-critique-mode.md`
- `references/library-and-weighting-mode.md`
- `references/orchestration-and-memory-mode.md`
- `references/variant-and-composition-mode.md`
- `references/traversal-and-invention-mode.md`
- `references/discovery-and-hypothesis-mode.md`
- `references/portfolio-and-optimization-mode.md`
- `references/governance-and-feedback-mode.md`
- `references/representation-and-serialization-mode.md`

### Tier 3: Source-Review Maintenance Layer

Read when aligning the skill back to the source or maintaining source-review assets:

- `references/examples-index.md`
- `references/examples-index.json`
- `references/opml-promotion-status-model.md`
- `references/opml-promotion-status-model.json`
- `references/source-node-promotion-catalog.json`
- `references/opml-promotion-backlog.json`
- `references/opml-architecture-optimization-roadmap.md`
- `references/opml-architecture-optimization-roadmap.json`
- `references/release-consolidation-checklist.md`
- `references/release-consolidation-checklist.json`
- `references/release-final-review.md`
- `references/release-final-review.json`
- `references/typed-source-node-index.md`
- `references/typed-source-node-index.yaml`
- `references/metaPrompt-step-index.md`
- `references/metaPrompt-step-index.json`
- `references/source-node-type-registry.md`
- `references/source-node-type-registry.json`

### Tier 4: Frozen Boundary / Archive Layer

Read only when a real downstream consumer or explicit review question requires them:

- `references/legacy-artifact-compatibility-policy.md`
- `references/legacy-artifact-compatibility-policy.json`
- `references/branch-topology-decision-table.md`
- `references/branch-topology-decision-table.json`
- `references/product-interaction-boundary.md`
- `references/ui-pattern-archive.json`
- `references/executor-persona-boundary.md`
- `references/execution-substrate-taxonomy.json`
- `references/strategy-intervention-boundary.md`
- `references/optional-strategy-mode.json`
- `references/boundary-razor-policy.md`
- `references/boundary-razor-policy.json`

## Release Gates

Before treating the current architecture as release-ready, confirm:

1. all YAML / JSON / XML reference assets parse successfully
2. `opml-promotion-backlog.json` has no non-completed items
3. `typed-source-node-index.yaml` covers the current promotion catalog
4. `typed-source-node-index.yaml` and `source-node-promotion-catalog.json` stay aligned on shared source fields
5. `metaPrompt.md` versus `agentic-nested-state-machine.opml` precedence stays explicit rather than being silently merged downstream
6. `metaPrompt-step-index.json` preserves the linear source scaffold and explicit numbering anomalies
7. `release-consolidation-checklist.json` covers every `source_review_reference_catalog` asset in an explicit loading tier
8. original source files and `references/` source copies still match by hash
9. `release-final-review.json` exists as the current closeout record once all release gates are satisfied
10. frozen archive planes are not being expanded without a real downstream consumer
11. any remaining `candidate_rule` entries have explicit defer / archive / promotion rationale rather than being unattended leftovers
12. no hardcoded local-machine paths leak into the distributed skill package

## Default Maintenance Rule

Prefer:

- alignment maintenance,
- catalog synchronization,
- and boundary preservation

over:

- creating new reference families,
- promoting archive material into active workflow contracts,
- or widening the default core.

## Release Closeout

When the checklist is fully satisfied, record the current release-facing conclusion in:

- `references/release-final-review.md`
- `references/release-final-review.json`

After that, default to:

- release review,
- commit preparation,
- packaging,
- or distribution,

unless a real downstream consumer or source drift explicitly reopens architecture work.

## Current Snapshot

- source-review reference assets: `19`
- promotion catalog entries: `46`
- typed source entries: `56`
- backlog total items: `8`
- backlog non-completed items: `0`
- original source hash match: `true`
- standard examples: `8`
- UI archive patterns: `6`
- execution substrate classes: `6`
- optional strategy classes: `4`
- remaining `candidate_rule` count: `1`

Interpretation:

- the current stack is in release-ready maintenance mode,
- and the remaining `candidate_rule` is an intentional defer case rather than an unattended gap.
