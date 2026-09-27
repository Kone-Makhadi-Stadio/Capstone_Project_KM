# Model 2 – Random Forest Classifier

## 1. Overview

This folder contains the implementation of **Model 2: Random Forest Classifier** for the Bank Marketing Capstone Project SS2.

The purpose of the model is to predict whether a customer will subscribe to the bank product based on customer characteristics, financial information, previous campaign information, contact information, and engineered features.

The target variable is binary:

- `0` – Customer did not subscribe
- `1` – Customer subscribed

Random Forest was selected as the second model because it provides a nonlinear, tree-based alternative to the Logistic Regression model used in Model 1. It can model more complex relationships and interactions between variables without requiring these relationships to be specified manually.

---

## 2. Notebook

The Random Forest model is implemented in:

`model2_random_forest.ipynb`

The notebook performs the following steps:

1. Imports the required Python libraries.
2. Loads the preprocessed training and testing datasets.
3. Inspects and converts the target variable.
4. Checks for missing values.
5. Defines the Random Forest Classifier.
6. Trains the model using the training dataset.
7. Generates predictions for the test dataset.
8. Generates predicted probabilities.
9. Evaluates model performance.
10. Produces a confusion matrix.
11. Calculates feature importance.
12. Saves the model evaluation results and feature importance results.

---

## 3. Input Data

The model uses the datasets generated during the preprocessing stage:

- `X_train_processed.csv`
- `X_test_processed.csv`
- `y_train_processed.csv`
- `y_test_processed.csv`

The training data is used to fit the Random Forest model, while the test data is used for evaluating its performance on observations that were not used during training.

The test dataset contains **9,043 observations**, consisting of:

- 7,985 customers who did not subscribe.
- 1,058 customers who subscribed.

---

## 4. Model Technique

### Random Forest Classifier

Random Forest is an ensemble machine learning technique that combines predictions from multiple decision trees.

Instead of relying on a single decision tree, Random Forest creates multiple trees and combines their predictions to produce the final classification.

This approach can capture nonlinear relationships and interactions between predictors and can reduce some of the instability associated with using an individual decision tree.

The model was implemented using:

```python
RandomForestClassifier(
    n_estimators=200,
    max_depth=None,
    min_samples_split=2,
    min_samples_leaf=1,
    class_weight="balanced",
    random_state=42,
    n_jobs=-1
)
```

---

## 5. Hyperparameters

| Hyperparameter | Value | Description |
|---|---:|---|
| `n_estimators` | 200 | Number of decision trees created in the Random Forest |
| `max_depth` | None | Trees are allowed to grow without a manually specified maximum depth |
| `min_samples_split` | 2 | Minimum number of observations required to split an internal node |
| `min_samples_leaf` | 1 | Minimum number of observations required in a leaf node |
| `class_weight` | balanced | Automatically adjusts class weights according to class frequencies |
| `random_state` | 42 | Provides reproducibility |
| `n_jobs` | -1 | Allows available CPU cores to be used during training |

The `class_weight="balanced"` setting was used because the target variable is imbalanced, with considerably fewer customers subscribing than not subscribing.

---

## 6. Model Evaluation

The Random Forest model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Classification report
- Confusion matrix

The resulting performance was:

| Metric | Random Forest Result |
|---|---:|
| Accuracy | 0.8966 |
| Precision | 0.5523 |
| Recall | 0.6134 |
| F1-score | 0.5813 |
| ROC-AUC | 0.9266 |

---

## 7. Interpretation of Results

### Accuracy

The model achieved an accuracy of approximately **89.66%**.

This means that approximately 89.66% of the test observations were classified correctly.

Accuracy should not, however, be considered in isolation because the target classes are imbalanced.

### Precision

The model achieved a precision of approximately **55.23%** for the positive subscription class.

This means that, among customers classified by the model as subscribers, approximately 55.23% were actual subscribers.

### Recall

The model achieved a recall of approximately **61.34%** for the subscription class.

This indicates that the model correctly identified approximately 61.34% of the customers in the test data who actually subscribed.

### F1-score

The F1-score was approximately **58.13%**.

The F1-score combines precision and recall and is particularly useful when considering performance on an imbalanced target variable.

