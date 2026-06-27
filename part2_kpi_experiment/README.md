# Part 2: KPI Framework, Business Experiment Analysis & Decision Recommendation
## Campaign Experiment — Onboarding & Activation

---

## Business Context

A subscription-based digital product company launched a new onboarding and activation campaign to improve user conversion and early engagement. Users were randomly divided into two groups:

- **Control Group:** Existing onboarding experience
- **Treatment Group:** New campaign experience

Leadership must decide whether to roll out the treatment to all users, hold, or restrict launch to selected segments, or  reject campaign.

---

## Business Problem Statement

### 1. What Decision Needs to Be Made

The business must decide whether to **fully launch the new onboarding campaign to all users**, hold the rollout pending further evidence, or selectively deploy the campaign to specific user segments, or reject the campaign. This is a go/no-go product decision with direct revenue and user experience implications.

### 2. Who the Decision Impacts

| Stakeholder | Impact |
|---|---|
| New users | Directly experience the onboarding flow — affects first-week activation and retention |
| Product & Engineering teams | Must build and maintain the new experience at scale |
| Growth & Marketing teams | Rely on conversion metrics to hit acquisition targets |
| Finance / Revenue team | Impacted by changes to paid conversion rate and average revenue per user |
| Customer Support team | Impacted by changes in support ticket volume and refund rates |

### 3. What Metric Should Improve

The **primary success metric** is **Paid Conversion Rate** — the proportion of users who convert from free/trial to a paid subscription within 30 days of signup.

This metric is chosen because:
- It directly measures the campaign's stated objective: improving user conversion
- it directly contributes to subscription growth and customer acquisition efficiency
- It has a clear, binary, attributable outcome per user
- It is the most direct leading indicator of revenue growth for a subscription business

Supporting metrics that should also improve:
- Trial Start Rate
- Onboarding Completion Rate
- Average Revenue Per User (ARPU)
- Engagement Score (early signal of long-term retention)

### 4. What Risks Must Be Monitored

The following **guardrail metrics** must be tracked to ensure the campaign does not cause unintended harm even if conversion improves:

| Guardrail Metric | Risk If Violated |
|---|---|
| Refund Rate | High refunds signal the campaign may attract low-quality or misled conversions |
| Support Ticket Rate | Increased tickets suggest the new onboarding creates confusion or friction |
| Average Days to Convert | If conversions are fast but revenue quality drops, the campaign may be optimizing for quantity over quality |
| Engagement Score | Low engagement among converted users signals poor fit or inflated expectations |
| Segment-Level Conversion | Improvement in one region/device could mask decline in another |

### 5. What Evidence Is Required Before Making a Recommendation

Before recommending a launch decision, the following evidence must be gathered and evaluated:

1. **Statistically significant improvement** in paid conversion rate (p-value < 0.05 using a two-proportion z-test)
2. **No statistically significant degradation** in any guardrail metric for the treatment group
3. **Consistent lift across at least 2 key segments** (e.g., region, device type, plan type) to ensure the effect is not isolated
4. **Adequate sample size** in both groups to ensure statistical power
5. **Revenue quality check** — average revenue per converted user must not decrease significantly in the treatment group
6. **Directional alignment** between conversion rate improvement and engagement score improvement

---

## Dataset Description

| Field | Description |
|---|---|
| `user_id` | Unique user identifier |
| `signup_date` | Date the user signed up (January–May 2025) |
| `experiment_group` | Control or Treatment |
| `region` | Geographic region: North, South, East, West |
| `device_type` | Mobile, Desktop, or Tablet |
| `traffic_source` | Organic, Paid Search, Social, Referral, Email |
| `plan_type` | Free, Basic, or Premium |
| `visited_landing_page` | Binary: 1 if user visited the landing page |
| `started_trial` | Binary: 1 if user started a trial |
| `completed_onboarding` | Binary: 1 if user completed onboarding |
| `converted_to_paid` | Binary: 1 if user converted to a paid plan |
| `revenue_30d` | Revenue generated within 30 days (0 for non-converters) |
| `support_tickets_30d` | Number of support tickets raised in 30 days |
| `refund_requested` | Binary: 1 if user requested a refund |
| `days_to_convert` | Days taken to convert (NaN for non-converters) |
| `engagement_score` | Engagement score on a 0–100 scale |

**Total records:** 1,408 users | **Control:** 693 | **Treatment:** 715

---

## North Star Metric

**Selected North Star Metric:** **Paid Conversion Rate** — the percentage of users who successfully convert from signup or trial users to a paid subscription within 30 days of signup.

