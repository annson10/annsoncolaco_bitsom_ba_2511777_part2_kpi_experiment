# Framing Hypotheses

##  Metric Being Tested
**Paid Conversion Rate** (The proportion of users who convert to a paid subscription).

##  Reason for Choosing This Metric
Paid Conversion Rate is the most direct measure of whether the onboarding campaign improves the core business outcome: turning users into paying customers. It connects directly to revenue growth and the final launch decision.   

Other metrics such as Landing Page Visit Rate, Trial Start Rate, and Onboarding Completion Rate are useful supporting metrics, but they only measure earlier stages of the customer journey and do not directly represent business revenue generation.

##  Null Hypothesis
* **Null Hypothesis ($H_0$):** The new onboarding campaign (Treatment) has no significant effect on the paid conversion rate compared to the existing experience (Control).     
  *( $P_{treatment} = P_{control}$)*

## Alternate Hypothesis
* **Alternate Hypothesis ($H_a$):** The new onboarding campaign (Treatment) results in a statistically significant difference in the paid conversion rate compared to the existing experience. 
  *($P_{treatment} \neq P_{control}$)*

## whether the test is 1 tailed or 2 tailed
* **Test Type:** Two-Tailed Hypothesis Test.
  * *Why Two-Tailed?* While our goal is to see if the Treatment is *better*, best practice in A/B testing dictates a two-tailed test so we can also mathematically detect if the new campaign is statistically *worse* than the Control.  
  The business decision depends on determining whether the treatment group performs significantly differently from the control group before deciding whether the campaign should be rolled out to all users.  
  Since both positive and negative differences affect the launch decision, a two-tailed test is most appropriate.

## Significance Level
* **Significance Level ($\alpha$):** 0.05 (95% Confidence Level).
  * *Why?* This is the industry standard for business experiments. We are willing to accept a 5% risk.

##  Interpretation Logic & Business Decision
To make our final recommendation, we will evaluate the resulting P-value against our significance level ($\alpha = 0.05$):

- If p-value < 0.05 and Treatment Rate > Control Rate, reject the null hypothesis. This means the Treatment group shows statistically significant improvement and the campaign may be considered successful.   

- If p-value < 0.05 and Treatment Rate < Control Rate, reject the null hypothesis. It suggests that the Treatment is statistically significantly worse.

- If p-value >= 0.05, fail to reject the null hypothesis. This means the observed improvement is not statistically significant and the company does not have enough evidence to confidently launch the campaign and say the campaign improved conversion.
- Even if the result is statistically significant, the final business decision must still consider guardrail metrics such as refund rate, support ticket rate, and days to convert. 

# Performing Hypothesis
##  Summary of Test Inputs
Control Group Users = 690   
Treatment Group Users = 710

Control Group Conversions = 22    
Treatment Group Conversions = 50

Control Conversion Rate = 3.19%   
Treatment Conversion Rate = 7.04%

##  Test Output
* **Test Statistic (Z-Score):** 3.264
* **P-Value:** 0.0011

##  Decision Rule
* If P-value < 0.05: Reject the Null Hypothesis (The difference is statistically significant).
* If P-value >= 0.05: Fail to reject the Null Hypothesis (The difference is not statistically significant).

##  Business Interpretation


The P-value of 0.0011 is strictly less than our 0.05 significance level, meaning we reject the null hypothesis. The Treatment group achieved a statistically significant improvement in the Paid Conversion Rate compared to the Control group.   
The Treatment group achieved a Paid Conversion Rate of 7.04%, compared to 3.19% in the Control group. This represents an improvement of 3.85 percentage points, indicating that the new onboarding campaign significantly improved user conversion performance.   
However, statistical significance alone is not sufficient for a final business recommendation. Additional guardrail metrics including Refund Rate, Support Ticket Rate, Engagement Score, and Days to Convert must also be evaluated before determining whether the campaign should be launched to all users.



