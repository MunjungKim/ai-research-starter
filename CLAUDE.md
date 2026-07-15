# CLAUDE.md

<!-- Keep this short — Claude loads it every session. Target under 200 lines. -->

**Project:** [YOUR PROJECT NAME]

If a named skill or tool is unavailable, use the closest available workflow.

I'm a researcher, not a software engineer. Explain choices in plain language,
and push back on bad ideas instead of agreeing by default. Never fabricate data or results.

---

## Core Principles

- **Plan first** — enter plan mode before non-trivial tasks; save the plan to `notes/plans/`.
- **Verify after** — actually run the code and confirm the output at the end of every task.
- **Single source of truth** — `data/raw/` is authoritative; everything downstream derives from it.
- **Feed mistakes back** — when I correct you, record it: add a rule here, or a
  `[LEARN] wrong → right` note to `notes/MEMORY.md`, so it doesn't happen twice.

---

## Folder Structure

```
project/
├── CLAUDE.md            # this file — context & rules
├── .claude/             # settings, skills, rules, hooks
├── seeds/               # seed papers & sources
├── data/raw/            # original data — READ-ONLY, never modify
├── ideas/               # one file per research idea
├── workflow/            # numbered pipeline — run in order
├── notebook/            # numbered analysis notebooks
├── drafts/              # writing (.tex .md .docx)
├── papers/figures/      # manuscripts + visual outputs
├── results/             # large / heavy outputs
├── notes/               # project hub, plans, MEMORY.md
├── deprecated/ · trash/ # archive & soft-delete — never rm
└── pyproject.toml · uv.lock   # Python env via uv
```

- `data/raw/` is read-only. Write derived data elsewhere.
- `workflow/` runs in numbered order — don't reorder scripts.
- Move, don't delete: retire files to `deprecated/` or `trash/`. Never `rm`.
- Human-readable folder and file names.

---

## Commands

```bash
uv run workflow/01_*.py        # run a pipeline step (in order)
uv add <package>               # add a dependency
uv run jupyter lab             # open notebooks
```

---

## Use Skills When Relevant

At the start of a task, check for a clearly relevant skill and invoke it first:
- Vague research idea / sharpening an RQ → `sharpen-my-rq`
- Planning a paper → `plan-my-paper`
- New dataset → `datacheck`
- Figures / plots → `viz`
- Reference & citation check → `check-refs`
- Manuscript review → `critique-manuscript`

Use `AskUserQuestion` (via `ToolSearch`) for structured questions; fall back to plain text if unavailable.

---

## Think Before Acting

- State your assumptions. If uncertain, ask — don't guess.
- Multiple interpretations → present them, don't pick one silently.
- If a simpler analysis exists, say so.
- Before writing code, tell me what you think I'm asking and how you'll approach it.

---

## Keep Changes Simple & Surgical

- No abstractions, config, or error handling beyond what the task needs.
- Don't refactor, rename, or reformat code you weren't asked to touch. Match the existing style.
- Remove only the orphans your own changes created.
- Exception: figures and writing should land as a cohesive whole, not fragmented edits.

---

## Reproducible Evidence

When running substantive analysis (not one-liners or sanity checks):
- Capture output via `tee` to `logs/YYYY-MM-DD_HH-MM-SS_<description>.log`.
- Keep `logs/` in `.gitignore`. Never commit logs.
- Never report a result without evidence it actually ran — a log, notebook output, or saved figure.

---

## Git

- Commit only when I ask.
- Never include `Co-Authored-By` in commit messages.
