# Recommendation Memo
## New Onboarding & Activation Campaign — Launch Decision

## Executive Summary

The company ran an A/B experiment to evaluate whether a new onboarding and activation campaign (Treatment) outperforms the existing onboarding experience (Control) in driving paid user conversion. This memo documents the business problem, experiment methodology, metric analysis, hypothesis test results, guardrail evaluation, and a final data-backed recommendation.

---

## Section 1: Business Problem Statement

**Decision to be made:** Should the new onboarding campaign be fully launched to all users, held for further testing, deployed only to selected segments, or rejected entirely?

**Who it impacts:** New users face the onboarding experience directly, affecting their activation and retention. Product, Engineering, Growth, Finance, and Customer Support teams are each affected by changes in conversion rates, revenue, and support volume.

**Primary metric to improve:** **Paid Conversion Rate** — the share of users who convert to a paid subscription within 30 days. This metric directly measures the campaign's objective, contributes to subscription growth and customer acquisition efficiency, and is the clearest revenue signal available per user. Supporting metrics include Trial Start Rate, Onboarding Completion Rate, ARPU, and Engagement Score.

**Risks to monitor:**

| Guardrail Metric | Risk If Violated |
|---|---|
| Refund Rate | Signals low-quality or misled conversions |
| Support Ticket Rate | Indicates onboarding confusion or friction |
| Days to Convert | Fast conversions without revenue quality = quantity over quality |
| Engagement Score | Low engagement among converters predicts early churn |
| Segment-Level Conversion | A lift in one segment may mask a decline in another |

**Evidence required before recommendation:**
1. Statistically significant improvement in paid conversion rate (p < 0.05, two-proportion z-test)
2. No significant degradation in any guardrail metric
3. Consistent positive lift across at least 2 key segments (region, device type, or plan type)
4. Adequate sample size in both groups to ensure statistical power
5. Average revenue per converted user must not decrease in the Treatment group
6. Directional alignment between conversion rate and engagement score improvement

---

## Section 2: North Star Metric

**North Star Metric:** **Paid Conversion Rate** — the percentage of users who successfully convert from signup or trial users to a paid subscription within 30 days of signup.

Paid Conversion Rate is the best primary success metric because the purpose of the experiment is to determine whether the new onboarding experience creates more paying customers. It links directly to subscription revenue, acquisition efficiency, and the final leadership decision. This metric is the primary success indicator because the company operates on a subscription-based model, making subscriber conversion the strongest direct driver of revenue growth.

Other metrics such as Trial Start Rate, Onboarding Completion Rate, ARPU, Engagement Score, Refund Rate, and Support Ticket Rate are supporting metrics because they measure progress within the customer journey but do not directly generate revenue.

This metric connects to business growth by increasing the share of acquired users who generate revenue. Improving Paid Conversion Rate supports business growth by increasing recurring subscription revenue and improving customer acquisition efficiency. 

However, if optimized blindly, it could create risks such as higher refund rates, increased support tickets, reduced engagement quality, or negative user experience, making guardrail metrics essential before making a final decision.

---

## Section 3: KPI Tree Explanation

The KPI Tree was designed around `Paid Conversion Rate`, which was selected as the `North Star Metric` because the primary objective of the onboarding experiment is to increase the percentage of users who successfully convert into paying subscribers. Since the company operates on a subscription-based business model, improving paid conversion directly supports revenue growth and long-term customer value.

Three primary KPI drivers were identified as the main factors influencing conversion performance. The first driver, `Trial Acquisition`, measures how effectively users enter the product funnel and includes `Landing Page Visit Rate` and `Trial Start Rate`. The second driver, `Onboarding Activation`, evaluates how successfully users progress through the onboarding process and includes `Onboarding Completion Rate` and `Time to Complete Onboarding`. The third driver, `Early Engagement`, measures whether users actively interact with the product during the early experience and includes `Average Engagement Score` and `Core Feature Usage Rate`.

To ensure conversion improvements do not negatively impact overall business performance, guardrail metrics were also included. These guardrails include `Refund Request Rate`, `Support Ticket Rate`, and `Days to Convert`. These metrics help identify whether higher conversion rates are being achieved at the cost of poor customer experience, operational inefficiency, or lower quality conversions. The KPI Tree ensures the experiment is evaluated using both growth metrics and business risk indicators before making a final launch decision.

---

## Section 4: Experiment Result Summary

The experiment shows a clear improvement in the primary funnel metrics for the Treatment group versus Control. `Treatment` has a higher landing page visit rate, trial start rate, onboarding completion rate, paid conversion rate, average revenue per user, and average engagement score.

The strongest lift appears in **paid conversion rate**, which rises from **3.19% in Control** to **7.04% in Treatment**. Landing page visit rate also increases from **63.62%** to **72.39%**, trial start rate from **25.07%** to **29.01%**, and onboarding completion rate from **15.65%** to **21.13%**.

On monetization quality, **average revenue per user** increases slightly from **51.97** to **54.25**, but **average revenue per converted user** declines from **1630.10** to **770.41**. This suggests Treatment is generating more converters, but the average revenue per converter is lower, so the revenue quality of the converted cohort should be interpreted carefully.

Operational guardrails are mixed. **Refund rate** remains very low, but increases from **0.00%** to **0.42%**, while **support ticket rate** rises from **14.78%** to **24.79%**. **Average days to convert** improves from **8.86 days** to **6.40 days**, which is directionally positive for speed, but it should be balanced against the higher support burden.

