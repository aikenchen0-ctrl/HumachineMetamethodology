# product-interaction-boundary

## Purpose

This file separates product interaction design from executable problem-structuring method logic.

It exists because the OPML still places UI-heavy ideas close to:

- candidate ranking,
- branch execution,
- template conversion,
- and shared editing behavior.

Those ideas are useful, but they do not belong to the workflow contract plane by default.

## Core Boundary

Treat the following as product interaction archive material rather than method-core contract material:

- candidate display style,
- color coding,
- highlight and diff emphasis,
- selection gestures,
- extraction gestures,
- inline editing affordances,
- viewport composition,
- scroll behavior,
- keyboard and focus handling,
- and client implementation choices.

These may consume workflow artifacts.
They must not redefine workflow semantics.

## Product Interaction Classes

### 1. Candidate Comparison Presentation

Examples:

- color-coded plan comparison
- highlighter for shared versus changed steps
- side-by-side or switchable variant presentation

Consumes:

- `variant-set.json`
- `decision-weighting.json`

Does not own:

- ranking logic
- default selection authority

### 2. Selection And Extraction Interaction

Examples:

- long-press selection
- multi-select extraction
- extract-to-draft
- selection markers

Consumes:

- candidate list artifacts
- step identity

Does not own:

- variant identity
- composition logic

### 3. Inline Editing And Recomposing Interaction

Examples:

- inline step editing
- confirm-and-create new variant
- deleting, regrouping, or recombining displayed steps

Consumes:

- `variant-set.json`
- `composition-plan.json`

Does not own:

- dependency repair semantics
- coherence checks

### 4. Viewport And Layout Composition

Examples:

- multiple text viewports
- scroll composition
- focus order
- keyboard interaction
- viewport synchronization

Consumes:

- representation payloads
- comparison artifacts

Does not own:

- candidate semantics
- workflow routing

### 5. Client Implementation Choice

Examples:

- `TextKit2`
- `SwiftUI ScrollView`
- `UICollectionView + CompositionalLayout`

These are implementation choices, not workflow contracts.

## Promotion Rule

Do not promote a product interaction node into an active workflow contract unless it directly defines:

- a human authority boundary,
- an artifact requirement,
- or a review gate that the workflow itself depends on.

Otherwise:

- archive it as product interaction,
- keep the method contract separate,
- and let product design consume method artifacts downstream.

## Current Source-Aligned Decision

The OPML subtree around:

- multiple-solution comparison,
- color-coded steps,
- long-press selection,
- extract-to-plan-draft,
- viewport composition,
- and client layout choice

should stay in the product interaction archive plane.

It may inform future products.
It should not be promoted through workflow-facing contracts by default.