### ROC-AUC

The model achieved a ROC-AUC score of approximately **0.9266**.

This indicates strong discrimination between the subscription and non-subscription classes across classification thresholds.

---

## 8. Classification Report

The classification results for the two classes were:

| Class | Precision | Recall | F1-score | Support |
|---|---:|---:|---:|---:|
| No | 0.95 | 0.93 | 0.94 | 7,985 |
| Yes | 0.55 | 0.61 | 0.58 | 1,058 |

The results demonstrate that the model performs more strongly on the majority `No` class than on the minority `Yes` class.

The use of balanced class weights helps account for this imbalance during model training.

---

## 9. Confusion Matrix

The resulting confusion matrix was:

```text
[[7459, 526],
 [ 409, 649]]
```

This corresponds to:

| Outcome | Number |
|---|---:|
| True Negatives | 7,459 |
| False Positives | 526 |
| False Negatives | 409 |
| True Positives | 649 |

Therefore, the model correctly identified:

- **7,459 non-subscribers**, and
- **649 subscribers**.

The model incorrectly classified:

- **526 non-subscribers as subscribers**, and
- **409 subscribers as non-subscribers**.

For the positive subscription class, these results correspond to the observed recall of approximately 61.34%.

---

## 10. Feature Importance

Random Forest provides feature importance values that can be used to examine which variables contributed most strongly to the fitted model's predictions.

The most important features identified by the model included:

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

The `duration` variable had the highest feature importance in the fitted Random Forest model.

The engineered `balance_to_age` feature was also among the highest-ranked features, indicating that the engineered variable contributed information used by the model.

Feature importance should be interpreted as an indication of how much the Random Forest relied on each feature when making predictions and should not be interpreted as evidence that a feature causes subscription.

---

## 11. Important Consideration: Call Duration

The strongest feature identified by the model was `duration`, which represents the duration of the marketing contact.

This requires careful consideration when interpreting the model.

If the intended use of the model is to predict whether a customer is likely to subscribe **before the marketing call takes place**, the duration of that call would not yet be known.

Consequently, although `duration` contributes strongly to the current model's predictive performance, a future experiment could evaluate model performance without this variable if the intended business application requires predictions to be made before customer contact.

This distinction is important when assessing whether the model can be applied operationally.

---

## 12. Output Files

The notebook generates two main output files:

### Model Results

`model2_results.csv`

This contains:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

### Feature Importance

`random_forest_feature_importance.csv`

This contains each processed feature and its Random Forest importance score.

---

## 13. How to Run the Model

Open:

`Model2/model2_random_forest.ipynb`

Ensure that the required preprocessed files exist in the `Preprocessing` folder:

```text
Preprocessing/
├── X_train_processed.csv
├── X_test_processed.csv
├── y_train_processed.csv
└── y_test_processed.csv
```

Run all notebook cells sequentially from top to bottom.

The modelling process follows:

```text
Load preprocessed data
        ↓
Check target variable
        ↓
Convert target to binary
        ↓
Define Random Forest
        ↓
Train model
        ↓
Generate predictions
        ↓
Calculate evaluation metrics
        ↓
Generate confusion matrix
        ↓
Calculate feature importance
        ↓
Save results
```

---

## 14. Reproducibility

The Random Forest uses:

```python
random_state=42
```

to support reproducibility.

The model also uses the same training and testing observations created earlier in the project so that its results can be compared with Model 1 using the same test dataset.

---

## 15. Relationship to the Project

The Random Forest represents Model 2 of the project:

```text
Bank Marketing Dataset
        ↓
Feature Engineering
        ↓
Preprocessing
        ↓
        ├── Model 1: Logistic Regression
        │
        └── Model 2: Random Forest
                     ↓
              Model Evaluation
                     ↓
              Model Comparison
```

The Random Forest results can therefore be compared with the Logistic Regression results using the same evaluation measures.

---

## 16. Folder Structure

```text
Model2/
│
├── README.md
├── model2_random_forest.ipynb
├── model2_results.csv
└── random_forest_feature_importance.csv
```

The notebook contains the Random Forest training and evaluation process, while the CSV files contain the resulting performance metrics and feature importance values.