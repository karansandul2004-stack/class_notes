# Statistics Notes for Data Analysis

Each topic below includes: **Note (concept)** → **Formula** → **Example** → **Scenario Question** → **Answer (with formula applied)**.

---

## 1. Mean

**Note:** The average of all values in a dataset. Best used when data is fairly symmetric with no major outliers.

**Formula:** Mean = Σx / n

**Example:** Daily sales: 200, 210, 190, 220, 180 → Mean = (200+210+190+220+180)/5 = 1000/5 = 200

**Scenario Question:** A store recorded monthly sales (in ₹'000) for 5 months: 50, 55, 60, 58, 52. What is the average monthly sales?

**Answer:**
Mean = (50+55+60+58+52)/5 = 275/5 = **₹55,000**

---

## 2. Median

**Note:** The middle value of sorted data. Preferred over mean when data has outliers or is skewed.

**Formula:** Sort data → middle value (or average of two middle values if n is even)

**Example:** Salaries: 25k, 27k, 28k, 30k, 200k → Median = 28k (mean would be misleadingly high due to 200k)

**Scenario Question:** A company's employee salaries (₹'000) are: 30, 32, 35, 40, 300. Why would you report median instead of mean here, and what is it?

**Answer:**
Sorted: 30, 32, 35, 40, 300 → Median = 35 (middle value).
Mean would be (30+32+35+40+300)/5 = 87.4 — heavily distorted by the 300 outlier, so median (₹35,000) better represents a "typical" employee's salary.

---

## 3. Mode

**Note:** The most frequently occurring value. Only measure usable on categorical data.

**Formula:** Value with highest frequency

**Example:** Product purchases: A, B, A, C, A, B → Mode = A

**Scenario Question:** Customer feedback ratings recorded: Good, Good, Average, Excellent, Good, Poor. What is the most common feedback?

**Answer:**
"Good" appears 3 times, more than any other rating → **Mode = Good**

---

## 4. Range

**Note:** Simplest spread measure; shows the gap between highest and lowest values. Very sensitive to outliers.

**Formula:** Range = Max − Min

**Example:** Data: 10, 12, 15, 18, 100 → Range = 100 − 10 = 90

**Scenario Question:** Daily website visitors over a week: 500, 520, 480, 510, 1200, 495, 505. What is the range, and what does it suggest?

**Answer:**
Range = 1200 − 480 = **720**. The large range (driven by the 1200 spike) suggests an outlier day — worth investigating before drawing conclusions about "typical" traffic.

---

## 5. Variance & Standard Deviation

**Note:** Measure how spread out values are around the mean. Low SD = consistent data; High SD = highly variable data.

**Formula:**
Variance = Σ(x − mean)² / n
SD = √Variance

**Example:** Data: 10, 12, 14 → Mean = 12 → Variance = [(10-12)²+(12-12)²+(14-12)²]/3 = (4+0+4)/3 = 2.67 → SD ≈ 1.63

**Scenario Question:** Two delivery routes have these delivery times (in minutes) — Route A: 30, 31, 29, 30 — Route B: 20, 40, 25, 35. Which route is more consistent?

**Answer:**
Route A mean = 30, deviations are tiny (±1) → very low SD.
Route B mean = 30, deviations are large (±5 to ±10) → high SD.
**Route A is more consistent**, even though both have the same average delivery time — this shows why SD matters alongside the mean.

---

## 6. Coefficient of Variation (CV)

**Note:** Normalizes SD relative to the mean so you can compare variability across datasets with different units/scales.

**Formula:** CV = (SD / Mean) × 100

**Example:** Dataset A: Mean=200, SD=20 → CV=10%. Dataset B: Mean=50, SD=10 → CV=20% → Dataset B is relatively more variable, even though its raw SD is smaller.

**Scenario Question:** Product A has average sales of ₹10,000 with SD ₹1,000. Product B has average sales of ₹2,000 with SD ₹500. Which product's sales are relatively more volatile?

**Answer:**
CV(A) = (1000/10000)×100 = 10%
CV(B) = (500/2000)×100 = 25%
**Product B is relatively more volatile**, even though its absolute SD is smaller than Product A's.

---

