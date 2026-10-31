# Auction-price prediction — LinkedIn Projects entry

## Project name
Auction-Price Prediction for Used Tractors

## Description
Built an evaluated machine-learning pipeline for used-tractor auction prices, constructing 22,857 distinct sale records from 354,607 repeated listings and handling missing specifications across five currencies.

Compared additive and quadratic regression, a decision tree, XGBoost and CatBoost using separate training, validation and test partitions. Training-only category rules and currency-scaled log-price targets controlled preprocessing. After validation selection, CatBoost and the quadratic comparator were refitted on the same development sample.

On 3,429 held-out sale records, CatBoost achieved median absolute percentage error of 31.96%, versus 40.18% for quadratic regression: an 8.22-percentage-point improvement, or 20.45% relative reduction. A paired 10,000-resample bootstrap gave a 95% interval of 6.60–10.06 points for the difference.

Analysed currency and rare-series failure modes, restored both fitted models and reproduced every saved test prediction. Performance remains limited: only 47.6% of predictions are within 30% of actual price, and missing transaction dates and asset IDs prevent a future-market or asset-disjoint claim.

## Skills to associate
Python; Machine Learning; Regression Analysis; Data Cleaning; Feature Engineering

## Project URL
https://github.com/Fakhruddin12/auction-price-prediction

## Media attachment
- File: Auction_Price_Project_Report.pdf
- Title: Used-Tractor Auction Prices — Methods and Evaluation
- Description: Plain research report covering sale-sample construction, currency-scaled targets, validation selection, quadratic controls, paired bootstrap intervals and currency/rare-series error analysis. Separates restored-model replay from retraining and future-market validation.

## Dates and association
Enter actual project dates from your records. The report assembly date and data validity cutoff are not project completion dates. Associate with the MSc only using the dissertation's actual academic record.

## Public report link
https://github.com/Fakhruddin12/auction-price-prediction/blob/master/reports/PROJECT_REPORT.pdf

## Evidence notes — not part of the pasted description
- Test split: 3,429 records; train 15,999; validation 3,429. Random stratification by currency and within-currency log-price quintile, seed 42.
- Selection objective is validation MAE on the scaled log-price target, not native-price MedAPE.
- Common-series MedAPE: 22.55%; rare/unseen: 44.02%. GBP: 57.52%; the small AUD slice favours quadratic regression.
- Usage hours missing: 25.1%. The 74.9% figure is availability.
- 135 test predictor profiles also occur in initial training; this does not prove identical physical assets, but identities are not available for grouped validation.
- Both archived fitted models reproduce all 3,429 saved predictions each; nine checks and all four 10,000-resample bootstrap intervals pass. Raw cleaning and full selection were not rerun.
- No valuation savings, causal equipment premium, live deployment or new future-sale evaluation is claimed.
