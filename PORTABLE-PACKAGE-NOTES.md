# Portable Package Notes

## Scope

This distributable package is intentionally limited to the runtime skill files:

- `SKILL.md`
- `agents/`
- `references/`

It does not include `artifacts/` because those files are historical iteration outputs and contain machine-specific absolute paths from the current workspace.

## Portability Rule

The packaged runtime files were checked for:

- absolute Windows drive paths,
- fixed local workspace roots,
- and fixed package-name reference prefixes that would break after unpacking into a different directory.

The runtime package now uses relative paths so it can be unpacked on another computer without preserving the original local directory layout.

## Source Files

The package already includes local copies of:

- `references/metaPrompt.md`
- `references/agentic-nested-state-machine.opml`

so the receiver does not need your original local source directory in order to use the skill.

The maintained `references/metaPrompt.md` is now the chapter-based `metaPrompt v2` source scaffold.

## Current Packaging Note

The repository is still in active reconstruction.

That means:

- the portable package definition is already aligned to the new source,
- but any new distributable zip should be regenerated only after the current consolidation review and commit-preparation pass.
