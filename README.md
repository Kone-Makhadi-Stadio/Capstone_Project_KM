# Capstone_Project_STADIOEquities

STADIOEquities (Retail Investing & Fintech)

**Motivation for Study**

The rise of digital investment platforms has made investing more accessible, allowing individuals to open accounts and access markets online. STADIOEquities serves this landscape in South Africa, boasting around 2.3 million registered accounts with a median client age of 31, reflecting a significant young investor demographic. However, many of these accounts are not funded or actively used, limiting the platform's economic value.

STADIOEquities faces a challenge with the gap between account registration and activation. Out of 2.3 million registered accounts, only 760,000 are funded and active, with 41% of accounts never making a deposit. The conversion rate from sign-up to first deposit has dropped from 64% to 59%, and the proportion of dormant accounts within 6 months has increased from 22% to 31%. This trend highlights that simply acquiring new customers is not enough for sustained value, as many do not engage meaningfully with the platform.

Financially, STADIOEquities incurs a cost of about R180 per account only upon activation. Registered but unfunded accounts represent an opportunity cost, impacting the return on marketing efforts. The challenge also affects growth and product teams, as onboarding communications are delivered on a fixed schedule rather than tailored to an individual client's activation probability.

STADIOEquities collects extensive customer journey data, including app and web behavior, onboarding activity, and demographics. This historical data offers an opportunity to identify patterns linked to successful account activation and to spot customers at risk of not progressing from registration to funding.

A data-driven approach can help STADIOEquities shift from a one-size-fits-all onboarding process to more targeted interventions. Predictive analytics can reveal characteristics and behaviors associated with account activation, assisting marketing and product teams in prioritising resources to improve the conversion of registered customers into funded investors.

Investigating account activation is crucial for STADIOEquities' current position and 2030 strategy, which aims to activate existing accounts and enable timely interventions for customers likely to activate or stall. A study on activation factors could provide valuable insights to support this strategic objective.

**Problem Statement**

STADIOEquities has a large customer acquisition base with approximately 2.3 million registered accounts. However, a significant number of these customers do not transition from registration to becoming funded and active investors. Currently, 41% of registered accounts have never made a deposit, and the conversion rate from sign-up to first deposit has dropped from 64% to 59%. The company employs fixed onboarding communications and does not effectively identify which newly registered customers are likely to activate their accounts and which may stall.

It remains unclear whether factors such as customer demographic characteristics, onboarding behavior, app and web activity, account information, and marketing engagement can effectively distinguish between customers who are likely to activate their accounts and those who are not. STADIOEquities has access to several years of historical data covering these areas, presenting an opportunity to address this knowledge gap.

