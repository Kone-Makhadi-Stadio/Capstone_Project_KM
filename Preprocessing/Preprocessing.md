# Preprocessing

## Overview


The purpose of preprocessing is to transform the feature-engineered Bank Marketing dataset into a format suitable for machine learning models.

The preprocessing is performed after the train/test split and feature engineering stages. The training data is used to fit the preprocessing transformations, and the same transformations are then applied to the test data

This approach helps prevent information from the test dataset influencing the training process

---

## Input Data

The preprocessing notebook uses the feature-engineered datasets produced by the Feature Engineering stage:

* `X_train_engineered.csv`
* `X_test_engineered.csv`
* `y_train.csv`
* `y_test.csv`

The original dataset used for the project is:

* `bank-full.csv`

The dataset is the Bank Marketing dataset obtained from the UCI Machine Learning Repository.

---

## Notebook

The preprocessing implementation is contained in:

```text
preprocessing.ipynb
```

The notebook performs the following preprocessing steps:

1. Load the feature-engineered training and testing datasets.
2. Identify numerical and categorical variables.
3. Check for missing values.
4. Impute missing numerical values using the median.
5. Impute missing categorical values using the most frequent category.
6. Apply one-hot encoding to categorical variables.
7. Standardise numerical variables.
8. Fit preprocessing transformations using the training data only.
9. Apply the fitted transformations to the testing data.
10. Save the processed datasets for modelling.

---

## Preprocessing Techniques

### 1. Missing Value Handling

Missing numerical values are handled using median imputation.

```python
SimpleImputer(strategy="median")
```

The median is used because it is less affected by extreme values than the mean.

Categorical missing values are handled using the most frequent category:

```python
SimpleImputer(strategy="most_frequent")
```

---

### 2. One-Hot Encoding

Categorical variables cannot be directly used by the machine learning models in their original text format.

One-hot encoding converts categorical variables into numerical indicator columns.

For example:

```text
job = management
```

may be represented through encoded columns such as:

```text
job_management = 1
job_services = 0
job_technician = 0
```

The preprocessing pipeline uses:

```python
OneHotEncoder(
    handle_unknown="ignore",
    sparse_output=False
)
```

`handle_unknown="ignore"` ensures that an unseen category in the test dataset does not cause an error.

---

### 3. Numerical Standardisation

Numerical variables are standardised using:

```python
StandardScaler()
```

Standardisation transforms numerical variables so that they are placed on a comparable scale.

This is particularly relevant for the Logistic Regression model because variables such as `balance`, `duration`, `campaign`, and `pdays` can have substantially different numerical ranges.

---

## Training and Testing Separation

The preprocessing transformations are fitted only using the training dataset.

```python
X_train_processed = preprocessor.fit_transform(X_train)
```

The already-fitted transformations are then applied to the test dataset:

```python
X_test_processed = preprocessor.transform(X_test)
```

The test dataset is therefore not used to calculate preprocessing parameters.

This maintains the separation between training and testing data and provides a more reliable evaluation of model performance.

---

## Preprocessing Pipeline

The preprocessing pipeline follows this structure:

```text
Feature-engineered data
          |
          v
    Identify columns
          |
     +----+----+
     |         |
     v         v
Numerical   Categorical
     |         |
     v         v
Median      Most-frequent
Imputation  Imputation
     |         |
     v         v
Standard    One-Hot
Scaling     Encoding
     |         |
     +----+----+
          |
          v
   Model-ready data
```

---

## Output Files

After running the notebook, the following processed datasets are generated:

```text
X_train_processed.csv
X_test_processed.csv
y_train_processed.csv
y_test_processed.csv
```

These datasets are used as inputs for the modelling stages.

---

## Relationship to the Models

The processed datasets will be used for the two machine learning models selected for the project:

### Model 1 — Logistic Regression

Logistic Regression is used as an interpretable classification model for predicting whether a customer will subscribe to the target product

Standardisation is particularly important for this model because it is sensitive to differences in numerical feature scales

### Model 2 — Random Forest

Random Forest is used as an ensemble classification model capable of modelling nonlinear relationships and interactions between variables

Random Forest does not require numerical standardisation in the same way as Logistic Regression. However, the preprocessing workflow maintains a consistent representation of the dataset for the modelling stage

---

## Reproducibility

The preprocessing process uses a consistent pipeline and fixed training/testing datasets.

The train/test split was performed using:

```python
random_state=42
```

and stratification was used to maintain the distribution of the target classes.

The preprocessing transformations are fitted on the training data and subsequently applied to the test data.

---

## How to Run

1. Open `preprocessing.ipynb`
2. Ensure the following files are available in the `Preprocessing` folder:

```text
X_train_engineered.csv
X_test_engineered.csv
y_train.csv
y_test.csv
```

3. Run the notebook cells from top to bottom
4. Confirm that the processed datasets are generated successfully
5. Use the processed datasets in the modelling notebooks

---

## Project Structure

```text
Capstone_Project_KM/
│
├── Preprocessing/
│   ├── README.md
│   ├── preprocessing.ipynb
│   ├── bank-full.csv
│   ├── X_train_engineered.csv
│   ├── X_test_engineered.csv
│   ├── y_train.csv
│   ├── y_test.csv
│   ├── X_train_processed.csv
│   ├── X_test_processed.csv
│   ├── y_train_processed.csv
│   └── y_test_processed.csv
│
├── FeatureEngineering/
│   ├── README.md
│   └── feature_engineering.ipynb
│
├── Model1/
│   ├── README.md
│   └── model1_logistic_regression.ipynb
│
└── Model2/
    ├── README.md
    └── model2_random_forest.ipynb
```

---

## Summary

The preprocessing stage converts the feature-engineered dataset into model-ready numerical data.

The main techniques used are:

* Median imputation for numerical variables
* Most-frequent imputation for categorical variables
* One-hot encoding for categorical variables
* Standardisation of numerical variables
* Training-only fitting of preprocessing transformations
* Consistent transformation of the test dataset

The resulting datasets provide the inputs required for the Logistic Regression and Random Forest modelling stages.
