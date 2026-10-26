# STADIOEquities — Account Activation: Data Extract

Five source extracts plus a full data dictionary (`DATA_DICTIONARY.md`), covering registrations from September 2024 to August 2026. Extraction date **2026-09-14 09:44:03**. All datetimes are `YYYY-MM-dd HH:mm:ss` in SAST (UTC+02:00). Join sources 1-4 on `customer_id`.

## Files

### `source1_registration_kyc_customer.csv`
Registration, KYC progress and stated customer profile.  
Rows: 1,898

| Column | Description |
|---|---|
| `customer_id` | String |
| `registration_date` | Datetime |
| `registration_channel` | Categorical |
| `acquisition_channel` | Categorical |
| `kyc_start_date` | Datetime |
| `kyc_completion_date` | Datetime |
| `kyc_status` | Categorical |
| `kyc_steps_completed` | Integer |
| `onboarding_abandonment_step` | Categorical |
| `age` | Integer |
| `region` | Categorical |
| `investment_goal` | Categorical |
| `risk_appetite` | Categorical |

### `source2_app_web_behaviour.csv`
Event-level app and web behaviour with session context.  
Rows: 18,322

| Column | Description |
|---|---|
| `session_id` | String |
| `customer_id` | String |
| `session_start` | Datetime |
| `session_duration` | Numeric |
| `platform` | Categorical |
| `screen_viewed` | Categorical |
| `screen_views` | Integer |
| `feature_used` | Categorical |
| `onboarding_step` | Categorical |
| `abandonment_flag` | Boolean |
| `event_timestamp` | Datetime |

### `source3_account_funds_activation.csv`
Funding position and the activation target.  
Rows: 1,893

| Column | Description |
|---|---|
| `customer_id` | String |
| `first_deposit_date` | Datetime |
| `first_deposit_amount` | Numeric |
| `deposit_count` | Integer |
| `total_deposited` | Numeric |
| `withdrawal_count` | Integer |
| `account_balance` | Numeric |
| `balance_as_at` | Datetime |
| `activation_flag` | Boolean |
| `activation_date` | Datetime |
| `days_to_first_deposit` | Integer |

### `source4_marketing_engagement.csv`
Campaign and nudge sends with engagement outcomes.  
Rows: 8,332

| Column | Description |
|---|---|
| `customer_id` | String |
| `campaign_id` | String |
| `campaign_channel` | Categorical |
| `campaign_date` | Datetime |
| `message_type` | Categorical |
| `message_sent` | Boolean |
| `message_opened` | Boolean |
| `link_clicked` | Boolean |
| `nudge_response` | Boolean |
| `acquisition_cost` | Numeric |

### `source5_data_quality_metadata.csv`
Record provenance, status and missingness metadata.  
Rows: 11,475

| Column | Description |
|---|---|
| `record_timestamp` | Datetime |
| `source_system` | Categorical |
| `record_status` | Categorical |
| `missingness_reason` | Categorical |
| `data_extraction_date` | Datetime |

## Data quality notes

This is an extract from live operational systems and has **not** been cleaned. Expect:

- Missing values in optional / conditionally-populated fields
- Inconsistent casing and stray whitespace in some free-text and categorical fields
- A small number of duplicate records
- Occasional out-of-range or implausible values from data-capture errors
- Some date fields captured in inconsistent formats

**Target:** `activation_flag` in `source3_account_funds_activation.csv`. The agreed definition — first successful deposit of R100 or more within 30 calendar days of registration — is set out in `DATA_DICTIONARY.md` along with all controlled values, units and business rules.

**Leakage warning:** `first_deposit_date`, `first_deposit_amount`, `activation_date`, `days_to_first_deposit`, `deposit_count`, `total_deposited`, `withdrawal_count` and `account_balance` in source 3 are all post-outcome. Sources 1, 2 and 4 are the intended predictors.

**Read `DATA_DICTIONARY.md` before modelling** — it documents the deliberate difference between *not applicable* and *not captured* in the missingness handling, which matters for the SMS engagement fields in source 4.

_Synthetic data supplied for the CAP182 capstone project. Not real client data._