### 1. Why this is the main success metric

Paid Conversion Rate is the best North Star metric for this experiment because the campaign's stated goal is to improve user conversion and early activation in a subscription business. The company ultimately creates value when more users become paying subscribers, so this metric directly reflects whether the new onboarding experience produces meaningful business impact.

It is also the clearest experiment outcome because:
- It aligns directly with the decision leadership must make
- It is simple to calculate and compare across Control vs. Treatment
- It is a definitive, binary outcome (each user either converts or does not)
- It ties onboarding quality to revenue generation more directly than early funnel metrics

### 2. Why other metrics are supporting metrics

The following metrics are important, but they are **supporting metrics** rather than the North Star because they describe steps in the funnel or quality signals rather than the final business outcome:

| Supporting Metric | Why It Supports Rather Than Leads |
|---|---|
| Trial Start Rate | Shows initial product interest, but trial starts do not guarantee revenue |
| Onboarding Completion Rate | Indicates whether users successfully progress through activation steps, but completion alone does not create paying customers |
| Landing Page Visit Rate | measures whether users enter the onboarding funnel |
| Average Revenue Per User (ARPU) | Useful for monetization, and is a revenue metric, but it can be skewed by a few users buying high-tier plans. |
| Engagement Score | Early retention/usage signal, but not a direct monetization outcome. While high engagement usually correlates with retention, engagement alone doesn't pay the bills if users remain on a free tier indefinitely |
| Refund Rate | A guardrail metric that reflects conversion quality, not success volume |
| Support Ticket Rate | Operational risk indicator, not a primary growth outcome |

These metrics are valuable because they help explain where improvements or drop-offs occur within the user journey, but none of them directly measure revenue-generating customer conversion.

### 3. How this metric connects to business growth

Paid Conversion Rate connects directly to business growth in four ways:

1. **Revenue growth** — more converted users means more subscription revenue from the same acquisition volume
2. **Acquisition efficiency** — the company gets more value from each acquired user without increasing acquisition spend
3. **Customer Engagement** — increases lifetime customer value, and supports long-term subscription growth
4. **Forecasting quality** — conversion rate is one of the most reliable short-term leading indicators for subscription businesses

In short, improving paid conversion means the company turns a larger share of signups into monetized users, which improves both topline growth and unit economics.

### 4. What could go wrong if optimized blindly

Optimizing Paid Conversion Rate blindly can create business risks. For example: If the company aggressively pushes users toward payment without maintaining a positive customer experience

- Users may convert faster but request more refunds later
- The onboarding flow may become too aggressive, increasing support tickets
- A short-term push to convert users could reduce engagement quality and increase future churn
- Growth in one segment may hide weaker performance in another segment
- Revenue quality may decline if converted users choose lower-value plans or refund quickly
- Dissatisfaction among users who convert but quickly cancel

For this reason, Paid Conversion Rate should remain the primary success metric, while guardrail metrics such as Refund Rate, Support Ticket Rate, Engagement Score, and Days to Convert must also be evaluated before making a final launch recommendation.

---

## KPI Tree Summary

The KPI tree shows how the North Star metric, **Paid Conversion Rate**, is supported by three main drivers:

1. **Trial Acquisition** — whether users enter the funnel and show intent to engage.
2. **Onboarding Activation** — whether users complete the onboarding flow smoothly.
3. **Early Engagement** — whether users stay active and interact meaningfully after onboarding.

Each driver breaks into two sub-drivers:
- Trial Acquisition: Landing Page Visit Rate, Trial Start Rate
- Onboarding Activation: Onboarding Completion Rate, Time to Complete Onboarding
- Early Engagement: Average Engagement Score, Core Feature Usage Rate

The tree also includes three guardrail metrics that protect business quality while conversion improves:
- Days to Convert
- Refund Request Rate
- Support Ticket Rate

This structure keeps the focus on conversion while making sure the campaign does not create low-quality signups, operational friction, or rushed conversions.

---
## Data Cleaning and Preparation

The raw dataset was prepared for analysis and saved to `analysis/experiment_analysis.xlsx`. The following checks were performed:

* **Duplicate User IDs:** 8 duplicate rows were identified and removed using Excel's Remove Duplicates tool to prevent double-counting. Each of the 8 row Ids(`USR-100096`,`USR-100433`,`USR-100541`,`USR-100917`,`USR-101059`,`USR-101210`,`USR-101232`,`USR-101362`) appearing twice were removed.    

