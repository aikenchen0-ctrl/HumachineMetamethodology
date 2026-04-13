# typed-source-node-index

## Purpose

This file is the maintained typed companion for `agentic-nested-state-machine.opml`.

It sits closer to the source than:

- the promotion catalog,
- the backlog,
- or the standard example catalog.

Its job is to expose:

- a stable `source_node_id`,
- a typed role,
- a scope layer,
- a source-plane hint,
- and a lightweight source locator

before downstream promotion logic interprets the node further.

## Why This Layer Is Needed

The current architecture already normalized many source ideas downstream.

But the OPML itself is still a free-form tree.

That means downstream assets keep reconstructing:

- node type,
- scope layer,
- source plane,
- and approximate source position.

This file reduces that reconstruction burden.

## Identity Strategy

The index intentionally uses a lightweight locator strategy:

- `root_anchor`
- `ancestor_hint`
- `leaf_text`

instead of a fully brittle absolute path string.

Why:

- some OPML parents are extremely long instruction nodes,
- and the typed source layer should stay stable even when nearby prose is edited.

## Coverage

This typed source companion now aims to cover:

- the current promotion catalog,
- plus a small number of synthetic archive entries for product, execution-substrate, and strategy planes

where the source pattern matters architecturally even before promotion-catalog coverage is expanded further.

## Recommended Next Move

If the source will keep evolving, keep this index aligned with the promotion catalog rather than creating new downstream review assets that reconstruct source position again.
