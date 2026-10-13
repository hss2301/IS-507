### Related scenario estimates (context only)

Birthal et al.'s conditional climate projections and Gulati et al.'s price-deficiency-payment cost scenarios supply context, not baseline results for this study. Gulati et al. estimate potential costs of Rs 56,518 crore, Rs 1.13 lakh crore and Rs 1.69 lakh crore if market prices are 10%, 20% or 30% below MSP, respectively, under their national-scale scenario assumptions. These figures should not be described as observed fiscal expenditure or causal effects.



### Predictive hypotheses

**H1 - Incremental value of biophysical and agricultural features.** *H0:* Adding weather, soil, irrigation and agricultural-input variables does not reduce out-of-time MAE/RMSE relative to the historical-only benchmark. *H1:* The expanded feature set reduces holdout MAE (the primary metric), with RMSE reported as a secondary metric and gains broken down by crop and region.

**H2 - Incremental value of structural features.** *H0:* Socioeconomic, infrastructure and livestock variables add no predictive value beyond H1's biophysical/agricultural model. *H1:* Adding these variables reduces holdout MAE relative to the biophysical/agricultural model; RMSE is reported as a secondary metric. Feature-group comparisons must use identical test observations and forecast cut-offs.



## 6. Causal strategy, hypotheses and decision gates

### Causal analysis

Causal estimation will be pursued only after selecting a specific intervention or exposure with measurable timing, geographic coverage and a credible comparison group. District and year fixed effects can account for time-invariant district differences and common shocks, but fixed effects alone do not eliminate time-varying confounding or make a relationship causal. A Difference-in-Differences design requires a defensible parallel-trends assumption and treatment-timing diagnostics; staggered rollouts require methods suited to heterogeneous treatment timing. Regression discontinuity is appropriate only when assignment follows an identifiable threshold and continuity near that threshold is defensible. Where these conditions do not hold, findings should be reported as associations or the causal question should be deferred (Angrist & Pischke, 2009; Imbens & Rubin, 2015).

The policy corpus can support this work only after a transparent coding protocol extracts scheme, instrument, announcement and implementation dates, eligibility, covered geography, target population and intensity. A language model may assist extraction, but a human-reviewed sample, source traceability and coding-error checks are required. Policy presence in a document is not, by itself, a measured district-level treatment. Where a credible design exists, report pre-trends, placebo or falsification tests, alternative specifications and uncertainty; align standard errors with the level at which treatment is assigned.

### Causal hypotheses

**H3 - Market connectivity or credit access and productivity (exploratory).** For a pre-specified improvement in market connectivity or credit access that is plausibly exogenous, *H0* is a zero causal effect on yield; *H1* is a positive average effect on yield. Road density and bank-office counts are imperfect proxies and may reflect broader development. Estimate separate intervention-specific effects rather than treating unlike proxies as a single treatment. Proceed only if a policy change, natural experiment or other defensible source of variation can be documented.

**H4 - Agricultural policy and yield outcomes.** For a clearly defined intervention with measurable implementation and exposure, *H0* is no causal effect on district-level crop yield; *H1* is an increase in mean yield. Yield variability may be assessed as a pre-specified secondary outcome, not blended into the primary test. Difference-in-Differences or regression discontinuity will be used only when its identifying assumptions fit the intervention. The project will not infer that all post-2017 policies generated a common structural gain or project gains without a defensible counterfactual.

<!-- PAGE BREAK -->

### Decision gates and limits

1. **Gate A - Data audit:** reconcile source vintages and district keys; validate outcome definitions; publish missingness, merge and imputation diagnostics.
2. **Gate B - Prediction:** establish historical-only benchmarks and common time-based holdouts; quantify feature-group improvements and geographic/crop variation.
3. **Gate C - Causality:** select one treatment at a time, document the assignment mechanism and test assumptions before reporting causal estimates.
4. **Gate D - Prices:** proceed only if crop-market-time prices are sufficiently complete, comparable and available at the intended forecast cut-off.

The project's defensible promise is a transparent framework and credible tests, not a pre-committed model winner, causal effect or price-forecasting result.

## References

Angrist, J. D., & Pischke, J.-S. (2009). *Mostly harmless econometrics: An empiricist's companion*. Princeton University Press.

Birthal, P. S., Khan, T., Negi, D. S., & Agarwal, S. (2014). Impact of climate change on yields of major food crops in India: Implications for food security. *Agricultural Economics Research Review, 27*(2), 145-155. [https://doi.org/10.5958/0974-0279.2014.00019.6](https://doi.org/10.5958/0974-0279.2014.00019.6)

Dharmaraja, S., Jain, V., Anjoy, P., & Chandra, H. (2020). Empirical analysis for crop yield forecasting in India. *Agricultural Research, 9*(1), 132-138. [https://doi.org/10.1007/s40003-019-00413-x](https://doi.org/10.1007/s40003-019-00413-x)

Government of India, Ministry of Finance. (2026). *Economic Survey 2025-26, Chapter 6: Agriculture and food management*. [https://www.indiabudget.gov.in/economicsurvey/doc/eschapter/echap06.pdf](https://www.indiabudget.gov.in/economicsurvey/doc/eschapter/echap06.pdf)

Gulati, A., Chatterjee, T., & Hussain, S. (2018). *Supporting Indian farmers: Price support or direct income/investment support?* (Working Paper No. 357). Indian Council for Research on International Economic Relations. [https://icrier.org/pdf/Working_Paper_357.pdf](https://icrier.org/pdf/Working_Paper_357.pdf)

India Brand Equity Foundation. (2026). *Food processing industry in India*. [https://www.ibef.org/industry/food-processing](https://www.ibef.org/industry/food-processing)

International Crops Research Institute for the Semi-Arid Tropics. (n.d.). *District-level database for Indian agriculture*. [https://www.icrisat.org/public/resources/data/district-level-data](https://www.icrisat.org/public/resources/data/district-level-data)

Imbens, G. W., & Rubin, D. B. (2015). *Causal inference for statistics, social, and biomedical sciences: An introduction*. Cambridge University Press. [https://doi.org/10.1017/CBO9781139025751](https://doi.org/10.1017/CBO9781139025751)

Jabed, M. A., & Murad, M. A. A. (2024). Crop yield prediction in agriculture: A comprehensive review of machine learning and deep learning approaches, with insights for future research and sustainability. *Heliyon, 10*(24), Article e40836. [https://doi.org/10.1016/j.heliyon.2024.e40836](https://doi.org/10.1016/j.heliyon.2024.e40836)

Tata-Cornell Institute. (n.d.). *Data: District-level database for Indian agriculture and allied sectors*. [https://tci.cornell.edu/data/](https://tci.cornell.edu/data/)

