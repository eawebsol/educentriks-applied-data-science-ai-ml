# Day 2: Experimental Design and A/B Testing

## 1. Day Overview & Objectives

**Session Duration:** 90 minutes  
**Module:** Foundations  
**Dataset:** Synthetic E-commerce A/B Testing Dataset

### Core Learning Objectives

By the end of this session, students should be able to:

1. Explain the purpose of controlled experiments and A/B testing.
2. Identify control and treatment groups and understand random assignment.
3. Calculate conversion rates and formulate basic statistical hypotheses.
4. Interpret a statistical test result in terms of business impact.

### Prerequisites

- Basic Python programming and functions.
- Familiarity with Pandas and NumPy.
- Basic understanding of mean, percentage and probability.
- Day 1 concepts: population, sample and variables.

### Session Structure

| Activity | Duration |
|---|---:|
| Concepts and experimental design | 18 minutes |
| Dataset generation and guided analysis | 36 minutes |
| Hands-on modification | 18 minutes |
| Business interpretation and recap | 18 minutes |

---

## 2. Conceptual Deep Dive

### 2.1 What is Experimental Design?

Experimental design is the process of planning a controlled test to determine whether a change produces a measurable difference.

Consider an e-commerce company that wants to improve its checkout page.

The existing checkout page is Version A. The redesigned checkout page is Version B.

The business question is:

**Does the redesigned checkout page increase the percentage of visitors who complete a purchase?**

Instead of changing the checkout page for everyone and hoping for better results, the company conducts a controlled experiment.

### 2.2 Understanding A/B Testing

A/B testing compares two versions of a product, website, process or marketing activity.

| Component | Description |
|---|---|
| Version A | Existing experience; control group |
| Version B | Modified experience; treatment group |
| Control group | Visitors exposed to Version A |
| Treatment group | Visitors exposed to Version B |
| Outcome | Whether a visitor completes a purchase |

The visitors are randomly assigned to one of the two groups.

**Why random assignment matters**

Random assignment helps reduce systematic differences between the groups. Ideally, the groups should differ only in the experience being tested.

For example, assigning all mobile users to Version A and all desktop users to Version B would introduce bias because device type may influence purchasing behaviour.

### 2.3 Important Elements of an Experiment

- **Hypothesis:** A statement that can be tested using collected data.
- **Independent variable:** The factor being changed, such as checkout-page version.
- **Dependent variable:** The outcome being measured, such as conversion.
- **Control group:** The group receiving the existing experience.
- **Treatment group:** The group receiving the modified experience.
- **Success metric:** The measurement used to evaluate the experiment.

### 2.4 Conversion Rate

Conversion rate measures the percentage of visitors who complete the desired action.

\[
\text{Conversion Rate} =
\frac{\text{Number of Conversions}}{\text{Total Visitors}}
\times 100
\]

Example:

- Visitors: 1,000
- Completed purchases: 100

\[
\text{Conversion Rate} = \frac{100}{1000}\times100=10\%
\]

A conversion rate of 10% means that 10 out of every 100 visitors completed a purchase.

### 2.5 Hypothesis Testing

A/B testing uses statistical methods to evaluate whether the observed difference could reasonably be explained by random variation.

**Null hypothesis (H₀)**

There is no difference in conversion rates between Version A and Version B.

\[
H_0:p_A=p_B
\]

**Alternative hypothesis (H₁)**

There is a difference in conversion rates between the two versions.

\[
H_1:p_A\neq p_B
\]

This is a two-sided test. It checks whether the conversion rates differ, without assuming in advance that Version B must perform better.

### 2.6 Understanding the p-value

The p-value measures how unusual the observed result, or a more extreme result, would be if the null hypothesis were true.

For this session, we use a significance level of:

\[
\alpha=0.05
\]

| Result | Interpretation |
|---|---|
| p-value ≤ 0.05 | Reject the null hypothesis |
| p-value > 0.05 | Fail to reject the null hypothesis |

Important: A p-value does not tell us the probability that the null hypothesis is true. Statistical significance also does not automatically mean that a change is commercially valuable.

### 2.7 Statistical Significance vs Business Significance

Suppose Version B increases conversion from 10% to 10.5%.

The result may be statistically significant with a sufficiently large sample, but the business must still consider:

- Additional revenue generated.
- Implementation and maintenance costs.
- Customer experience.
- Operational complexity.
- Whether the improvement is sustainable.

A data analyst must explain both the statistical result and its business implications.

---

## 3. Practical Implementation & Code

### 3.1 Dataset Description

We will generate one synthetic e-commerce experiment dataset using Faker, NumPy and Pandas.

The dataset represents 2,000 visitors divided equally between two experiment groups.

| Column | Description |
|---|---|
| visitor_id | Unique visitor identifier |
| visit_date | Date of the visitor's session |
| device_type | Mobile, Desktop or Tablet |
| traffic_source | Organic, Paid, Social or Direct |
| experiment_group | A (Control) or B (Treatment) |
| converted | 1 if the visitor purchased; otherwise 0 |
| session_duration_sec | Session duration in seconds |
| pages_viewed | Number of pages viewed |
| order_value | Purchase amount; zero for non-conversions |