## 7. Percentiles & IQR (Outlier Detection)

**Note:** Percentiles show relative standing in a dataset. IQR (middle 50% spread) is used to set defensible outlier boundaries.

**Formula:**
IQR = Q3 − Q1
Lower fence = Q1 − 1.5×IQR
Upper fence = Q3 + 1.5×IQR

**Example:** Q1 = 20, Q3 = 50 → IQR = 30 → Lower fence = 20−45 = −25 → Upper fence = 50+45 = 95. Any value below −25 or above 95 is a potential outlier.

**Scenario Question:** Customer order values have Q1 = ₹500 and Q3 = ₹1,500. An order comes in at ₹4,000. Is it an outlier?

**Answer:**
IQR = 1500 − 500 = 1000
Upper fence = 1500 + 1.5×1000 = 1500+1500 = **₹3,000**
Since ₹4,000 > ₹3,000, **yes, it's a potential outlier** and should be investigated (bulk order? data entry error?) before deciding to keep or exclude it.

---

## 8. Z-score

**Note:** Tells you how many standard deviations a value is above/below the mean. Used to standardize and flag anomalies.

**Formula:** z = (x − μ) / σ

**Example:** Mean=50, SD=5, x=60 → z = (60−50)/5 = 2 → 2 SDs above the mean

**Scenario Question:** Average customer transaction is ₹1,000 with SD ₹150. A transaction of ₹1,450 occurs. How unusual is it?

**Answer:**
z = (1450 − 1000)/150 = 450/150 = **3**
A z-score of 3 means this transaction is 3 standard deviations above average — statistically unusual and worth flagging for review (potential fraud or a high-value customer).

---

## 9. Classical & Conditional Probability

**Note:** Classical probability is basic likelihood from possible outcomes; conditional probability refines that likelihood using known related information.

**Formula:**
P(A) = Favorable outcomes / Total outcomes
P(A|B) = P(A∩B) / P(B)

**Example:** P(customer buys phone) = 0.2 generally, but P(buys phone | already bought a case) = 0.6 — much higher given the related purchase.

**Scenario Question:** Out of 200 customers, 40 bought Product A. Among those 40, 24 also bought Product B. What is P(bought B | bought A)?

**Answer:**
P(A) = 40/200 = 0.2
P(A∩B) = 24/200 = 0.12
P(B|A) = P(A∩B)/P(A) = 0.12/0.2 = **0.6 (60%)**
So 60% of Product A buyers also buy Product B — useful for bundling/cross-sell strategy.

---

## 10. Bayes' Theorem

**Note:** Updates a probability when new evidence/information becomes available. Basis of predictive scoring (e.g., churn risk).

**Formula:** P(A|B) = [P(B|A) × P(A)] / P(B)

**Example:** Base churn rate P(churn)=0.1. Among churners, 70% had filed a complaint. Overall, 15% of all customers filed a complaint. → Updated churn probability given a complaint is filed.

**Scenario Question:** 10% of customers churn overall. 70% of churners had filed a complaint, while only 15% of all customers filed a complaint. What's the probability a customer churns, given they filed a complaint?

**Answer:**
P(Churn) = 0.10, P(Complaint|Churn) = 0.70, P(Complaint) = 0.15
P(Churn|Complaint) = (0.70 × 0.10) / 0.15 = 0.07/0.15 = **0.467 (≈47%)**
A customer who complains has a much higher churn risk (47%) than the baseline (10%) — flag them for retention outreach.

---

## 11. Binomial Distribution

**Note:** Models the number of successes in a fixed number of independent trials, each with the same probability of success.

**Formula:** P(X=k) = C(n,k) × p^k × (1−p)^(n−k)

**Example:** 10 emails sent, each with a 20% open rate → probability exactly 3 are opened uses the binomial formula with n=10, p=0.2, k=3.

**Scenario Question:** A sales rep calls 5 leads, each with a 40% chance of converting. What's the probability exactly 2 convert?

**Answer:**
n=5, p=0.4, k=2
P(X=2) = C(5,2) × 0.4² × 0.6³ = 10 × 0.16 × 0.216 = **0.3456 (≈34.6%)**
There's about a 35% chance exactly 2 out of 5 leads convert — useful for setting realistic sales targets.

