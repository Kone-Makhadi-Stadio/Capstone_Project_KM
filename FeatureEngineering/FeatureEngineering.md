# Feature Engineering

## 1. Overview

This folder contains the feature engineering component of the  Bank Marketing prediction project in SS2

The purpose of the feature engineering process is to create additional variables from the original dataset that may provide useful information for predicting whether a customer subscribes to a term deposit

The feature engineering process was performed after separating the target variable and splitting the dataset into training datasets and testing datasets.

The training and testing datasets were engineered separately to make sure that the test dataset remains independent of the training process

---

## 2. Dataset

The feature engineering notebook uses the UCI Bank Marketing dataset:

**Dataset:** Bank Marketing (`bank-full.csv`)

The dataset contains information about customers and their interactions with a bank marketing campaign.

The target variable is:

* `y` – whether the customer subscribed to a term deposit (`yes` or `no`)

The original dataset contains 45,211 observations and 17 columns, consisting of 16 predictor variables and one target variable.

---

## 3. Feature Engineering Notebook

The feature engineering is performed using:

`feature_engineering.ipynb`

The notebook performs the following steps:

1. Imports the required Python libraries.
2. Loads the `bank-full.csv` dataset.
3. Separates the predictor variables from the target variable.
4. Splits the dataset into training and testing sets.
5. Applies feature engineering separately to the training and testing datasets.
6. Examines the newly created features.
7. Checks for missing values created during feature engineering.
8. Saves the engineered datasets for use by the preprocessing stage.

---

## 4. Train/Test Split

The dataset is divided into:

* 80% training data
* 20% testing data

A `random_state` of 42 is used to ensure that the split can be reproduced.

Stratified sampling is used based on the target variable `y` so that the proportion of customers who subscribed and did not subscribe remains similar between the training and testing datasets.

The test dataset is kept separate from the feature engineering process and is not combined with the training dataset.

---

## 5. Engineered Features

Six additional features are created
### 5.1 Age Group

The original `age` variable is converted into age categories:

* 18–25
* 26–35
* 36–45
* 46–55
* 56–65
* 66+

This provides an alternative representation of customer age that can be used to identify patterns between different age groups.

### 5.2 Has Balance

The `balance` variable is used to create a binary feature called `has_balance`

The feature is defined as:

* `1` – customer has a positive account balance
* `0` – customer does not have a positive account balance

### 5.3 Balance-to-Age Ratio

A ratio between account balance and customer age is created:

`balance_to_age = balance / (age + 1)`

The addition of 1 prevents division by zero.

This feature provides a relative measure of account balance in relation to customer age
### 5.4 Has Previous Contact

The `pdays` variable is used to determine whether a customer had previously been contacted during a campaign.

The original dataset uses `-1` to indicate that the customer was not previously contacted.

The engineered feature is:

* `1` – customer was previously contacted
* `0` – customer was not previously contacted

### 5.5 Previous Positive Outcome

The `poutcome` variable is used to identify whether a previous marketing campaign resulted in a successful outcome.

The feature is defined as:

* `1` – previous outcome was `success`
* `0` – previous outcome was not `success`

### 5.6 Contact Intensity

The `campaign` variable represents the number of contacts performed during the current campaign.

This is grouped into three categories:

* `Low` – 1 contact
* `Medium` – 2–3 contacts
* `High` – more than 3 contacts

This provides a categorical representation of the intensity of contact during the current campaign.

---

## 6. Preprocessing Separation

Categorical encoding and numerical scaling are not performed in this notebook.

These processes are handled separately in the preprocessing stage.

This separation allows the feature engineering stage to focus on creating meaningful variables while the preprocessing stage prepares those variables for use by the machine learning models

---

## 7. Output Files

After the notebook has been executed the following files were produced:

* `X_train_engineered.csv`
* `X_test_engineered.csv`
* `y_train.csv`
* `y_test.csv`

These files are used as inputs for the preprocessing stage.

---

## 8. How to Run

### Requirements

The following Python packages are required:

* pandas
* numpy
* scikit-learn

### Running the notebook

1. Open `feature_engineering.ipynb` in Jupyter Notebook or JupyterLab.
2. Ensure that `bank-full.csv` is located in the `Preprocessing` folder.
3. Run the notebook cells from top to bottom.
4. Check the dataset dimensions and engineered features.
5. Confirm that the output CSV files have been created in the `Preprocessing` folder.

The engineered datasets can then be used in the preprocessing notebook.

---

## 9. Repository Location

The feature engineering notebook is located at:

`FeatureEngineering/feature_engineering.ipynb`

The resulting engineered datasets are stored in:

`Preprocessing/`
