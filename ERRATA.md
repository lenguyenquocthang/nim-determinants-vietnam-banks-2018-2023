# Reconciliation notes (source study vs recomputation)

These notes list where the source tables and the recomputation from the data appendix differ, and how each is handled on the pages. They are working notes for transparency, not a criticism of the source.

| # | Topic | Source shows | Recomputation / handling |
|---|---|---|---|
| N-1 | COVID sign | FGLS coefficient −0.128 | The Stata `encode` assigned Có = 1, Không = 2 (alphabetical), which flips the sign. Correct reading: **+0.128**. H6 is not supported. |
| N-2 | COVID window | Described as the pandemic years | The flag covers **2019–2022**. With a 2020–2022 window the FEM estimate is +0.209 (p = 0.007). |
| N-3 | Table 4.4 scale | SIZE and COVID statistics | About 100× smaller than a recomputation from the appendix; the pages use recomputed values and label them. |
| N-4 | Mean inflation | Text quotes 3.25885 | That value is the NIM mean; mean inflation is **2.983**. |
| N-5 | Coefficient direction | Prose on some effects | Directions follow the signed coefficients in the tables, not the prose. |
| N-6 | Diagnostic tests | Prose and numbers differ in places | The p-values quoted on the pages are the numeric ones (Hausman 0.0036; autocorrelation 0.0009; cross-sectional 0.0092). |
| N-7 | NPL zeros | Three zero values | BVB 2018, VAB 2018 and VAB 2019 are **missing values** coded 0; they are flagged in the re-estimation. |
| N-8 | Variable definitions | SIZE | SIZE is **log₂**(total assets) (VCB 2018 ≈ 50), not ln. |
| N-9 | Chosen vs reported model | FEM selected by tests | FGLS is the model reported for the final coefficients because of the residual violations. |
| N-10 | Macro variables | INF, GDP, COVID | Year-level: only six distinct values each, so standard errors need care and effects are weakly identified. |

Pooled/FEM/REM coefficients shown on the presentation are recomputed from the data appendix (they match the replication code); FGLS coefficients are taken from the source tables.
