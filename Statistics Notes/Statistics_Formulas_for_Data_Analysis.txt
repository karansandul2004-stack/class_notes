# Statistics & Probability Formula Reference for Data Analysis

A practical cheat sheet: formula → name → when/where to use it → why it matters.

---

## 1. Descriptive Statistics (Summarizing Data)

### Mean
**Formula:** Mean = Σx / n

**When to use:** Any time you need a single "typical value" summary of numeric data — average order value, average delivery time, average customer age.

**Why:** It's the most common summary stat and the input to many other formulas (variance, z-score, regression). Use it when data is roughly symmetric with no extreme outliers.

**Watch out:** Skewed data or outliers (e.g., one $50,000 order among $50 orders) will distort the mean — switch to median in that case.

---

### Median
**Formula:** Middle value when data is sorted (average of two middle values if n is even)

**When to use:** Income data, house prices, customer spend — any dataset prone to outliers or skew.

**Why:** It's resistant to extreme values, so it better represents the "typical" customer/transaction when a few large values would drag the mean upward.

---

### Mode
**Formula:** Most frequently occurring value

**When to use:** Categorical data (most common product bought, most common complaint type) or to describe the peak of a distribution.

**Why:** Only stat that works on non-numeric/categorical data; useful for "what's most common" business questions.

---

### Range
**Formula:** Range = Max − Min

**When to use:** Quick first-look spread check during initial EDA.

**Why:** Fast and simple, but very sensitive to outliers — one extreme value inflates it. Use only as a rough first pass, not a final spread metric.

---

### Variance & Standard Deviation
**Formula:**
Variance = Σ(x − mean)² / n (or n−1 for sample)
SD = √Variance

**When to use:** Whenever you need to know how spread out or consistent your data is — sales consistency across stores, variability in delivery times, risk/volatility in returns.

**Why:** Low SD → values cluster near the mean (predictable/consistent). High SD → values are widely spread (inconsistent/risky). Almost every downstream statistical test assumes you know this.

**Python:** `df['col'].std()`

---

### Coefficient of Variation (CV)
**Formula:** CV = (SD / Mean) × 100

**When to use:** Comparing variability between two datasets measured on different scales or units — e.g., comparing volatility of revenue (in ₹) vs. units sold (count).

**Why:** Raw SD can't be compared across different units; CV normalizes it into a percentage so comparisons are meaningful.

---

### Percentile
**Formula:** Position-based ranking of a value within sorted data

**When to use:** Identifying top/bottom performers — top 10% of spenders, bottom 25% of response times, salary bands.

**Why:** Lets you segment customers/employees/products by relative standing rather than absolute value, which is more useful for targeting and benchmarking.

---

### Interquartile Range (IQR) & Outlier Fences
**Formula:**
IQR = Q3 − Q1
Lower fence = Q1 − 1.5×IQR
Upper fence = Q3 + 1.5×IQR

**When to use:** Any time you need a defensible, repeatable rule for flagging outliers before cleaning data or before running tests that assume no extreme values.

**Why:** It's the standard behind boxplots and a widely accepted, non-arbitrary way to say "this value is unusual" — much better than eyeballing.

---

### Z-score
**Formula:** z = (x − μ) / σ

