# source-node-type-registry

## Purpose

This file explains the typed source roles used by the maintained typed source companion.

It exists so the typed source plane can stay separate from:

- promotion status,
- downstream contract shape,
- and human-readable architecture review.

## Core Node Types

- `state`
  A workflow-stage or stage-like control object.
- `rule`
  A reusable decision boundary, interaction constraint, or topology rule.
- `artifact`
  A source node that points toward a concrete output object or file identity.
- `reference`
  A theory, method, format, or optional background concept that may be activated later.
- `ui`
  A product interaction or client implementation idea, not a workflow contract.
- `example`
  An illustrative scenario or local interaction probe.

## Scope Layers

- `core`
  Default problem-structuring shell.
- `orchestration`
  Branching, execution, shared context, writeback, and topology coordination.
- `reference`
  Optional theory, format, or method background.
- `ui-product`
  Product interaction archive rather than workflow contract.

## Source Plane Hints

The typed source index also uses a lighter `source_plane` hint.

This is not the same as scope layer.

It helps answer:

- which abstract architecture plane the source node most naturally belongs to,
- even before promotion is finalized.

## Why Both Layers Are Needed

`scope_layer` says where the node belongs in the current executable architecture.

`source_plane` says which abstract plane the source node expresses at the source-design level.

The two usually align, but they should not be forced to collapse into one field.

## Current Product Archive Extension

The typed source companion may now also include:

- lightweight synthetic ids for product-interaction archive entries

when the source contains important UI/product patterns that are still worth indexing even before they receive full promotion-catalog coverage.

The same extension rule also applies to execution substrate archive entries when the source contains:

- substrate taxonomy,
- carrier assumptions,
- or executor persona material

that should be indexed before promotion-catalog coverage is expanded.

The same extension rule also applies to optional strategy/intervention archive entries when the source contains:

- demand visibility shaping,
- field construction,
- adoption pressure logic,
- or non-rational amplification references

that should be indexed before promotion-catalog coverage is expanded.