The dataset is synthetic and intended for learning. Its conversion probabilities are deliberately controlled so that students can practise statistical testing.

### 3.2 Install Required Libraries

```bash
python -m pip install faker numpy pandas scipy
```

### 3.3 Generate the Synthetic Dataset

```python
# Import required libraries
import numpy as np
import pandas as pd

from faker import Faker

# Create Faker instance
fake = Faker()

# Set seeds to make the dataset reproducible
fake.seed_instance(42)
rng = np.random.default_rng(42)

# Number of visitors
n_visitors = 2000

# Create equal-sized experiment groups
groups = np.array(
    ["A"] * (n_visitors // 2) +
    ["B"] * (n_visitors // 2)
)

# Randomly distribute visitors between groups
rng.shuffle(groups)

# Generate visitor dates
visit_dates = [
    fake.date_between(start_date="-30d", end_date="today")
    for _ in range(n_visitors)
]

# Generate device types
device_types = rng.choice(
    ["Mobile", "Desktop", "Tablet"],
    size=n_visitors,
    p=[0.60, 0.32, 0.08]
)

# Generate traffic sources
traffic_sources = rng.choice(
    ["Organic", "Paid", "Social", "Direct"],
    size=n_visitors,
    p=[0.35, 0.30, 0.15, 0.20]
)

# Define conversion probabilities for each experiment group
conversion_probabilities = np.where(
    groups == "A",
    0.10,   # Control group
    0.13    # Treatment group
)

# Generate conversion outcomes
converted = rng.binomial(
    n=1,
    p=conversion_probabilities
)

# Generate session duration in seconds
session_duration = np.round(
    np.clip(
        rng.gamma(shape=2.5, scale=75, size=n_visitors),
        10,
        900
    ),
    1
)

# Generate pages viewed
pages_viewed = np.clip(
    rng.poisson(lam=4, size=n_visitors) + 1,
    1,
    20
)

# Generate order values only for converted visitors
order_value = np.where(
    converted == 1,
    np.round(
        rng.lognormal(mean=3.7, sigma=0.55, size=n_visitors),
        2
    ),
    0.0
)

# Assemble the dataset
ab_test = pd.DataFrame({
    "visitor_id": [
        f"VIS-{i:05d}" for i in range(1, n_visitors + 1)
    ],
    "visit_date": visit_dates,
    "device_type": device_types,
    "traffic_source": traffic_sources,
    "experiment_group": groups,
    "converted": converted,
    "session_duration_sec": session_duration,
    "pages_viewed": pages_viewed,
    "order_value": order_value
})

# Save the dataset
ab_test.to_csv("synthetic_ab_testing.csv", index=False)

# Display basic information
print("Dataset generated successfully.")
print("Total visitors:", len(ab_test))

display(ab_test.head())
```

**Important observations about the generator**

- Faker supplies realistic dates.
- NumPy controls group assignment and experiment outcomes.
- Both groups have exactly 1,000 visitors.
- The treatment group has a deliberately higher conversion probability.
- The fixed seeds allow the same dataset to be regenerated.
- The generated data does not represent actual customer behaviour.

### 3.4 Inspect the Dataset

```python
# Check the dataset structure
print(ab_test.shape)

# Review column data types and missing values
ab_test.info()

# Check the first five records
display(ab_test.head())

# Check experiment group counts
print(ab_test["experiment_group"].value_counts())
```

Expected group counts:

| Group | Visitors |
|---|---:|
| A | 1,000 |
| B | 1,000 |

### 3.5 Calculate Conversion Rates

```python
# Group visitors by experiment version
conversion_summary = (
    ab_test
    .groupby("experiment_group")
    .agg(
        visitors=("visitor_id", "count"),
        conversions=("converted", "sum"),
        conversion_rate=("converted", "mean")
    )
)

# Convert the rate into a percentage
conversion_summary["conversion_rate"] *= 100

display(conversion_summary)
```

Expected output for the fixed seed:

| Group | Visitors | Conversions | Conversion Rate |
|---|---:|---:|---:|
| A | 1,000 | 91 | 9.1% |
| B | 1,000 | 122 | 12.2% |

Version B has a higher observed conversion rate.

### 3.6 Calculate the Absolute Conversion Difference

```python
rate_a = (
    ab_test.loc[
        ab_test["experiment_group"] == "A",
        "converted"
    ].mean()
)

rate_b = (
    ab_test.loc[
        ab_test["experiment_group"] == "B",
        "converted"
    ].mean()
)

# Express the difference in percentage points
absolute_difference = (rate_b - rate_a) * 100

print(f"Version A: {rate_a * 100:.2f}%")
print(f"Version B: {rate_b * 100:.2f}%")

print(
    f"Absolute conversion difference: "
    f"{absolute_difference:.2f} percentage points"
)
```

