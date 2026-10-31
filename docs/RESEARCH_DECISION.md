# Auction-Price Prediction: research decision

Reviewed 31 October 2026. This note separates the supported result from the next research decision.

## Decision

Retain CatBoost as the stronger cross-sectional benchmark; require dated, asset-disjoint validation before future-market valuation claims.

## Strongest relevant comparison

On 3,429 held-out records, CatBoost MedAPE is 31.96% versus quadratic regression 40.18% (8.22 percentage points, 20.45% relative reduction). Paired 10,000-resample CI for the difference is 6.60–10.06 points. Only 47.6% of predictions are within 30% of recorded prices.

## Evidence limits

Rare/unseen-series MedAPE is 44.02%, versus 22.55% for common series. GBP MedAPE is 57.52%; quadratic regression wins the small AUD slice. Transaction dates and physical-asset IDs are absent, and 135 test predictor profiles also occur in the initial training sample. This is a random record holdout, not independent future assets.

## Checks and changes

Both archived fitted models reproduce all 3,429 saved predictions each. Nine evidence checks and all four recomputed bootstrap intervals pass. Raw cleaning and full selection were not rerun. The training notebook is published with source only, without embedded samples or executed outputs. The public repository receives aggregate verification only; the privately restored data and weights are not redistributed.

## Next independent milestone

Obtain sale dates and stable asset/lot identifiers, freeze a later grouped sample, retain the quadratic control and evaluate calibrated intervals and a review/abstention policy against an explicit valuation tolerance.

[Project report](../reports/PROJECT_REPORT.pdf) · [Prepared LinkedIn Projects entry](../reports/LINKEDIN_PROJECT_ENTRY.md)

The report and entry are portfolio summaries. Original experimental source version: `97773747835a98cea5b13d818cd37bd17b7cfa3a`. The report records verification scope and distinguishes earlier numerical replays from this presentation/code review.
