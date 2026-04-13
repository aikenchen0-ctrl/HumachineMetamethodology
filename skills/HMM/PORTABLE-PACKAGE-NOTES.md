# Portable Package Notes

## Scope

This distributable package is intentionally limited to the runtime skill files:

- `SKILL.md`
- `agents/`
- `references/`

It does not include `artifacts/` because those files are historical iteration outputs and contain machine-specific absolute paths from the current workspace.

## GitHub Installer Entry

For the official Codex GitHub skill installer, the repository exposes an installer-friendly subpath:

- `skills/HMM`

Use that subpath instead of the repository root.
This keeps the install target aligned with the intended skill directory name:

- `~/.codex/skills/HMM`

After installation, the current directory is the unpacked runtime skill root.

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

The repository has completed the current reconstruction closeout.

That means:

- the portable package definition is already aligned to the new source,
- the official-installer-friendly GitHub entry is `skills/HMM`,
- and any new distributable zip should be regenerated from the current clean working tree before distribution.
