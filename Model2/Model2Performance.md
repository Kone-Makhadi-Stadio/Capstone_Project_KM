# Model 2 Performance – Random Forest

## Overview

This document presents the performance results of Model 2, a Random Forest classifier applied to the UCI Bank Marketing dataset.

The model predicts whether a customer will subscribe to the bank product.

The performance calculations are contained in:

`Model2/model2_random_forest.ipynb`

The notebook trains the Random Forest model, generates predictions and probabilities, evaluates model performance, and calculates feature importance.

## Evaluation Metrics

The Random Forest model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix
- Classification report

## Results

| Metric | Result |
|---|---:|
| Accuracy | 0.8966 |
| Precision | 0.5523 |
| Recall | 0.6134 |
| F1-score | 0.5813 |
| ROC-AUC | 0.9266 |

## Interpretation

The Random Forest model achieved an accuracy of approximately 89.66%.

Its precision for the positive subscription class was approximately 55.23%, meaning that more than half of the customers predicted as subscribers were actual subscribers.

The recall was approximately 61.34%, meaning that the model correctly identified approximately 61.34% of the customers who actually subscribed.

The F1-score was approximately 58.13%, reflecting the balance between precision and recall.

The ROC-AUC score was approximately 0.9266, indicating strong separation between the two target classes across classification thresholds.

## Confusion Matrix

The confusion matrix was:

```text
[[7459, 526],
 [ 409,  649]]
```

This corresponds to:

| Outcome | Count |
|---|---:|
| True Negatives | 7,459 |
| False Positives | 526 |
| False Negatives | 409 |
| True Positives | 649 |

Compared with the Logistic Regression model, the Random Forest produced fewer false positives but more false negatives.

## Classification Report

For the positive `Yes` class:

- Precision: 0.55
- Recall: 0.61
- F1-score: 0.58
- Support: 1,058

For the negative `No` class:

- Precision: 0.95
- Recall: 0.93
- F1-score: 0.94
- Support: 7,985

The model therefore provides a more balanced trade-off between precision and recall than the Logistic Regression model.

## Feature Importance

The most influential features in the Random Forest included:

| Feature | Importance |
|---|---:|
| `duration` | 0.3209 |
| `balance_to_age` | 0.0572 |
| `balance` | 0.0562 |
| `day` | 0.0535 |
| `age` | 0.0533 |
| `contact_unknown` | 0.0247 |
| `poutcome_success` | 0.0242 |
| `pdays` | 0.0236 |
| `previous_positive_outcome` | 0.0224 |
| `campaign` | 0.0202 |

The `duration` variable contributed substantially more importance than the other variables.

This should be interpreted carefully because `duration` may only be known once or after the contact has taken place. If the intended application requires prediction before contact, a future experiment should evaluate performance without this variable.

## How to Reproduce the Results

Open:

`Model2/model2_random_forest.ipynb`

Ensure the processed datasets are available in the `Preprocessing` folder and run all notebook cells from top to bottom.

The notebook saves:

- `model2_results.csv`
- `random_forest_feature_importance.csv`