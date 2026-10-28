# Predicting Used-Tractor Auction Prices

**How much should a used tractor sell for, given its age, usage and specifications?**

This MSc dissertation uses auction records to estimate sale prices across different makes, model series and currencies. The first challenge was constructing a reliable set of actual sales from repeated listings. The second was testing whether a nonlinear model improved on a transparent regression benchmark.

I reduced **354,607 listings to 22,857 unique realised sales** and compared several models. On **3,429 unseen sales**, CatBoost reduced the **median absolute percentage error from 40.2% to 32.0%** versus quadratic regression. Performance was much weaker for rare or unseen tractor model series than for familiar ones.

[**Results and error analysis**](reports/RESULTS.md) · [**MSc dissertation**](reports/dissertation.pdf) · [**Analysis notebooks**](notebooks/)

## What I did

- Defined the sale sample, removed duplicate/invalid records and examined missing specifications.
- Built predictors from manufacture year, usage, make/model, country, currency, drive and equipment indicators.
- Compared regression, a decision tree, XGBoost and CatBoost using separate training, validation and test samples.
- Evaluated errors in native price units and examined where limited training examples made predictions less reliable.

## Results in context

Median absolute percentage error is the median of the individual absolute percentage errors; lower is better. The **8.2 percentage-point reduction** is a **20.5% relative reduction in that error measure**, not a 20.5% rise in sale prices or a measure of business savings.

| Test measure | CatBoost | Quadratic regression |
|---|---:|---:|
| Median absolute percentage error | **32.0%** | 40.2% |
| Predictions within 30% of actual sale price | **47.6%** | See dissertation |

| Model-series support in training | Test sales | CatBoost median percentage error |
|---|---:|---:|
| Common model series | 1,605 | **22.6%** |
| Rare or unseen series | 1,824 | **44.0%** |

The lower overall error does not make every valuation reliable. [Bootstrap uncertainty and currency-specific interpretation](reports/RESULTS.md).

![Final-test model comparison](docs/assets/test-comparison.png)

## Modelling details

The 70/15/15 split is stratified by currency and within-currency price group. Rare-category rules, missing-value handling and target transformations are learned from training data. After model selection, CatBoost and the quadratic comparator are refit on training plus validation data. Predictions are converted back to native currencies before evaluation.

Horsepower and transmission were investigated but excluded from the final models because too many records lacked them. CatBoost handles nonlinear effects and categorical information; its greater complexity is assessed against the simpler benchmark rather than assumed useful.

## Inspect or run

The executed notebooks and dissertation are readable without the source data. Full retraining needs the original listings dataset, which is not redistributed here. [Input instructions](data/README.md).

```bash
python -m pip install -r requirements.txt
jupyter lab
```

Run `notebooks/01_data_cleaning_and_eda.ipynb`, then `notebooks/02_model_training_and_testing.ipynb` using the working-directory instructions in the data guide.

## Scope

Transaction dates are unavailable. This random split tests generalisation within the observed sample, not future-market prices or price drift. Raw monetary errors across different currencies cannot meaningfully be pooled. Feature importance is predictive dependence, not a causal price premium.

**Author:** Fakhruddin Hakim Hussain · MSc Statistics with Data Science, University of Edinburgh · [Portfolio](https://github.com/Fakhruddin12)
