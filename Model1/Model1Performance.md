# Model 1 Performance – Logistic Regression

## Overview

This document presents the performance results of Model 1, a Logistic Regression classifier applied to the UCI Bank Marketing dataset.

The model was developed to predict whether a customer would subscribe to the bank product, where:

- `0` represents a customer who did not subscribe.
- `1` represents a customer who subscribed.

The performance calculations are contained in:

`Model1/model1_logistic_regression.ipynb`

The notebook loads the preprocessed training and testing datasets, trains the Logistic Regression model, generates predictions, and calculates the performance metrics reported below.

## Evaluation Metrics

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix
- Classification report

Because the target variable is imbalanced, accuracy was not considered in isolation. Precision, recall, F1-score and ROC-AUC were also used to assess the model's ability to identify the minority subscription class.

## Results

| Metric | Result |
|---|---:|
| Accuracy | 0.8458 |
| Precision | 0.4181 |
| Recall | 0.8110 |
| F1-score | 0.5518 |
| ROC-AUC | 0.9097 |

## Interpretation

The Logistic Regression model achieved an accuracy of approximately 84.58%, meaning that approximately 84.58% of all test observations were classified correctly.

The precision for the positive subscription class was approximately 41.81%. This means that among customers predicted as subscribers, approximately 41.81% actually subscribed.

The model achieved a recall of approximately 81.10%. This indicates that the model correctly identified a large proportion of the customers who actually subscribed.

The F1-score was approximately 55.18%, reflecting the balance between precision and recall.

The ROC-AUC score of approximately 0.9097 indicates that the model has a strong ability to distinguish between subscribing and non-subscribing customers across different classification thresholds.

## Confusion Matrix

The confusion matrix was:

```text
[[6791, 1194],
 [ 200,  858]]
```

This corresponds to:

| Outcome | Count |
|---|---:|
| True Negatives | 6,791 |
| False Positives | 1,194 |
| False Negatives | 200 |
| True Positives | 858 |

The model correctly identified 858 subscribers and missed 200 subscribers.

However, it also incorrectly classified 1,194 non-subscribers as subscribers. This helps explain the relatively high recall but lower precision.

## Classification Report

For the positive `Yes` class, the model achieved:

- Precision: 0.42
- Recall: 0.81
- F1-score: 0.55
- Support: 1,058

For the negative `No` class, the model achieved:

- Precision: 0.97
- Recall: 0.85
- F1-score: 0.91
- Support: 7,985

The model therefore performs strongly in identifying actual subscribers, but it produces a comparatively high number of false-positive predictions.

## How to Reproduce the Results

Open:

`Model1/model1_logistic_regression.ipynb`

Ensure the processed datasets are available in the `Preprocessing` folder:

- `X_train_processed.csv`
- `X_test_processed.csv`
- `y_train_processed.csv`
- `y_test_processed.csv`

Run all notebook cells from top to bottom.

The resulting performance metrics are saved in:

`Model1/model1_results.csv`