**When to use:** Standardizing values so you can compare things measured on different scales (e.g., comparing a student's test score to a salary figure), or flagging anomalies (a value with |z| > 3 is often flagged as extreme).

**Why:** Converts any raw number into "how many standard deviations from average" — a universal, comparable unit. Also required before many statistical tests and z-tests.

---

## 2. Probability

### Classical Probability
**Formula:** P(A) = Favorable Outcomes / Total Outcomes

**When to use:** Simple scenario modeling — probability a random customer is from a given segment, probability of a defect in a batch.

**Why:** Baseline probability logic; foundation for every other probability formula below.

---

### Complement Rule
**Formula:** P(not A) = 1 − P(A)

**When to use:** Whenever it's easier to calculate the opposite event — e.g., "probability at least one of 10 emails bounces" is easier via 1 − P(none bounce).

**Why:** Quick shortcut that avoids complex direct calculations.

---

### Conditional Probability
**Formula:** P(A|B) = P(A∩B) / P(B)

**When to use:** "Given that a customer did X, what's the chance they'll do Y?" — probability of purchase given prior browsing, probability of churn given a support complaint.

**Why:** This is the logic behind targeting, segmentation, and recommendation systems — it lets you refine probability using known context instead of a blind average.

---

### Bayes' Theorem
**Formula:** P(A|B) = [P(B|A) × P(A)] / P(B)

**When to use:** Updating a prior belief/probability as new evidence comes in — updating churn risk after observing recent behavior, spam detection, medical/quality-testing scenarios.

**Why:** Lets you combine a base rate with new data to get a more accurate, revised probability — core to predictive scoring models.

---

## 3. Probability Distributions

### Bernoulli Distribution
**Concept:** One trial, two outcomes (success/failure)

**When to use:** Modeling a single binary event — did the customer buy or not, did the email get opened or not.

**Why:** Simplest building block for binary outcome modeling; basis of logistic regression and binomial distribution.

---

### Binomial Distribution
**Concept:** Number of successes across a fixed number of independent trials

**When to use:** "Out of 100 customers contacted, how many will convert?" — fixed number of trials, each with the same success probability.

**Why:** Lets you estimate the probability of getting a specific number of successes, useful for campaign planning and quality control.

---

### Poisson Distribution
**Formula:** P(X = k) = [e^(−λ) × λ^k] / k!

**When to use:** Modeling counts of events over a fixed time/space interval where events are rare/random — support tickets per day, website crashes per week, defects per batch.

**Why:** Lets you estimate the probability of an unusual count occurring (e.g., "how likely are 25 tickets when average is 20?") — useful for staffing and capacity planning.

---

### Normal Distribution
**Concept:** Bell-shaped, symmetric; Mean = Median = Mode; defined by μ and σ

**When to use:** Modeling naturally occurring continuous variables — heights, test scores, many aggregated business metrics.

**Why:** Many statistical tests (t-tests, z-tests, confidence intervals) assume approximate normality — recognizing it tells you which tools are valid to apply.

---

## 4. Sampling & Inference Foundations

### Central Limit Theorem (CLT)
**Concept:** Sampling distribution of the sample mean becomes approximately normal as sample size grows, regardless of the population's original shape.

**When to use:** Justifying the use of t-tests, z-tests, and confidence intervals on sample means — even if the raw data isn't normally distributed.

**Why:** It's the theoretical backbone that makes most inferential statistics valid on real-world (non-normal) business data, as long as your sample size is reasonably large.

---

### Standard Error (implied companion to CLT)
**Formula:** SE = σ / √n

**When to use:** Estimating how much a sample mean is likely to vary from the true population mean — used inside confidence intervals and t-tests.

**Why:** Larger samples shrink the standard error, meaning more reliable estimates — this quantifies "how much can I trust this sample's average."

---

## 5. Hypothesis Testing

### Hypotheses Setup
**Formula:** H₀: μ_new = μ_old (no effect) vs. Hₐ: μ_new ≠/>/< μ_old (effect exists)

**When to use:** Any "did the change actually work" question — did a new discount increase sales, did a new UI increase conversion.

**Why:** Frames a business question into a testable statistical statement — the first step of any A/B test or experiment analysis.

---

### p-value Decision Rule
**Formula:** If p < 0.05 → reject H₀; if p ≥ 0.05 → fail to reject H₀

**When to use:** After running any statistical test (t-test, chi-square, ANOVA) to decide if a result is "statistically significant."

**Why:** Converts a test statistic into a clear go/no-go decision — but remember it tells you about statistical significance, not necessarily practical/business importance.

---

### Type I & Type II Errors
**Concept:**
Type I = rejecting a true H₀ (false positive)
Type II = failing to reject a false H₀ (false negative)

**When to use:** Any time you're evaluating risk in a decision based on a test — e.g., wrongly concluding a campaign worked (Type I) vs. missing a real effect (Type II).

**Why:** Helps you weigh the cost of being wrong in either direction, which matters when choosing significance thresholds and sample sizes.

---

### One-sample t-test
**When to use:** Comparing one sample's mean against a known/reference value — "is average delivery time different from the promised 3 days?"

**Why:** Tells you if an observed average is significantly different from a fixed target/benchmark.

---

### Two-sample (independent) t-test
**When to use:** Comparing means of two separate, unrelated groups — Group A vs. Group B average purchase value.

**Why:** Determines if a difference between two independent groups is real or just random variation.

---

### Paired t-test
**When to use:** Comparing the same subjects measured twice — before vs. after a campaign, pre/post training scores.

**Why:** Accounts for the fact that the same units are measured twice, giving a more precise test than treating before/after as independent groups.

**Python:** `scipy.stats.ttest_rel()`

---

### Chi-Square Test
**When to use:** Testing whether two categorical variables are independent — e.g., is product preference related to gender, is churn related to contract type.

**Why:** T-tests need numeric data; chi-square is the equivalent tool for categorical/count data (built from a contingency table).

---

### ANOVA (Analysis of Variance)
**Formula:** F = Between-group variance / Within-group variance

**When to use:** Comparing means across three or more groups — average purchase value across three age brackets.

**Why:** Running many separate t-tests inflates the chance of a false positive (Type I error); ANOVA tests all groups at once, controlling that risk.

---

## 6. Correlation & Regression

### Pearson Correlation
**Concept:** Measures strength/direction of a linear relationship (range −1 to +1)

**When to use:** Checking if two numeric variables move together linearly — advertising spend vs. sales, temperature vs. ice-cream sales.

**Why:** Quantifies relationship strength before building a model; values near ±1 = strong relationship, near 0 = weak/no linear relationship. Remember: correlation ≠ causation.

---

### Spearman Correlation
**Concept:** Measures monotonic relationship strength using ranks, not raw values

**When to use:** When the relationship isn't linear, or data is ordinal (rankings, satisfaction scores) rather than truly numeric.

**Why:** More robust than Pearson when data has outliers or a non-linear (but still consistent-direction) relationship.

---

### Simple Linear Regression
**Formula:** Y = β₀ + β₁X

**When to use:** Predicting one numeric outcome from one predictor — predicting sales from advertising spend.

**Why:** β₁ directly tells you the expected change in Y for each one-unit increase in X — turns a relationship into an actionable, quantified prediction.

---

### Multiple Linear Regression
**Formula:** Y = β₀ + β₁X₁ + β₂X₂ + ... + ε

**When to use:** Predicting an outcome influenced by several factors at once — predicting customer spending from age, income, and region together.

**Why:** Isolates the effect of each variable while controlling for the others — critical because real business outcomes are rarely driven by just one factor.

---

### R-squared (R²)
**Concept:** Proportion of variance in the outcome explained by the model (0 to 1)

**When to use:** Evaluating how well a regression model fits the data — reported alongside every regression result.

**Why:** Tells you how much to trust the model's explanatory/predictive power. High R² doesn't guarantee accuracy on new data or prove causation — it just measures fit to the data used.

---

## Quick Reference: Which Tool for Which Situation

| Business Question | Formula/Test to Use |
|---|---|
| What's the typical value? | Mean / Median |
| How spread out is the data? | Standard Deviation / IQR |
| Is this data point unusual? | Z-score / IQR fences |
| What's the chance of an event? | Classical / Conditional Probability |
| How to update a probability with new info? | Bayes' Theorem |
| Modeling counts per day/interval | Poisson |
| Comparing 1 group's average to a target | One-sample t-test |
| Comparing 2 independent groups | Two-sample t-test |
| Comparing the same group before/after | Paired t-test |
| Comparing 3+ groups | ANOVA |
| Testing 2 categorical variables' relationship | Chi-square test |
| Measuring how 2 numeric variables relate | Pearson/Spearman correlation |
| Predicting a numeric outcome | Linear / Multiple Regression |
| Justifying use of these tests on real data | Central Limit Theorem |

---
*Reference compiled from Statistics & Probability interview prep material, expanded with usage context for data analysis practice.*
