# representation-and-serialization-mode

## Purpose

Use this mode when the current analysis result needs to be exported into an explicit representation layer rather than remaining only as JSON or prose.

This mode is source-aligned with the original material on:

- XML-wrapped rewritten prompts,
- Mermaid sequence diagrams,
- graph formats,
- triple formats,
- DAG formats,
- and logic-oriented symbolic formats.

## Core Position

### 1. Representation Is Part Of The Method, Not Decoration

The source treats serialization and export as functional parts of the workflow.

The representation layer should therefore preserve:

- the same object identity,
- the same scope,
- and the same decision boundaries already established upstream.

Do not use export as a place to silently redefine the problem.

### 2. Different Formats Serve Different Purposes

- `xml` is for strong structural wrapping and tag-based downstream consumption.
- `Mermaid` is for interaction order, sequence, or visible execution flow.
- `triple` is for compressed relation statements.
- `DAG` is for dependencies, branch structure, and non-cyclic execution order.
- `logic` is for necessary conditions, sufficient conditions, gates, and formal rule statements.

Choose formats by use, not by completeness theater.

### 3. Stable Semantics First

Do not export unstable content.

Representation mode should activate after:

- the rewritten object is stable enough,
- the branch or flow order is clear enough,
- or the downstream consumer explicitly requires a format conversion.

### 4. Bundle The Export Decision

When more than one representation format is in play, record:

- which formats were selected,
- which targets each format points to,
- and why other formats were omitted.

## Recommended Artifacts

### `xml-rewrite.xml`

Use when:

- the source explicitly asks for XML output,
- the rewritten prompt or problem statement must be wrapped for downstream consumption,
- or a tagged structure is more important than free-form prose.

Required top-level fields in contract terms:

- `rewritten_problem`

Useful optional structure:

- `source_artifact`
- `xml_root_tag`
- `target_consumer`

### `sequence-diagram.mmd`

Use when:

- the user explicitly asks for Mermaid sequence output,
- the current artifact already has a stable interaction order,
- or the execution / interaction flow needs a visual sequence export.

Required top-level fields in contract terms:

- `mermaid_sequence`

Useful optional structure:

- `source_artifact`
- `sequence_scope`
- `participant_map`

### `representation-bundle.json`

Use when:

- more than one representation format is relevant,
- the export step needs an explicit index,
- or downstream consumers should not guess what was exported.

Required top-level fields:

- `selected_formats`
- `xml_targets`
- `graph_targets`
- `logic_targets`
- `export_notes`

Useful optional structure:

- `triple_targets`
- `dag_targets`
- `sequence_targets`
- `omitted_formats`
- `selection_rationale`

## Activation

Enable this mode when:

- the user explicitly asks for XML, Mermaid, DAG, triple, or logic export,
- a downstream step explicitly needs one of those formats,
- or the current branch / interaction structure is stable enough that representation is now useful rather than premature.

Do not activate it just because an internal JSON artifact already exists. Representation mode is for explicit export intent or downstream format need.
