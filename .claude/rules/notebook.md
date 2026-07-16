<!--
  Path-scoped rule — loads only when Claude touches notebooks (see `paths` below),
  not every session. This keeps CLAUDE.md lean.
  How rules work (official docs): https://code.claude.com/docs/en/memory#organize-rules-with-claude%2Frules%2F
-->
---
paths:
  - "notebook/**"
  - "**/*.ipynb"
---

## Before writing (planning stage)
- Before writing any code, first explain what you'll do, why,
  and in what order — in plain, undergraduate-level terms — and ask for approval.
- Do not write any code until the user approves the plan.
- Once approved, record the plan as markdown at the top of the notebook.

## Package usage
- Before introducing any package beyond standard tools, ask first.
  (Familiar: pandas, numpy, matplotlib / in R: tidyverse, survey, lavaan)
- When proposing a new package, explain in one line why it's needed.

## Code style
- Assume I only know undergraduate-level R/Python. Avoid clever idioms;
  prefer spelled-out, multi-line code over dense one-liners.
- One cell does one thing. Put a one-line markdown note above each cell.
- When you first use an unfamiliar function, add a comment explaining it.
  e.g. # pivot_longer: reshapes data from wide to long

## After writing (explanation stage)
- Once the code is done, pick the 3 functions or patterns I'm most likely
  not to know and explain them separately.

## Naming & organization
- Inside `notebook/`, group each task in a purpose-named folder, with a date suffix:
  `<topic>_YYYYMMDD/` — e.g. `turnout_20260716/`.
  Add the date because the same analysis often gets revisited and re-run
  differently over time, so each pass keeps its own dated folder.
- Inside that folder, number the notebooks in run order with a `00_`, `01_`, `02_` prefix
  — e.g. `00_explore.ipynb`, `01_clean.ipynb`, `02_model.ipynb`.