| RAAIDD Category | Description | Project-Specific Log Entry |
| :--- | :--- | :--- |
| **Risks** | Unexpected possibilities that could comprise successful completion of the project. | 1. Severe class imbalance between active and dormant/never-funded accounts could bias the machine learning model toward the majority class.<br>2. Inconsistent timestamps and unmerged identities across separate app and web session tracking systems may distort feature engineering.<br>3. High false-positive rates in dormancy prediction could result in unnecessary or intrusive marketing interventions sent to truly active clients.<br>4. Unreliable or unlabelled historical target categories in legacy datasets could degrade the predictive validity of the supervised classifier. |
| **Actions** | Tasks to be done throughout the project’s lifecycle. | 1. Perform comprehensive exploratory data analysis (EDA) to map feature distributions across app clickstreams, KYC steps, and funding logs.<br>2. Apply data resampling techniques (such as SMOTE) and appropriate evaluation metrics (precision, recall, F1-score) to handle class imbalance.<br>3. Implement rigorous cross-validation and hyperparameter tuning configurations to optimize model generalizability.<br>4. Structure the repository directory cleanly to maintain seamless separation between experimental code, helper utilities, and model artefacts. |
| **Assumptions** | Conditions that you assume to be true, but currently unproven. | 1. Historical digital behavior and KYC onboarding patterns over the past several years remain stable and predictive of future user engagement.<br>2. Account funding status and transaction logs accurately reflect true client financial activity without systemic recording errors.<br>3. Marketing channels and campaign attribution data are consistently captured across all acquisition funnels.<br>4. Standard Python data science libraries (scikit-learn, pandas, NumPy) will provide sufficient computational capability for training the baseline classifiers. |
| **Issues** | Problems that transpire throughout the problem’s lifecycle. | Fragmented data silos between app clickstreams, compliance monitoring, and billing systems create initial data merging friction that requires careful pipeline cleaning. |
| **Decisions** | Choices that you (and stakeholders) make throughout the project. | Selected a supervised classification framework (specifically comparing Decision Trees and Random Forests against Logistic Regression) to effectively capture non-linear drop-offs during KYC onboarding and user retention phases. |
| **Dependencies** | Relationships between actions that indicate the chronology of completion. | 1. Exploratory data analysis and data cleaning must be fully completed before algorithm selection and model training can begin.<br>2. Feature engineering scripts and dataset preparation pipelines must be locked down before saving finalized model artefacts to the `models/` directory.<br>3. Final model evaluation results and confusion matrices must be generated prior to compiling the technical report and executive presentation.<br>4. The GitHub repository structure and base README documentation must be fully operational and shared with the lecturer to ensure formal assessment compliance. |

## SS2

# Capstone Project - Machine Learning for Customer Outcome Prediction

## Project Overview

This repository contains the implementation and evaluation of a machine learning solution developed as part of the STADIO Capstone Project.

The project investigates the use of machine learning to predict customer outcomes using the publicly available **UCI Bank Marketing dataset** as an analogous dataset for developing and evaluating the proposed methodology.

The public dataset contains information relating to direct marketing campaigns conducted by a Portuguese banking institution. The classification target indicates whether a customer subscribed to a term deposit.

The public dataset is used to develop and evaluate the machine learning methodology. The intended client application requires the approach to be adapted and retrained using the requested client data and the client-specific target outcome.

---

## Project Objectives

The main objectives of the project are to:

- prepare and preprocess a public dataset suitable for machine learning;
- engineer additional features that may improve predictive performance;
- develop two classification models;
- evaluate the models using appropriate classification metrics;
- statistically compare the performance of the models;
- identify an appropriate model for further development;
- recommend improvements to the selected model; and
- explain how the modelling approach can be adapted to the requested client data.

Two classification algorithms were evaluated:

1. **Logistic Regression**
2. **Random Forest Classifier**

---

# Repository Structure

