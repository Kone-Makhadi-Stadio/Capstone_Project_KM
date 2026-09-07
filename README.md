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
| --- | --- | --- |
| **Risks** | Unexpected possibilities that could comprise successful completion of the project.

 | 1. Severe class imbalance between active and dormant/never-funded accounts could bias the machine learning model toward the majority class.

<br>

<br>2. Inconsistent timestamps and unmerged identities across separate app and web session tracking systems may distort feature engineering.

<br>

<br>3. High false-positive rates in dormancy prediction could result in unnecessary or intrusive marketing interventions sent to truly active clients.

<br>

<br>4. Unreliable or unlabelled historical target categories in legacy datasets could degrade the predictive validity of the supervised classifier.

 |
| **Actions** | Tasks to be done throughout the project’s lifecycle.

 | 1. Perform comprehensive exploratory data analysis (EDA) to map feature distributions across app clickstreams, KYC steps, and funding logs.

<br>

<br>2. Apply data resampling techniques (such as SMOTE) and appropriate evaluation metrics (precision, recall, F1-score) to handle class imbalance.

<br>

<br>3. Implement rigorous cross-validation and hyperparameter tuning configurations to optimize model generalizability.

<br>

<br>4. Structure the repository directory cleanly to maintain seamless separation between experimental code, helper utilities, and model artefacts.

 |
| **Assumptions** | Conditions that you assume to be true, but currently unproven.

 | 1. Historical digital behavior and KYC onboarding patterns over the past several years remain stable and predictive of future user engagement.

<br>

<br>2. Account funding status and transaction logs accurately reflect true client financial activity without systemic recording errors.

<br>

<br>3. Marketing channels and campaign attribution data are consistently captured across all acquisition funnels.

<br>

<br>4. Standard Python data science libraries (scikit-learn, pandas, NumPy) will provide sufficient computational capability for training the baseline classifiers.

 |
| **Issues** | Problems that transpire throughout the problem’s lifecycle.

 | Fragmented data silos between app clickstreams, compliance monitoring, and billing systems create initial data merging friction that requires careful pipeline cleaning.

 |
| **Decisions** | Choices that you (and stakeholders) make throughout the project.

 | Selected a supervised classification framework (specifically comparing Decision Trees and Random Forests against Logistic Regression) to effectively capture non-linear drop-offs during KYC onboarding and user retention phases.

 |
| **Dependencies** | Relationships between actions that indicate the chronology of completion.

 | 1. Exploratory data analysis and data cleaning must be fully completed before algorithm selection and model training can begin.

<br>

<br>2. Feature engineering scripts and dataset preparation pipelines must be locked down before saving finalized model artefacts to the `models/` directory.

<br>

<br>3. Final model evaluation results and confusion matrices must be generated prior to compiling the technical report and executive presentation.

<br>

<br>4. The GitHub repository structure and base README documentation must be fully operational and shared with the lecturer to ensure formal assessment compliance.

 |