---

## 12. Poisson Distribution

**Note:** Models the number of events in a fixed interval when events happen independently at a known average rate (λ).

**Formula:** P(X=k) = [e^(−λ) × λ^k] / k!

**Example:** Average 20 support tickets/day → probability of exactly 25 tickets tomorrow is calculated using λ=20, k=25.

**Scenario Question:** A website averages 5 crashes per month. What's the probability of exactly 2 crashes next month?

**Answer:**
λ=5, k=2
P(X=2) = [e^(−5) × 5²]/2! = [0.0067 × 25]/2 = 0.1675/2 = **≈0.084 (8.4%)**
There's about an 8.4% chance of exactly 2 crashes next month — helps set support-team staffing expectations.

---

## 13. Normal Distribution

**Note:** Bell-shaped, symmetric distribution; foundation for most statistical inference (mean = median = mode).

**Concept only — no single closed formula needed for DA use; recognized via shape and via z-scores.**

**Example:** Customer heights, test scores, and many aggregated business KPIs approximate a normal distribution.

**Scenario Question:** A dataset of exam scores is bell-shaped and symmetric, with mean = median = mode = 70. What distribution is this, and why does it matter for analysis?

**Answer:**
This is a **normal distribution**. It matters because many statistical tests (t-tests, z-tests, confidence intervals) assume approximate normality — recognizing this shape confirms those tools can be validly applied.

---

## 14. Central Limit Theorem (CLT)

**Note:** As sample size grows, the sampling distribution of the sample mean becomes approximately normal — even if the original data isn't normal.

**Concept:** Sample data → repeated sampling → sample means → approximately normal distribution

**Example:** Customer spending is skewed, but if you repeatedly take samples of 50 customers and average each sample, those averages will form a roughly normal distribution.

**Scenario Question:** Why can you apply a t-test on a sample mean of customer spending, even though the raw spending data is heavily skewed?

**Answer:**
Because of the **Central Limit Theorem** — with a sufficiently large sample size, the *sampling distribution of the mean* becomes approximately normal regardless of the original data's shape, which justifies using t-tests and confidence intervals on the sample mean.

---

## 15. Hypothesis Testing & p-value

**Note:** Formal framework to test if an observed effect is real or due to random chance.

**Formula:**
H₀: no effect/difference, Hₐ: effect/difference exists
Decision rule: p < 0.05 → reject H₀; p ≥ 0.05 → fail to reject H₀

**Example:** Testing whether a new website layout increases conversion rate vs. the old layout.

**Scenario Question:** After running an A/B test on a new checkout page, you get a p-value of 0.02. What do you conclude?

**Answer:**
Since p = 0.02 < 0.05, **reject H₀** — there is statistically significant evidence that the new checkout page performs differently from the old one.

---

## 16. Type I & Type II Errors

**Note:** Type I = false positive (rejecting a true H₀); Type II = false negative (failing to reject a false H₀).

**Example:** Concluding a marketing campaign worked when it actually didn't (Type I) vs. concluding it didn't work when it actually did (Type II).

**Scenario Question:** A company rolls out a new pricing strategy and the test wrongly concludes there's no effect, when in reality the strategy did increase revenue. What type of error is this?

**Answer:**
This is a **Type II error** — failing to detect a real effect (false negative). It's costly because the company may abandon a strategy that was actually working.

---

## 17. One-sample, Two-sample & Paired t-tests

**Note:**
- One-sample: compare 1 sample mean to a known/reference value
- Two-sample: compare means of 2 independent groups
- Paired: compare the same subjects measured twice (before/after)

**Formula (concept):** t = (difference in means) / (standard error of the difference)

**Example:** Paired t-test on before/after revenue for the same 50 stores after a new promotion.

**Scenario Question:** You want to check if a training program improved employee performance scores, measuring the same 30 employees before and after training. Which test should you use, and why?

**Answer:**
Use a **paired t-test**, because the same employees are measured twice (before and after) — this test accounts for that relationship and is more precise than treating the two sets as independent groups.

---

## 18. Chi-Square Test

