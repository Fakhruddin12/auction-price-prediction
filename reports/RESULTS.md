# Results and evidence

The dissertation reports 3,429 held-out test sales. CatBoost was selected using the validation set, then refitted on combined training and validation data. Quadratic regression was refitted on the same sample as the substantive benchmark.

| Metric | CatBoost | Quadratic regression |
|---|---:|---:|
| Test MedAPE | 32.0% | 40.2% |
| Predictions within 20% of actual price | 34.2% | See dissertation |
| Predictions within 30% of actual price | 47.6% | See dissertation |

The relative MedAPE reduction is 20.5%; the absolute improvement is 8.2 percentage points. These are different summaries of the same comparison.

An accompanying saved bootstrap table reports a MedAPE improvement interval of 6.60–10.06 percentage points. This is a resampling analysis conditional on the test sample; it is not evidence about future market drift. [Saved bootstrap table](test_medape_bootstrap_ci.csv).

| Model-series support | Test n | CatBoost MedAPE |
|---|---:|---:|
| Common in training | 1,605 | 22.6% |
| Rare or unseen | 1,824 | 44.0% |

Native-currency errors are reported separately in [the dissertation](dissertation.pdf). Pooling raw monetary MAE across different currencies would be misleading. Feature importance measures predictive reliance, not causal price premiums.

Evidence is preserved from the supplied dissertation and executed notebooks. Full retraining requires the original listings dataset and is not claimed as part of the portfolio packaging validation.
