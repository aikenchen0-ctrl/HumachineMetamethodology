# boundary-razor-policy

## Purpose

This file defines the boundary razor for the current `HMM` architecture.

Its job is not to add new planes.
Its job is to stop unnecessary expansion after the major source-alignment work is already complete.

## Core Rule

When an archive plane or typed source layer already exists in maintained usable form, do not keep expanding it by default.

Expand it only if at least one of these is true:

- a real downstream consumer now depends on a missing distinction,
- a current active contract is still forced to reconstruct that plane implicitly,
- or a real source change invalidates the current maintained layer.

Otherwise:

- freeze the plane at its current boundary,
- keep it readable,
- keep it machine-readable,
- but do not keep turning archive material into workflow-facing contract surface.

## Freeze States

### `alignment_surface`

Keep aligned and maintained, but do not expand by default.

### `archive_boundary`

Keep non-core material out of workflow contracts; expand only when a real consumer requires it.

### `gated_optional_plane`

Keep available, but never activate implicitly into the neutral core.

### `wait_real_case`

Hold current decision-table form until a real distinguishing case appears.

### `policy_defined`

Treat current policy as sufficient unless an explicit reactivation trigger appears.

## Current Freeze Matrix

- `typed_source_plane`
  `alignment_surface`
- `product_interaction_archive_plane`
  `archive_boundary`
- `execution_substrate_plane`
  `archive_boundary`
- `strategy_intervention_plane`
  `gated_optional_plane`
- `topology_decision_plane`
  `wait_real_case`
- `archive_compatibility_plane`
  `policy_defined`

## Expansion Tests

Before expanding any of these planes, ask:

1. Which active contract is still forced to reconstruct this plane implicitly?
2. Which real downstream consumer now requires the extra distinction?
3. What would break if the plane stayed frozen today?

If none of those questions has a concrete answer, do not expand the plane.

## Stop Rule

If all of the following are true:

- release gates are satisfied,
- no non-completed backlog items remain,
- frozen planes are already bounded by explicit policy,
- and no real downstream consumer is forcing a new distinction,

then stop architecture expansion work.

At that point, the correct next move is:

- release review,
- commit preparation,
- packaging,
- or distribution work,

not another abstract architecture pass.
