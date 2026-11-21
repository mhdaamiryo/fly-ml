# Capstone Report — CTR / Engagement Opportunity Scoring

- **Author:** Aamir
- **Lane:** CTR / Engagement Opportunity Scoring
- **Repo:** https://github.com/mhdaamiryo/fly-ml
- **Data release:** flyrank_pseudonymized_warehouse_release_v20260703

## 0. Abstract
This study asks whether prior search-performance signals can rank content items that will under-capture clicks in a subsequent 30-day period. It uses the pseudonymized FlyRank ML Internship warehouse and aggregates daily search observations into client-content features over 2 March–30 April 2026. A position-adjusted rule is compared with Logistic Regression and Random Forest using a client-grouped holdout and a future CTR outcome defined from training-client position bands. The measured model-versus-baseline results must be inserted after the executed notebook generates the aggregate metrics; no performance result is claimed before that run. The intended output is a reason-coded human-review queue, not an automatic publishing decision or a causal estimate of metadata changes.

## 1. Problem framing
Decision: which eligible content items should a human review first for possible CTR/snippet/intent mismatch? Unit: client-content pair. Output: ranked score, one action and reason code. False positives consume editorial time; false negatives may leave review opportunities undiscovered.

## 2. Data safety
Source: FlyRank/internship-warehouse, build flyrank_pseudonymized_warehouse_release_v20260703. Table: fact_content_daily_performance. Feature window 2026-03-02–2026-04-30; outcome window 2026-05-01–2026-05-31. Minimums: 500 prior impressions and 100 future impressions. Query-level fixed-window data and GA4 fields are excluded. IDs are grouping-only, never model inputs. No names, domains, URLs, titles, private queries, credentials or raw exports are published.

## 3. Baseline
Prior CTR is compared with the 25th percentile of positive prior CTR in the same prior-position band, calculated on training clients. The gap is multiplied by prior impressions. It is evaluated on the same client-held-out test rows as the models.

## 4. Model / analysis
Models: Logistic Regression and Random Forest. Features: prior impressions, prior clicks, prior CTR, recent-30 CTR, older-30 CTR, impression change, prior average position, prior position standard deviation, and prior days with impressions. Target: future CTR below the training-client 25th percentile of positive future CTR for the prior-position band. Future window, target fields and IDs are excluded from model features.

## 5. Evaluation
One 75/25 GroupShuffleSplit by client hash, random seed 42. Primary metrics: average precision and Precision@50; secondary metrics: ROC AUC, recall and F1. The executed notebook writes the test base rate and all metrics to docs/assets/capstone_results.json. Insert the actual output before treating the paper as final.

## 6. Interpretation
Interpretation must be filled from the executed feature-importance and error-summary outputs. Feature importance is predictive association, not causation. Negative or inconclusive comparisons should be reported plainly.

## 7. Recommendation
Use the ranked queue to prioritise human review only. Verify query intent, SERP context, brand mix, measurement coverage and volume before editing. Do not automatically rewrite or publish pages.

## 8. Reproducibility
Open work/notebooks/capstone.ipynb in Colab, add HF_TOKEN in Colab Secrets, and run all cells. Commit the executed notebook and aggregate-only JSON/SVG outputs under docs/assets. Keep work/outputs/capstone_ranked_queue.csv local and untracked. Seed 42.

## 9. Acknowledgments & data credit
Built on the [FlyRank ML Internship dataset](https://flyrank.ai).

## Completion gate
The notebook requires an authenticated run. Until the actual aggregate JSON and charts are generated and committed, model metrics and empirical conclusions are intentionally not claimed.
