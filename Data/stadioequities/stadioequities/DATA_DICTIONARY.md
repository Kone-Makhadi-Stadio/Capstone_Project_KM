# Data dictionary — STADIOEquities activation extract

**Extraction date:** 2026-09-14 09:44:03 (SAST, UTC+02:00)
**Observation period:** 2024-09-01 to 2026-08-14 (registrations)
**Join key:** `customer_id`, present in sources 1-4.

## Agreed business rules

- **Activation definition.** A customer is activated when they make their **first successful
  deposit of R100 or more within 30 calendar days of registration**. `activation_flag` is True
  on that definition only; `activation_date` is the timestamp the criterion was first met and is
  therefore identical to `first_deposit_date` for activated customers.
- **Activation window:** 30 calendar days from `registration_date`. Every customer in this extract
  registered on or before 2026-08-14, so the window is fully elapsed for all of them.
- **Total KYC steps:** 6. `kyc_steps_completed` ranges 0-6.
  Order: Personal details, Contact verification, Proof of identity, Proof of address,
  Bank account linking, Risk profile questionnaire.
- **Acquisition cost allocation:** total channel spend for the calendar month divided by
  registrations attributed to that channel in the same month (last non-direct click attribution).
  It is a channel-month average, not a true per-customer cost.

## Units

| Field | Unit |
|---|---|
| `session_duration` | minutes, decimal |
| `first_deposit_amount`, `total_deposited`, `account_balance`, `acquisition_cost` | ZAR |
| `days_to_first_deposit` | calendar days |
| all datetimes | `YYYY-MM-dd HH:mm:ss`, SAST (UTC+02:00) |

## Controlled values

| Field | Valid values |
|---|---|
| `registration_channel` | Mobile app, Web, Tablet app |
| `acquisition_channel` | Paid social, Organic search, Referral, Direct, Email, Influencer, Display, Radio |
| `kyc_status` | Not started, In progress, Completed, Failed, Rejected |
| `onboarding_abandonment_step` | the six KYC steps above; blank where onboarding completed |
| `region` | the nine South African provinces |
| `investment_goal` | Long-term growth, Retirement, Short-term gains, Savings, Education fund, Income generation |
| `risk_appetite` | Conservative, Moderate, Aggressive |
| `platform` | iOS, Android, Web - Desktop, Web - Mobile, Tablet |
| `campaign_channel` | Email, Push notification, SMS, In-app message, WhatsApp |
| `record_status` | Active, Corrected, Deleted, Superseded |

## Known limitations

- `message_opened`, `link_clicked` and `nudge_response` are **blank rather than False** for SMS,
  where open tracking does not exist. This is genuine unavailability, not a failed send — see
  `missingness_reason` in source 5.
- `feature_used` is blank on ~16% of behavioural events; the field was only added to the mobile
  SDK partway through the period.
- `account_balance` is a point-in-time value **as at the extraction date**, not as at the event
  date. `balance_as_at` has been added to make that explicit.
- Source 5 is record-level metadata and does **not** carry `customer_id`; it describes the volume
  and provenance of records loaded per source system, and cannot be joined row-to-row.
- The request listed "First deposit date" twice; the second entry, with a numeric example, has
  been supplied as `first_deposit_amount`.