### Segment-level result highlights

Treatment improves paid conversion across several segments, especially in **region** and **device type**. For example, paid conversion rate rises in every region, with the largest lift in **North** from **3.48%** to **8.89%**, and in **Mobile** from **2.58%** to **7.41%**.

By **traffic source**, Treatment lifts conversion for Email, Organic, Paid Search, and Referral, but Social declines from **7.75%** to **6.06%**. This means the overall treatment effect is positive, but it is not perfectly uniform across acquisition channels.

By **plan type**, Treatment increases trial start rate for **Basic** and **Free**, but decreases it for **Premium**. Specifically, trial start rate moves from **23.53%** to **28.02%** for Basic, from **25.00%** to **31.69%** for Free, and from **28.44%** down to **22.32%** for Premium.

---

## Section 5: Hypothesis Test Interpretation

A Two-Proportion two-tailed Z-Test was performed to determine whether the new onboarding campaign produced a statistically significant difference in Paid Conversion Rate between the Control and Treatment groups.

The Control group contained 690 users, of which 22 converted to paid subscriptions, resulting in a conversion rate of `3.19%`. The Treatment group contained 710 users, of which 50 converted to paid subscriptions, resulting in a conversion rate of `7.04%`.

The hypothesis test produced a `Z-Score` of `3.264` and a `P-value` of `0.0011`. Since the P-value is below the significance level of 0.05, the null hypothesis is `rejected`.

This confirms that the Treatment group performed significantly differently from the Control group, with a measurable improvement of `3.85` percentage points in Paid Conversion Rate. The experiment provides strong statistical evidence that the new onboarding campaign improves conversion performance.

---

## Section 6: Guardrail Analysis

Despite the massive lift in conversion rate, our guardrail metrics reveal severe operational risks and revenue quality concerns:
* **Support Ticket Rate (Major Risk):** Support tickets skyrocketed from 14.78% in Control to 24.78% in Treatment. The new onboarding flow is causing significant user friction and confusion.  

* **Revenue Quality / ARPU (Major Risk):** Average Revenue per Converted User drastically decreased from 1630.10 to 770.41. While total Average Revenue Per User (ARPU) slightly increased (51.97 to 54.25) due to the sheer volume of conversions, the *quality* of each converted user dropped by more than half. The new campaign is likely driving users toward cheaper plans.

* **Refund Rate (Minor Risk):** Refunds increased from 0.00% to 0.42%. While the absolute number is low, it indicates buyer's remorse not present in the original flow.

* **Engagement & Speed (Positive):** Average Days to Convert improved (8.86 days to 6.40 days), and Engagement Scores rose (57.03 to 62.94). Users are activating faster and engaging more, but at a high cost to support and revenue margins.

---

## Section 7: Segment-Level Insight

Segment-level analysis was performed across Region, Device Type, Traffic Source, and Plan Type using key performance metrics including Landing Page Visit Rate, Paid Conversion Rate, Refund Rate, and Support Ticket Rate.

The analysis showed that Treatment generally outperformed Control across most customer segments, indicating that the campaign improvement is broadly consistent rather than isolated to a single user segment.


* **By Traffic Source:** The campaign performed exceptionally well for "Referral" traffic (Conversion jumped from 2.47% to 10.98%). However, for "Social" traffic, the conversion rate actually *dropped* (7.75% to 6.06%).

* **By Plan Type:** Trial start rates increased for Free (25.0% to 31.6%) and Basic (23.5% to 28.0%) plans, but dropped significantly for Premium plans (28.4% down to 22.3%). This explains the drastic drop in Revenue Quality noted in the guardrail analysis.

* **By Device:** The Support Ticket rate increased heavily across all devices (Desktop, Mobile, and Tablet), proving the confusion is systemic to the new campaign, not a device-specific bug.

---

## Section 8: Final Recommendation

**Recommendation: Launch only for selected segment(s).**

The evidence supports a launch in segments where the treatment is clearly working and the risks are manageable, rather than a full rollout. Treatment significantly improves paid conversion overall, but it also increases support tickets and lowers revenue per converted user. The best business choice is to launch selectively, prioritizing high-performing segments such as **North, South, Mobile, Basic, Free, and Referral/Organic/Paid Search traffic**, while holding back or separately testing **Social traffic** and Premium-related flows.

---

## Section 9: Risks and Limitations

The biggest risk is that the Treatment flow may improve conversion partly by increasing support burden or by attracting lower-revenue converters. The increase in support tickets and the decline in revenue per converted user both point to potential quality trade-offs.

Another limitation is that segment performance is not uniform. Social traffic underperforms relative to the overall treatment result, so a full rollout could hide weak spots if the business only looks at the aggregate metric. The test also reflects one sample window, so long-term behavior such as retention, churn, and refund lag is not fully captured.

---

## Section 10: Next Steps

1. Investigate the cause of increased support ticket volume by reviewing user feedback and customer support interactions.

2. Conduct usability analysis on the new onboarding experience to identify points of user confusion or friction.

3. Perform additional retention analysis to determine whether newly converted users remain engaged and continue subscription usage over time.

4. Roll out the treatment only to the segments where it performed best and monitor guardrails closely.

5. Investigate the Social segment separately to understand why paid conversion declined there.

6. Track revenue quality over a longer window to confirm that the lower revenue per converted user is not a temporary effect.

7. Run a follow-up experiment for Premium users if that segment is strategically important.

