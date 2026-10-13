# Causal and Predictive Modeling of Indian Crop Yields and Agricultural Prices

*A district-level framework integrating agronomic, agro-meteorological, socioeconomic, and policy data*

**Project proposal | Research focus:** Out-of-time crop-yield prediction first; causal analysis only where identification is credible; price forecasting conditional on data readiness.

## 1. Background and motivation

Agricultural uncertainty in India affects farm incomes, food security, commodity markets, and the industries that procure, process, finance, insure, and distribute agricultural products. Agriculture and allied activities contribute nearly one-fifth of national income at current prices and account for 46.1% of the workforce (Government of India, Ministry of Finance, 2026; workforce share based on PLFS 2023-24). India's food-processing market was estimated at US$382.24 billion in FY2024-25 (India Brand Equity Foundation [IBEF], 2026). These facts make better information about agricultural supply economically consequential, although they do not themselves demonstrate that any particular forecasting model or policy is effective.

Food and consumer-goods businesses often make procurement, production, inventory, and budgeting decisions before harvest quantities are known. Public procurement creates a related planning problem: the Economic Survey notes that rice and wheat procurement has at times grown faster than food-security requirements, contributing to high buffer stocks and carrying costs (Government of India, Ministry of Finance, 2026, Box VI.5). Forecasts can inform decisions, but prediction and explanation must be kept distinct. A variable may improve forecasts without causing higher yields; causal claims require a defensible counterfactual design.

## 2. Aim and research questions

**Aim.** Build a reproducible district-level framework to benchmark crop-yield predictions, measure the incremental value of environmental and structural variables, and investigate selected causal questions. Treat price prediction as a secondary extension that proceeds only if market data pass a documented quality audit.

**Research questions**

- **RQ1 - Prediction:** How much do agro-meteorological conditions, soil, irrigation, fertilizer and other agricultural inputs improve out-of-time yield prediction beyond historical yield alone?
- **RQ2 - Generalization:** Do predictive gains persist across crops, regions and future years, or are they concentrated in particular crop-district systems?
- **RQ3 - Structural variables:** Do socioeconomic and infrastructure variables add predictive value beyond biophysical and agricultural features, and when can their relationship with productivity be interpreted causally?
- **RQ4 - Prices:** Are crop-, market- and time-specific price data sufficiently complete and comparable to support valid forecasting?
- **RQ5 - Policy:** Can a clearly defined agricultural intervention be linked to district-level yields or yield stability using a credible identification strategy?

The central deliverable is a validated yield-prediction pipeline and transparent evidence about what improves forecasts. Causal estimates and price forecasts are conditional outputs, not assumed deliverables.

<!-- PAGE BREAK -->

## 3. Literature foundation and research gap

Dharmaraja et al. (2020) compare regression and time-series approaches for pearl millet (*bajra*) in Alwar, Rajasthan. Their study motivates using crop-growth-stage weather information alongside a time-series structure. Birthal et al. (2014), examining Indian food crops, find that higher maximum temperatures adversely affect yields and that positive rainfall effects do not fully offset these impacts. Their climate-change projections suggest rice yields could be 15% lower and wheat yields 22% lower by 2100 under the study's scenario of significant temperature and rainfall change; these are conditional projections, not unconditional predictions. Jabed and Murad (2024) review machine-learning and deep-learning approaches, including Random Forest, Support Vector Machines, neural networks, CNNs and LSTMs, and emphasize the importance of data quality and crop- and place-specific context.

The policy and market context matters as well. Gulati, Chatterjee and Hussain (2018) estimate the potential national cost of scaling a price-deficiency payment scheme under explicit assumptions about minimum support prices (MSPs) and market-price shortfalls. Their scenario estimates illuminate possible fiscal exposure; they do not establish a causal effect of MSP or procurement policy on yields or prices. Government policy initiatives in irrigation, income support, credit, insurance and market access therefore motivate questions for evaluation, but their effects must be tested intervention by intervention.



### Research gaps addressed

**Gap 1 - Incremental predictive value and portability.** Prior studies establish that weather and time-series information can matter, but the project still needs a common, leakage-safe comparison of historical-yield baselines against nested groups of weather, agricultural-input and structural variables, evaluated on the same future-year holdout and reported across crops and regions. The contribution is a reproducible, multi-domain benchmark, not a claim that crop-yield prediction itself is new.

**Gap 2 - Prediction versus causal explanation.** Feature importance or correlation cannot show that irrigation, credit, roads or policy caused yield changes. Causal work requires a defined treatment, timing and comparison group, plus an identification argument and diagnostics. This is a separate empirical task from forecast evaluation (Angrist & Pischke, 2009; Imbens & Rubin, 2015).

**Gap 3 - Data feasibility and policy linkage.** The availability of consistently aligned crop-market prices has not yet been demonstrated. The policy corpus is also unstructured and cannot be treated as quantitative treatment data until scheme names, dates, target populations, geography, eligibility and implementation intensity have been extracted, checked and linked to outcomes. The project will document where these data permit analysis and where they do not.