```text
Capstone_Project_KM/
│
├── README.md
│
├── Data/
│   └── bank-full.csv
│
├── FeatureEngineering/
│   ├── FeatureEngineering.MD
│   ├── feature_engineering.ipynb
│   └── requirements.txt
│
├── Preprocessing/
│   ├── README.md
│   ├── Preprocessing.MD
│   ├── preprocessing.ipynb
│   ├── requirements.txt
│   ├── X_train_engineered.csv
│   ├── X_test_engineered.csv
│   ├── y_train.csv
│   ├── y_test.csv
│   ├── X_train_processed.csv
│   ├── X_test_processed.csv
│   ├── y_train_processed.csv
│   └── y_test_processed.csv
│
├── Model1/
│   ├── README.md
│   ├── Model1.MD
│   ├── Model1Performance.MD
│   ├── model1_logistic_regression.ipynb
│   ├── model1_results.csv
│   ├── model1_predictions.csv
│   └── requirements.txt
│
├── Model2/
│   ├── README.md
│   ├── Model2.MD
│   ├── Model2Performance.MD
│   ├── model2_random_forest.ipynb
│   ├── model2_results.csv
│   ├── model2_predictions.csv
│   ├── random_forest_feature_importance.csv
│   └── requirements.txt
│
├── ModelComparison/
│   ├── Comparison.MD
│   ├── model_comparison.ipynb
│   ├── model_comparison_results.csv
│   ├── mcnemar_test_results.csv
│   └── requirements.txt
│
└── PartD/
    ├── PartD Client Recommendations.pdf
    └── requirements.txt

---

# Part A - Research and Dataset

The project uses the **UCI Bank Marketing dataset** developed from direct marketing campaigns conducted by a Portuguese banking institution.

The dataset contains **45,211 observations** and includes demographic, financial and marketing campaign variables.

The target variable is:

`y`

where:

- `yes` indicates that the customer subscribed to a term deposit; and
- `no` indicates that the customer did not subscribe.

The dataset is used as a public experimental dataset for developing and evaluating the machine learning methodology.

Relevant literature informing the project includes research by Moro, Cortez and Rita (2014) and Hou et al. (2022), which demonstrates the application of data-driven and machine learning techniques to bank marketing and deposit-subscription prediction.

---

# Part B - Model Development

Part B covers feature engineering, preprocessing and the development of the two machine learning models.

## Feature Engineering

The feature engineering process creates additional variables from the original dataset to provide potentially useful representations of customer and campaign information.

Engineered features include:

- age group;
- positive balance indicator;
- balance-to-age ratio;
- previous contact indicator;
- previous positive campaign outcome; and
- contact intensity.

Detailed documentation:

[View Feature Engineering Documentation](FeatureEngineering.MD)

Notebook:

`FeatureEngineering/feature_engineering.ipynb`

---

## Data Preprocessing

The preprocessing pipeline prepares the engineered data for machine learning.

The process includes:

- separation of numerical and categorical variables;
- missing-value handling;
- numerical feature scaling;
- one-hot encoding of categorical variables;
- fitting preprocessing transformations using training data only; and
- transformation of the training and test datasets.

Detailed documentation:

[View Preprocessing Documentation](Preprocessing.MD)

Notebook:

`Preprocessing/preprocessing.ipynb`

---

## Model 1 - Logistic Regression

The first model is a **Logistic Regression classifier**.

The model uses class weighting to account for the imbalance between subscribers and non-subscribers.

Detailed documentation:

[View Model 1 Documentation](Model1.MD)

Notebook:

`Model1/model1_logistic_regression.ipynb`

---

## Model 2 - Random Forest

The second model is a **Random Forest Classifier**.

Random Forest provides a nonlinear tree-based modelling approach and allows the relative importance of the input features to be examined.

Detailed documentation:

[View Model 2 Documentation](Model2.MD)

Notebook:

`Model2/model2_random_forest.ipynb`

---

# Part C - Model Performance

Both models were evaluated on the same held-out test dataset.

The following evaluation metrics were used:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix

Because the target variable is imbalanced, model performance was evaluated using multiple measures rather than accuracy alone.

## Model 1 Performance

The Logistic Regression model produced the following results:

| Metric | Result |
|---|---:|
| Accuracy | 84.58% |
| Precision | 41.81% |
| Recall | 81.10% |
| F1-score | 55.18% |
| ROC-AUC | 90.97% |

Detailed results:

[View Logistic Regression Performance](Model1Performance.MD)

---

## Model 2 Performance

The Random Forest model produced the following results:

| Metric | Result |
|---|---:|
| Accuracy | 89.66% |
| Precision | 55.23% |
| Recall | 61.34% |
| F1-score | 58.13% |
| ROC-AUC | 92.66% |

Detailed results:

[View Random Forest Performance](Model2Performance.MD)

---

# Model Comparison

The two models demonstrated different classification characteristics.

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Accuracy | 84.58% | 89.66% |
| Precision | 41.81% | 55.23% |
| Recall | 81.10% | 61.34% |
| F1-score | 55.18% | 58.13% |
| ROC-AUC | 90.97% | 92.66% |

Random Forest achieved higher accuracy, precision, F1-score and ROC-AUC.

Logistic Regression achieved higher recall, indicating that it identified a larger proportion of the actual positive cases.

A **McNemar test** was also used to statistically compare the paired classification outcomes of the models.

The test produced:

- McNemar test statistic: **217.3720**
- p-value: **approximately 3.39 × 10^-49**
- significance level: **0.05**

The result indicates a statistically significant difference between the classification performance of the two models on the test observations.

Detailed comparison:

[View Model Comparison](Comparison.MD)

Comparison notebook:

`ModelComparison/model_comparison.ipynb`

---

# Part D - Client Recommendations

Based on the experimental results, **Random Forest was selected as the primary model for further development** because it achieved higher accuracy, precision, F1-score and ROC-AUC on the public dataset.

Logistic Regression remains an important benchmark because it achieved substantially higher recall.

The recommendation therefore considers both predictive performance and the operational consequences of false-positive and false-negative predictions.

The Part D report also discusses:

- improvements to the selected model;
- hyperparameter and classification-threshold tuning;
- the effect of the `duration` variable;
- adaptation of the modelling pipeline to the requested client data;
- retraining and validation using the client-specific target outcome; and
- alignment between the experimental results and the literature reviewed in Part A.

Client recommendation report:

[View Part D Client Recommendations Report](PartD/PartD_Client_Recommendations_Report.pdf)

---

# Important Modelling Consideration

The `duration` variable was identified as the most influential feature in the fitted Random Forest model.

This variable represents the duration of the marketing contact.

If the intended model is required to generate predictions **before customer contact takes place**, this information would not yet be available at prediction time.

A future experiment should therefore remove `duration` and repeat model training and evaluation to establish the performance of a strictly pre-contact prediction model.

The current results should consequently be interpreted as experimental performance using the present feature set.

---

# Running the Project

## 1. Clone the Repository

Clone or download the repository and navigate to the project directory.

## 2. Install Dependencies

Install the required Python packages using:

```bash
pip install -r requirements.txt
```

The project requires packages including:

- pandas
- NumPy
- scikit-learn
- Matplotlib
- Jupyter
- statsmodels

## 3. Run the Notebooks

The notebooks should be executed in the following order:

```text
1. FeatureEngineering/feature_engineering.ipynb
                    ↓