* **Missing Values:** A missing value assessment was conducted across all variables. Missing values were identified in device_type, traffic_source, engagement_score, and days_to_convert. Missing values in `device_type`(18 records) and `traffic_source`(24 records) were replaced with "Unknown" to retain the rows without losing data. Blank values in `engagement_score` (14 records) were left as true nulls so they are naturally excluded from average calculations without skewing variance. Missing values in `days_to_convert` were retained because users who did not convert naturally do not have a conversion time recorded.     

* **Invalid Binary Values:** Binary variable validation was performed for `visited_landing_page`,` started_trial`,` completed_onboarding`,` converted_to_paid`, and `refund_requested`. All boolean columns were verified to contain only `0` or `1`. No corrections were needed. 

* **Group Counts:** The experiment group distribution was confirmed to have a balanced split between `Control` (690 users) and `Treatment` (710 users), indicating a reasonably balanced experiment split without major allocation bias. Device type distribution was proportionally equal across both groups, confirming no Sample Ratio Mismatch (SRM).   

* **Outliers in Revenue:** Revenue outlier detection was performed on `revenue_30d` using interquartile range analysis on non-zero revenue observations. Four high-value outliers were identified. 25% of paying users generated revenue below 404.02, while 75% of paying users generated revenue below 1178.67. IQR = Q3 − Q1=774.65. Upper Bound = Q3 + (1.5 × IQR)=2340.63. Any revenue > 2340.63 = Outlier. High revenue outliers were identified, but these records were retained because they may represent legitimate high-value customers rather than data errors.  

* **Segment Distribution:** Segment distribution analysis was performed across region, device_type, traffic_source, and plan_type to confirm that both Control and Treatment groups had reasonably balanced segment representation. This helps reduce experiment bias and improves confidence in later comparison analysis.

---

## Experiment Analysis Approach

1. Load and clean the dataset (handle duplicates, missing values, outliers)
2. Compute per-group rates for all 11 required metrics
3. Break down 3+ metrics by segment (region, device type, plan type)
4. Perform two-proportion z-test on paid conversion rate
5. Evaluate guardrail metrics to identify risks
6. Synthesize findings into a recommendation

> Full cleaned data: `analysis/experiment_analysis.xlsx`

---

## Hypothesis Test Summary

* **Metric Tested:** Paid Conversion Rate
* **Test Type:** Two-Tailed Z-Test for Proportions ($\alpha = 0.05$)
* **Results:** Control CR = 3.19%, Treatment CR = 7.04%. 
* **Statistical Output:** Z-Score = 3.264, P-value = 0.0011. 
* **Conclusion:** The P-value is strictly less than 0.05. We reject the null hypothesis. The Treatment group showed a statistically significant improvement in top-line conversion.

> Full test output: `analysis/hypothesis_test_notes.md` and `screenshots/hypothesis_test_output.png`

---

## Guardrail Metrics Considered

To ensure the conversion lift did not harm the business, the following guardrails were evaluated:
1. **Support Ticket Rate:** Increased from 14.78% to 24.78% (Failed)
2. **Average Revenue per Converted User:** Decreased from 1630.10 to 770.41 (Failed)
3. **Refund Rate:** Increased from 0.00% to 0.42% (Failed/Monitor)
4. **Days to Convert:** Improved from 8.86 to 6.40 (Passed)
5. **Engagement Score:** Improved from 57.03 to 62.94 (Passed)

---

## Final Recommendation

**Recommended action: Launch only for selected segments.**

Treatment significantly improves paid conversion, but it also increases support tickets and reduces revenue per converted user. That means the treatment is promising, but not yet strong enough for a full universal launch. The safest business choice is a targeted rollout in segments where the treatment performs well, while continuing to monitor weak segments such as Social traffic.

> Full recommendation: `outputs/recommendation_memo.md`

---

## Assumptions and Limitations

* **Assumptions:** We assumed missing `engagement_score` values were missing completely at random and excluded them from averages. We assume the 30-day window is a reliable proxy for long-term behavior.
* **Limitations:** We do not have visibility into long-term retention (churn after 30 days). A short-term spike in conversions could result in high early churn, which this dataset cannot currently measure.

---

## Screenshots Included

* `screenshots/summary_metrics.png`: Displays the core Control vs Treatment summary metrics table.
* `screenshots/hypothesis_test_output.png`: Displays the inputs, P-value, and Z-score of the statistical test.
* `screenshots/kpi_tree_preview.png`: Visualizes the relationship between the North Star metric, drivers, and guardrails.

