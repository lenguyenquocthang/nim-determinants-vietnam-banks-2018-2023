# Determinants of Net Interest Margin in Vietnamese Joint-Stock Banks, 2018–2023

Panel-econometric study of bank net interest margin (NIM) for **27 listed Vietnamese joint-stock commercial banks over 2018–2023 (N·T = 162)**, with a case focus on PGBank. Part of my [quant portfolio](https://github.com/lenguyenquocthang/quant-portfolio); a related study is [nim-determinants-vietnam-banks](https://github.com/lenguyenquocthang/nim-determinants-vietnam-banks).

**Pages:** [Landing](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks-2018-2023/) · [Scroll presentation](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks-2018-2023/presentation/) · [Research report](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks-2018-2023/report/)

## Specification

$$\mathrm{NIM}_{it}=\alpha_i+\beta_1\,\mathrm{CAP}_{it}+\beta_2\,\mathrm{SIZE}_{it}+\beta_3\,\mathrm{NPL}_{it}+\beta_4\,\mathrm{INF}_t+\beta_5\,\mathrm{GDP}_t+\beta_6\,\mathrm{COVID}_t+\varepsilon_{it}$$

CAP is equity capital size (%), SIZE is $\log_2$(total assets), NPL the non-performing loan ratio (%), INF and GDP are year-level macro series, and COVID is a dummy for 2019–2022. Estimated by Pooled OLS, FEM, REM and FGLS (Stata 17).

## Model selection and diagnostics
The F test and Breusch–Pagan LM reject pooled OLS; Hausman ($p=0.0036$) selects FEM over REM. Residual diagnostics reject homoskedasticity, serial independence (autocorrelation $p=0.0009$) and cross-sectional independence ($p=0.0092$); mean VIF is 1.32. The reported estimator is therefore **FGLS** (Stata `xtgls`), which addresses the three violations.

## Results (FGLS)
| Variable | Coef. | Inference | Expected sign | Reading |
|---|---|---|---|---|
| CAP | +0.185 | $z=7.06$ | + | supported |
| SIZE | +0.294 | $z=6.21$ | + | supported |
| NPL | −0.052 | $z=-4.29$ | − | supported |
| INF | −0.053 | $p=0.249$ | ± | insignificant, consistent with two-way expectation |
| GDP | +0.031 | $p=0.010$ | − | **opposite sign**, not supported |
| COVID | +0.128 | $p=0.044$ | − | **opposite sign**, not supported (sign corrected, see `ERRATA.md`) |

Standardised effects: CAP +0.41, SIZE +0.33, NPL −0.10, others below 0.06 in absolute value. NIM has mean 3.26% and range 0.59–9.43%; most of the variance is between banks.

## Independent re-estimation (Python)
FEM with bank-clustered errors on the data appendix: NPL −0.055 ($p<0.001$); within SIZE and CAP effects are weak while between effects are large (0.454 and 0.317), i.e. these variables explain cross-sectional rather than time-series variation. With G = 6 year clusters, a wild bootstrap by year gives COVID $p=0.014$ and GDP $p=0.084$. A rolling-origin forecast test finds FEM **not** better than a naive benchmark out of sample (RMSE 0.72 vs 0.55): the specification is explanatory, not predictive.

## Limitations
27 of 33 banks and six years; INF, GDP and COVID take only six distinct values, so their effects are weakly identified and cluster-robust inference is fragile; COVID is a single dummy; NPL zeros in three bank-years are missing values; results describe associations, not causal effects. Statements on PGBank are limited to what the source study and the data appendix show.

## Repository
| Path | Content |
|---|---|
| `presentation/` | Interactive scroll presentation (VI/EN, light/dark, equations under "Technical") |
| `report/` | Research report with Appendix A (data reconciliation) and B (independent check) |
| `data/` | Balanced panel: NIM, CAP, SIZE, NPL, INF, GDP, COVID |
| `reestimation/` | Python code: Pooled/FEM/REM, clustered and wild-bootstrap inference, rolling-origin test |
| `ERRATA.md`, `SUMMARY.md` | Reconciliation notes; one-page summary |

```bash
cd reestimation && pip install -r requirements.txt
python run.py --data <practicum_workbook.xlsx> --out results && python make_figures.py
```
The source workbook is not redistributed; `data/` holds the cleaned panel used on the pages.
