# AI-Assisted Research — Starter Kit

Copy-paste starter for setting up a research project with Claude Code.
From the *AI-Assisted Research Workshop*.

## How to use

**1. Scaffold the folders.** Open Claude Code in an empty project folder and paste
the contents of [`folder-structure.txt`](folder-structure.txt). Claude will create
the whole layout for you.

**2. Drop in the rules.** Copy [`CLAUDE.md`](CLAUDE.md) into the project root and
replace `[YOUR PROJECT NAME]`. Trim or add rules to fit your field — it's a starting
point, not a fixed template.

That's it. Claude reads `CLAUDE.md` at the start of every session, so your project
context and conventions travel with you.

## What's inside

| File | Purpose |
| --- | --- |
| `CLAUDE.md` | Project rules & context, loaded every session (< 200 lines) |
| `folder-structure.txt` | The folder layout — paste it to Claude to scaffold |

## Why this structure

- **`data/raw/` is read-only** — original data never gets modified.
- **`workflow/` is a numbered pipeline** — run order is baked into filenames.
- **Move, don't delete** — retire files to `deprecated/` or `trash/`, never `rm`.
- **`uv` for the Python env** — reproducible, fast.