The absolute difference is 3.1 percentage points.

### 3.7 Perform a Chi-Square Test

Because conversion is a categorical outcome (converted or not converted), we can use a chi-square test of independence to examine the relationship between experiment group and conversion outcome.

```python
from scipy.stats import chi2_contingency

# Create a contingency table
contingency_table = pd.crosstab(
    ab_test["experiment_group"],
    ab_test["converted"]
)

display(contingency_table)

# Perform the chi-square test
chi2_stat, p_value, degrees_freedom, expected = (
    chi2_contingency(contingency_table)
)

print("Chi-square statistic:", round(chi2_stat, 4))
print("p-value:", round(p_value, 5))

# Interpret the result
alpha = 0.05

if p_value <= alpha:
    print("Reject the null hypothesis.")
    print("The conversion rates differ significantly.")
else:
    print("Fail to reject the null hypothesis.")
    print("There is insufficient evidence of a difference.")
```

Expected output:

```text
Chi-square statistic: 4.7290
p-value: 0.02966

Reject the null hypothesis.
The conversion rates differ significantly.
```

### 3.8 Interpret the Result

The p-value is approximately 0.02966, which is below 0.05.

Therefore, we reject the null hypothesis at the 5% significance level.

For this generated dataset:

- Version B has a higher observed conversion rate.
- The difference is statistically significant at the chosen significance level.
- This does not prove that every real-world implementation of Version B will improve conversions.
- A business decision should also consider revenue, implementation costs and customer experience.

**Statistical caution:** The chi-square test assumes independent observations and adequate expected cell counts. Our experiment uses one record per visitor and the expected counts are sufficiently large. A real experiment also needs suitable randomisation, sample-size planning and checks for experiment contamination.

---

## 4. Real-World Case Study: E-commerce Checkout Optimisation

### Business Scenario

An online retailer experiences a high checkout abandonment rate.

The product team proposes a simplified checkout process:

- Fewer form fields.
- Clearer delivery information.
- A more visible payment button.

Before deploying the new checkout to every visitor, the company conducts an A/B test.

### Experiment Design

| Element | Design |
|---|---|
| Business problem | Too many visitors abandon checkout |
| Version A | Existing checkout |
| Version B | Simplified checkout |
| Population | Eligible website visitors |
| Assignment | Random allocation |
| Primary metric | Purchase conversion rate |
| Secondary metrics | Order value and session duration |

### Business Decision

If Version B performs better and the result is statistically credible, the company may consider a wider rollout.

However, the team should also check whether the change affects average order value, payment failures or customer experience.

**Key lesson:** A data analyst does not simply report which version won. The analyst explains what was measured, how reliable the result is and whether the change is worth implementing.

---

## 5. Hands-On Exercise & Challenge

### Assignment: Evaluate a Checkout Experiment

Using `synthetic_ab_testing.csv`, analyse the two checkout versions.

### Tasks

1. Load the CSV file into Pandas.
2. Display the number of visitors in each experiment group.
3. Calculate conversions and conversion rates.
4. Compare conversion rates between A and B.
5. Calculate the absolute conversion difference in percentage points.
6. Create a contingency table.
7. Perform a chi-square test.
8. Write a short business recommendation based on the result.

### Expected Output

Students should submit:

- A conversion summary table.
- A contingency table.
- The chi-square statistic and p-value.
- A short explanation of the statistical result.
- A business recommendation supported by the analysis.

### Hint / Starter Framework

```python
# Load the dataset
data = pd.read_csv("synthetic_ab_testing.csv")

# Calculate group-level conversion metrics
# TODO

# Create a contingency table
# TODO

# Perform the chi-square test
# TODO

# Explain the result in business language
# TODO
```

---

## 6. Knowledge Check

**Question 1:** What is the purpose of a control group?

**Question 2:** Why is random assignment important in an A/B test?

**Question 3:** What does a conversion rate of 12% mean?

**Question 4:** If the p-value is 0.03 and alpha is 0.05, what is the statistical decision?

**Question 5:** Does statistical significance automatically mean that a business should implement the change?

### Answers for Self-Evaluation

1. It provides the baseline experience against which the treatment is compared.
2. It helps reduce systematic differences between the groups.
3. Twelve out of every 100 visitors completed the desired action.
4. Reject the null hypothesis at the 5% significance level.
5. No. Business value, costs, risks and customer experience must also be considered.

---

## Key Takeaways

- A/B testing compares two versions using controlled experimentation.
- Random assignment helps make the comparison fair.
- Conversion rate is a common business success metric.
- Hypothesis testing helps assess whether an observed difference is statistically significant.
- Statistical significance and business significance are not the same.
- A good data analyst translates statistical results into practical business recommendations.

**Next Session: Day 3 – ML Pipeline and Bias–Variance**

The next session introduces the machine learning workflow and explains how models can underfit or overfit data.
