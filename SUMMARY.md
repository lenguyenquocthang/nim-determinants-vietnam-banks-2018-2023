# Summary

**Question.** Which factors explain the net interest margin of Vietnamese listed joint-stock banks, 2018–2023, and where does PGBank stand?

**Data.** 27 banks × 6 years = 162 observations. Dependent variable NIM (%). Regressors: CAP (equity capital size), SIZE (log₂ total assets), NPL (bad-loan ratio), INF, GDP growth, COVID dummy (2019–2022). Sources: bank financial statements, World Bank, SSI price boards.

**Descriptives.** NIM mean 3.26%, range 0.59% to 9.43% (about 16×). Sector mean 3.07% (2018), peak 3.59% (2022), 3.20% (2023). PGBank is below the sector mean in all six years; its rank among 27 moves 11, 12, 13, …, 24 (2021), 18 (2023).

**Model choice.** F and Breusch–Pagan reject pooled OLS; Hausman (p = 0.0036) chooses FEM over REM. Residuals show heteroskedasticity, autocorrelation (p = 0.0009) and cross-sectional dependence (p = 0.0092); mean VIF 1.32. Reported estimator: FGLS.

**Findings (FGLS).** CAP +0.185 (z 7.06), SIZE +0.294 (z 6.21), NPL −0.052 (z −4.29), GDP +0.031 (p 0.010), COVID +0.128 (p 0.044), INF −0.053 (p 0.249). Standardised: CAP +0.41, SIZE +0.33, NPL −0.10. H1–H4 supported, H5–H6 not.

**Independent check (Python, FEM, bank-clustered SE).** COVID +0.209 (p = 0.007) for a 2020–2022 window; wild bootstrap by year p = 0.014. GDP p = 0.084 under the bootstrap. A rolling-origin forecast test finds FEM no better than a naive benchmark out of sample (RMSE 0.72 vs 0.55), so the model is explanatory, not predictive.

**Limits.** 27 of 33 banks, 6 years, COVID only as a dummy, year-level macro variables take six distinct values, associations not causal effects.
