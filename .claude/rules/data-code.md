---
paths:
  - "notebook/**/*.ipynb"
  - "workflow/**/*.py"
---

# Data Code Rules

## Before writing ANY code that loads data
1. Run `head -1 <filepath>` or equivalent to verify actual column names.
   NEVER guess or assume column names.
2. Grep for existing code that loads the same data file. Reuse column
   names, filters, and variable names exactly.
3. If the data file is new (never loaded before), read the first few rows
   and print columns before writing analysis code.

## No silent shortcuts
- Never use `nrows`, sampling, partial reads, or hardcoded subsets without
  explicitly telling the user and getting approval.
- If a speed optimization is needed, propose it first: "This file has X
  rows, loading will be slow. Should I limit to Y rows or use usecols?"

## Variable flow across cells
- When a notebook cell computes results that later cells reference, verify
  the variable name is defined and stored.
- Before writing a summary/figure cell, list all variables it depends on
  and confirm each is defined in a prior cell.

## Matching existing analysis
- When replicating a published method (e.g., Frank et al.), read the
  original paper's methods section AND supplementary BEFORE writing code.
  Do not rely on memory.
- If the paper references supplementary materials for methodology details,
  ask the user for that file before proceeding.

## Verification
- Every data-loading cell must print: row count, column count, key column
  names, and any filter applied.
- Every regression cell must print: N, R², key coefficients with p-values.