**Note:** Tests whether two categorical variables are independent or associated, using a contingency table.

**Formula (concept):** χ² = Σ [(Observed − Expected)² / Expected]

**Example:** Testing whether gender and product preference are related, using a table of counts by gender × product.

**Scenario Question:** A company wants to know if customer region (North/South) is related to whether they churn or not. What test should be used?

**Answer:**
Use a **chi-square test of independence**, since both variables (region and churn status) are categorical. Build a contingency table of counts, then test if the observed counts differ significantly from what independence would predict.

---

## 19. ANOVA (Analysis of Variance)

**Note:** Compares means across 3 or more groups at once, avoiding the inflated false-positive risk of running many separate t-tests.

**Formula:** F = Between-group variance / Within-group variance

**Example:** Comparing average purchase value across three age groups: 18–30, 31–45, 46+.

**Scenario Question:** A retailer wants to compare average spend across 4 store locations. Why use ANOVA instead of running 6 separate t-tests (one for each pair)?

**Answer:**
Running 6 separate t-tests inflates the chance of a **Type I error** (false positive) across all the comparisons. **ANOVA** tests all 4 groups simultaneously using the F-statistic (between-group vs within-group variance), controlling that overall error rate in a single test.

---

## 20. Pearson & Spearman Correlation

**Note:** Pearson measures linear relationship strength (−1 to +1); Spearman measures monotonic relationship using ranks (better for non-linear or ordinal data).

**Example:** Advertising spend vs. sales — Pearson correlation of 0.85 indicates a strong positive linear relationship.

**Scenario Question:** You find a Pearson correlation of 0.90 between advertising spend and sales. Can you conclude advertising *causes* higher sales?

**Answer:**
**No.** A correlation of 0.90 shows a strong positive linear relationship, but **correlation does not imply causation** — other factors (seasonality, pricing, competitor activity) could be driving both variables simultaneously. Further causal analysis (e.g., controlled experiments) would be needed to confirm causation.

---

## 21. Simple Linear Regression

**Note:** Predicts one numeric outcome from one predictor variable.

**Formula:** Y = β₀ + β₁X

**Example:** Sales = β₀ + β₁(Advertising) — β₁ tells you the expected increase in sales per unit increase in ad spend.

**Scenario Question:** A regression model gives: Sales = 10,000 + 500(Advertising). What does the model predict if advertising spend is 20 units, and how do you interpret the 500 coefficient?

**Answer:**
Predicted Sales = 10,000 + 500(20) = 10,000 + 10,000 = **20,000**
The coefficient (500) means each one-unit increase in advertising is associated with an expected increase of 500 units in sales, holding the model's assumptions constant.

---

## 22. Multiple Linear Regression

**Note:** Predicts an outcome using two or more predictors, isolating each one's individual effect while controlling for the others.

**Formula:** Y = β₀ + β₁X₁ + β₂X₂ + ... + ε

**Example:** Spending = β₀ + β₁(Age) + β₂(Income) — lets you see the effect of Age on spending while holding Income constant, and vice versa.

**Scenario Question:** A model predicts customer spending using both Age and Income: Spending = 200 + 2(Age) + 0.05(Income). If Age=30 and Income=50,000, what's the predicted spending?

**Answer:**
Spending = 200 + 2(30) + 0.05(50,000) = 200 + 60 + 2,500 = **₹2,760**

---

## 23. R-squared (R²)

**Note:** Proportion of variance in the outcome explained by the regression model (0 to 1). Higher isn't always "more accurate" — it measures fit, not correctness or causation.

**Example:** R² = 0.85 means the model explains 85% of the variation in the outcome variable using the data it was built on.

**Scenario Question:** Your sales prediction model has R² = 0.60. Is this a "bad" model, and does it mean 40% of predictions are wrong?

**Answer:**
R² = 0.60 means the model explains 60% of the variation in sales — it does **not** mean 40% of individual predictions are "wrong." Whether 0.60 is "good enough" depends on the business context and what other models in that domain typically achieve; it should be considered alongside residual analysis and business judgment, not in isolation.

---

*Notes scoped to statistics topics directly relevant to data analysis — descriptive stats, probability, distributions, inference, and regression.*