**Expected contribution.** An auditable pipeline that states which features improve out-of-time forecasts, where that improvement generalizes, and which causal questions are or are not identified by the available variation. It will avoid presenting a model's predictive performance as proof of policy effectiveness.



## 4. Data, preparation and analytical readiness

### Sources and current inventory

The principal structured source is the District-Level Database for Indian Agriculture and Allied Sectors associated with ICRISAT and the Tata-Cornell Institute. It combines crop and agricultural outcomes with environmental, socioeconomic and infrastructure indicators. The current ICRISAT landing page describes 27 datasets, 571 districts and 1,030 variables; the project's working-file inventory reports 602 district entries across 20 states. These counts may reflect different vintages, geographic definitions or duplicate name/code variants and must not be treated as directly equivalent until the downloaded source version and district-boundary convention are recorded (ICRISAT, n.d.; Tata-Cornell Institute, n.d.).

The present project inventory comprises **26 CSV files**, nearly **400,000 cumulative rows across those files**, more than **300 fields/variables**, up to **34 years** of coverage, and a crop-outcome file with **18,060 rows**. These cumulative row counts are not the number of unique observations in the final analysis panel. After integration, two wide analytical matrices were prepared: a 175-column matrix combining agronomic and meteorological variables, and a 174-column matrix combining agronomic, socioeconomic, infrastructure and livestock indicators. Final row counts, coverage by crop and year, and the unique observational key still need to be documented in the audit log.

<!-- PAGE BREAK -->

### Operations already performed

Python and Pandas were used to standardize the source tables and integrate them with the core crop file. Join cardinality was explicitly considered to guard against accidental row multiplication. Values of **-1**, used in source fields to represent null or uncaptured data, were recoded as missing. Variable-level mean or median imputation has been applied to much of the merged data. These are completed preprocessing operations, but the fact that they were applied does not establish that they are statistically adequate.



### Validation required before modeling

1. **Keys and geography:** assert the intended crop-district-year key is unique; log row counts before and after every join; trace duplicated or unmatched keys; standardize district codes and names; record whether observations use apportioned historical boundaries or current districts.
2. **Missingness and imputation:** report missingness by variable, crop, district and year; inspect outliers and distributions; compare complete-case and alternative-imputation sensitivity where feasible. Fit imputation parameters on training data only and apply them to validation/test data, preventing information from future years leaking into model development.
3. **Measurement and timing:** check units, definitions, source vintages, yield consistency and implausible area/production combinations. Define the forecast cut-off before selecting features; observed weather or inputs unavailable at that cut-off cannot be presented as operational forecast predictors.
4. **Policy and price layers:** policy documents remain unstructured and require extraction plus human review. Price forecasting remains on hold until crop-market identifiers, dates, units, price concepts and temporal coverage are aligned and audited.

The data are therefore **integrated but not yet fully validated for inference**. The next gate is a reproducible data-quality report, not immediate high-complexity modeling.



## 5. Empirical strategy: prediction and published benchmarks

### Predictive design

**Unit and outcomes.** Use crop-district-year as the principal panel unit. Define yield consistently (including units and source measure); analyze production separately rather than treating production and yield as interchangeable. Select crops with adequate historical coverage and publish the inclusion rules. Fix a real forecast horizon and information cut-off for every model.

**Nested comparisons.** Start with transparent historical-only benchmarks: last-observed yield and a training-period district/crop trend or mean, as justified by the forecast task. Compare these with a simple regression/time-series benchmark, then add feature groups in sequence: (1) weather and soil; (2) agricultural inputs and irrigation; and (3) socioeconomic, livestock and infrastructure variables. Random Forest and XGBoost are candidate nonlinear models. RNN/LSTM or Transformer-style models should be attempted only if the number and length of comparable time series support them; model complexity is not evidence of better forecasts.

**Validation and metrics.** Split by time, keeping later years out of training, and tune only within the earlier training/validation period. Use rolling-origin tests if coverage permits; compare each feature set on the same test observations. Report MAE and RMSE as primary error metrics, with R-squared as a complementary measure, and break results down by crop and region. Record uncertainty and missing coverage rather than reporting a single pooled score alone. Imputation, scaling and feature selection must be fitted inside the training split. For weather variables, distinguish a retrospective estimate that uses realized growing-season weather from a forecast that could genuinely have been made before harvest.

### Established external benchmark - not a project result

Dharmaraja et al. (2020) used Alwar district pearl-millet yields from 1997-2013 for model development and **2014-2016 as a three-year validation set**. Reported MAE was **441.23 kg/ha** for simple regression (year as predictor), **118.03 kg/ha** for multiple regression, **91.92 kg/ha** for ARIMA and **50.67 kg/ha** for ARIMAX. Their ARIMAX specification combines time-series structure with a selected weather predictor. Within that particular validation exercise, ARIMAX's MAE was substantially lower than the simple-regression MAE. This is a useful published benchmark for motivating a time-aware, weather-informed comparison, but it is not directly comparable to this project's eventual scores: it covers one crop, one district and three validation years. **No model-performance baseline has yet been generated from the project's assembled datasets.**

<!-- PAGE BREAK -->

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