2. Preprocessing/preprocessing.ipynb
                    ↓
3. Model1/model1_logistic_regression.ipynb
                    ↓
4. Model2/model2_random_forest.ipynb
                    ↓
5. ModelComparison/model_comparison.ipynb
```

This order ensures that each stage produces the files required by the next stage.

---

# Reproducibility

A fixed `random_state=42` is used during model development where applicable to improve reproducibility.

The dataset is split into training and testing subsets using stratification to preserve the distribution of the target variable.

Preprocessing transformations are fitted using the training data and subsequently applied to the test data to reduce the risk of information leakage between the training and evaluation stages.

Dependencies required to reproduce the project are listed in:

`requirements.txt`

---

# Technologies Used

The project was developed using:

- Python
- Jupyter Notebook
- pandas
- NumPy
- scikit-learn
- Matplotlib
- statsmodels
- Git
- GitHub

---

# References

Hou, S., Cai, Z., Wu, J., Du, H. and Xie, P. (2022) 'Applying machine learning to the development of prediction models for bank deposit subscription', *International Journal of Business Analytics*, 9(1), pp. 1-14. doi:10.4018/IJBAN.288514.

Moro, S., Cortez, P. and Rita, P. (2014) 'A data-driven approach to predict the success of bank telemarketing', *Decision Support Systems*, 62, pp. 22-31. doi:10.1016/j.dss.2014.03.001.

Moro, S., Rita, P. and Cortez, P. (2014) *Bank Marketing* [Dataset]. UCI Machine Learning Repository. doi:10.24432/C5K306.

## SS3 Part B: STADIOEquities Account Activation

### Project objective

Apply the Random Forest method selected in SS2 to the supplied
synthetic STADIOEquities data.

The model predicts whether customers who have not activated by
day 3 after registration will activate by day 30.

Activation means a successful first deposit of at least R100 within
30 calendar days of registration:

- **Class 0:** Not activated within 30 days.
- **Class 1:** Activated within 30 days.

### Notebook

[Open SS3_PartB.ipynb](SS3_PartB.ipynb)

The notebook contains five clearly labelled assessment components:

1. Dataset loading.
2. Dataset preprocessing.
3. Model training.
4. Model validation.
5. Results visualisation.

### Data

The supplied extract contains five CSV files:

| File | Contents |
|---|---|
| source1_registration_kyc_customer.csv | Registration, customer attributes and KYC |
| source2_app_web_behaviour.csv | App and web activity |
| source3_account_funds_activation.csv | Funding and activation outcomes |
| source4_marketing_engagement.csv | Marketing activity |
| source5_data_quality_metadata.csv | Extract and data-quality metadata |

The funding dataset contains 1,893 customers: 1,085 non-activated
customers (57.32%) and 808 activated customers (42.68%).

These are raw dataset counts. The modelling cohort is smaller after
quality checks and exclusion of customers already activated by day 3.

### Requirements

Python 3.11 or later is recommended.

Install the required packages using:

```bash
pip install "pandas>=2.0" numpy matplotlib "scikit-learn>=1.2" notebook
```

### How to run

1. Download or clone this repository.
2. Obtain and extract the supplied STADIOEquities CSV files.
3. Open `SS3_PartB.ipynb` in Jupyter Notebook.
4. In the folder-path cell, update `data_folder` to the folder
   containing all five CSV files.
5. Run the notebook cells from top to bottom.
6. Save the notebook with its outputs.

### Preprocessing

Exact duplicates are removed, text categories are standardised and
dates are parsed. Records with insufficient registration timestamps,
incomplete follow-up or conflicting target information are excluded.

Behavioural events and marketing messages are aggregated within the
first three days after registration.

Funding outcomes, balances and other information unavailable at the
prediction time are excluded from model inputs.

Missing numeric values are imputed using training-data medians.
Categorical variables are imputed and one-hot encoded within the
modelling pipeline.

Customers are split chronologically into training, validation and test
subsets. Outcome-overlap embargoes ensure earlier customers' outcomes
are available before predictions begin in the next subset.

### Model training

The model is a Random Forest with 300 trees and balanced class weights.

Eight combinations of maximum tree depth, minimum leaf size and
maximum features are compared using validation macro F1.

The classification threshold is selected using validation data.
The selected configuration is then fitted on training plus validation
data before final test evaluation.

The test set is not used for model or threshold selection.

### Evaluation

The notebook reports:

- Accuracy and balanced accuracy.
- Macro and weighted F1.
- Class-specific precision, recall and F1.
- ROC-AUC and activation average precision.
- Brier score.
- A conditional bootstrap interval for test macro F1.

Performance is compared with majority-class and constant-probability
baselines.

### Visualisations and saved outputs

Running the notebook creates a `results/` folder containing:

- Dataset inventory and input file hashes.
- Quality checks and cohort counts.
- Training, validation and test subset summaries.
- Hyperparameter and threshold comparisons.
- Selected model settings and evaluation metrics.
- Training and validation performance plots.
- Test confusion matrix.
- ROC and precision-recall curves.
- Calibration and class-specific performance plots.
- Class proportions and feature importance.

### Limitations

The supplied data are synthetic, so performance does not establish
effectiveness on live client data.

Results apply to customers who have not activated by day 3.
This notebook does not model six-month dormancy.

Feature importance describes model behaviour rather than causal
relationships. A separate intervention study is needed to determine
whether targeted follow-up improves activation.

### Commit history

Part B requires at least five meaningful commits, covering dataset
loading, preprocessing, training, validation and visualisation.