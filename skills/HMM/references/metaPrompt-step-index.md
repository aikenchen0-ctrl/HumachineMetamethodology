# metaPrompt-step-index

## Purpose

This file is the typed companion for `references/metaPrompt.md`.

It keeps the maintained source scaffold explicit after the source moved from the old step-numbered draft into the current chapter-based `metaPrompt v2`.

## Why This Layer Matters

`references/metaPrompt.md` is now authoritative for:

- the chapter order,
- the main method chain,
- the placement of retrieval, generation, evaluation, and pluginization,
- and the shared symbol system used by the whole method.

Without a typed companion, later maintenance work keeps reconstructing:

- chapter order,
- chapter scope,
- chapter handoff,
- and where the mainline stops versus where extension planes begin.

## Compatibility Note

For downstream compatibility, the machine-readable JSON still keeps the historical field name:

- `normalized_step_id`

Even though the maintained source is now chapter-based rather than the old linear `步骤1-步骤8` scaffold.

## Recommended Use

Use this file when:

- maintaining source precedence,
- aligning `SKILL.md` back to the maintained source,
- mapping chapter outputs into contracts,
- or checking whether a later edit still reflects the maintained chapter scaffold.
