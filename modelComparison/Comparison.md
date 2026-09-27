# Model Comparison – Logistic Regression vs Random Forest

## Overview

This document compares the performance of the two machine learning models developed for the Bank Marketing dataset:

1. Logistic Regression
2. Random Forest Classifier

The performance comparison is based on the same test dataset and the same evaluation measures.

The comparison notebook is:

`ModelComparison/model_comparison.ipynb`

## Performance Comparison

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Accuracy | 0.8458 | 0.8966 |
| Precision | 0.4181 | 0.5523 |
| Recall | 0.8110 | 0.6134 |
| F1-score | 0.5518 | 0.5813 |
| ROC-AUC | 0.9097 | 0.9266 |

## Accuracy

Random Forest achieved higher accuracy:

- Logistic Regression: 84.58%
- Random Forest: 89.66%

The Random Forest therefore made more correct predictions overall on the test dataset.

## Precision

Random Forest also achieved higher precision:

- Logistic Regression: 41.81%
- Random Forest: 55.23%

This means the Random Forest produced fewer false-positive subscription predictions relative to the number of customers it predicted as subscribers.

## Recall

Logistic Regression achieved substantially higher recall:

- Logistic Regression: 81.10%
- Random Forest: 61.34%

This means Logistic Regression identified a larger proportion of the customers who actually subscribed.

The confusion matrices support this observation. Logistic Regression produced only 200 false negatives, while Random Forest produced 409 false negatives.

## F1-score

Random Forest achieved a slightly higher F1-score:

- Logistic Regression: 55.18%
- Random Forest: 58.13%

This indicates that Random Forest provided a somewhat stronger balance between precision and recall on the test dataset.

## ROC-AUC

Random Forest also achieved a higher ROC-AUC:

- Logistic Regression: 0.9097
- Random Forest: 0.9266

Both models demonstrated strong discriminatory ability, while the Random Forest achieved the higher ROC-AUC value.

## Confusion Matrix Comparison

### Logistic Regression

```text
[[6791, 1194],
 [ 200,  858]]
```

### Random Forest

```text
[[7459, 526],
 [ 409,  649]]
```

| Outcome | Logistic Regression | Random Forest |
|---|---:|---:|
| True Negatives | 6,791 | 7,459 |
| False Positives | 1,194 | 526 |
| False Negatives | 200 | 409 |
| True Positives | 858 | 649 |

The Logistic Regression model identified more actual subscribers but produced substantially more false-positive predictions.

The Random Forest produced fewer false positives and more true negatives, but it failed to identify more of the actual subscribers.

## Overall Interpretation

The two models demonstrate different performance characteristics.

Logistic Regression provides higher recall and therefore identifies a larger proportion of actual subscribers. This may be useful in situations where missing a potential subscriber is considered more costly than contacting additional customers.

Random Forest provides higher accuracy, precision, F1-score and ROC-AUC. It also produces substantially fewer false positives, indicating that its positive predictions are more selective.

The preferred model therefore depends on the intended business objective and the relative cost of false positives and false negatives.

If the primary objective is to identify as many potential subscribers as possible, recall may receive greater emphasis.

If the objective is to reduce unnecessary interventions while maintaining stronger overall predictive performance, precision, F1-score and ROC-AUC may receive greater emphasis.

## Statistical and Performance Measures Used

The models were compared using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrices
- Class-specific precision and recall

These measures were selected because the target dataset is imbalanced and accuracy alone may not adequately describe performance on the minority subscription class.

## How to Reproduce the Comparison

The comparison notebook should load:

`Model1/model1_results.csv`

and:

`Model2/model2_results.csv`

It should then combine the results and generate a direct comparison table and chart.

Run:

`ModelComparison/model_comparison.ipynb`

from top to bottom.

The final comparison output can be saved as:

`ModelComparison/model_comparison_results.csv`