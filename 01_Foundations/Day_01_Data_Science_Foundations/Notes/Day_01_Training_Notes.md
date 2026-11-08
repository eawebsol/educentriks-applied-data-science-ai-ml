# Day 1: Data Science Foundations
## Student Training Notes

**Programme:** Applied Data Science, AI/ML & Generative AI  
**Module:** 1 – Data Science Foundations and Statistical Thinking  
**Session Duration:** 1.5 Hours  
**Level:** Foundation  
**Tools:** Python, Jupyter Notebook, pandas, NumPy

---

# 1. Day Overview and Learning Objectives

## 1.1 Introduction

Data Science is not simply about writing Python code, creating charts or applying machine learning algorithms.

It is about using data to understand problems, discover meaningful patterns, evaluate possible solutions and support better business decisions.

Organisations generate enormous amounts of information through their daily operations:

- Retail companies record customer purchases and product sales.
- Banks record transactions and customer interactions.
- Hospitals maintain patient and operational records.
- E-commerce companies track website visits, orders and delivery performance.
- Telecommunications companies monitor network usage and customer complaints.

However, collecting data alone does not create business value.

The real value comes from asking the right questions and extracting useful information from the available data.

**Think like a Data Scientist:** Before asking which algorithm to use, ask what business problem needs to be solved.

## 1.2 Learning Objectives

By the end of this session, you should be able to:

1. Differentiate Data Science, Data Analytics and traditional reporting.
2. Explain the major stages of the Data Science lifecycle.
3. Translate a business question into an analytical problem.
4. Understand population, sample, variables and common data types.
5. Interpret basic descriptive statistics, distributions and correlation.
6. Explain how statistical observations can support business decisions.

## 1.3 Prerequisites

- Basic understanding of Python.
- Familiarity with variables, functions and libraries.
- Basic knowledge of working with tabular data.
- Python 3.13.x and Jupyter Notebook environment.

---

# 2. Conceptual Deep Dive

## 2.1 What is Data Science?

Data Science is an interdisciplinary field that combines:

- Statistics and mathematics.
- Programming and computational techniques.
- Data analysis and visualisation.
- Machine learning and predictive modelling.
- Business and domain knowledge.

Its purpose is to extract useful information from data and support decision-making.

### A simple business example

Consider an online retail company.

The company collects information about:

- Customers.
- Products.
- Orders.
- Transaction amounts.
- Discounts.
- Payment methods.
- Delivery performance.

Management wants to understand why monthly revenue is declining.

A Data Science approach would involve:

1. Understanding the revenue problem.
2. Identifying the information required.
3. Collecting relevant data.
4. Exploring and analysing the data.
5. Identifying possible reasons for the decline.
6. Communicating findings and recommending actions.

Notice that the process begins with the business problem, not with an algorithm.

## 2.2 Data Science vs Data Analytics vs Traditional Reporting

These three areas are related, but they do not have exactly the same purpose.

| Area | Primary Purpose | Typical Question |
|---|---|---|
| Traditional Reporting | Present information about business performance | What were last month's sales? |
| Data Analytics | Examine data to understand performance and patterns | Why did sales decline? |
| Data Science | Apply statistical and computational methods to investigate problems and develop predictive or data-driven solutions | Which customers are likely to stop purchasing? |

### Example: E-commerce business

Suppose an online retailer wants to improve customer retention.

**Traditional Reporting**

A report shows:
- Total customers.
- Monthly orders.
- Total revenue.
- Number of inactive customers.

**Data Analytics**

An analyst investigates:
- Which customer groups are becoming inactive?
- Which products have declining repeat purchases?
- Is customer inactivity associated with delivery delays?

**Data Science**

A Data Scientist may develop a model to:
- Estimate the likelihood that a customer will stop purchasing.
- Identify important factors associated with customer inactivity.
- Support targeted retention strategies.

### Important distinction

The boundaries between these disciplines can overlap. Data Analytics can include advanced statistical analysis, and Data Science can involve reporting and visualisation.

The distinction is primarily about the questions being addressed and the methods used.

**Business takeaway:** Reports describe performance. Analysis helps explain performance. Data Science can extend this work towards predictive and more advanced data-driven solutions.

---

# 3. Understanding the Data Science Lifecycle

A Data Science project follows a structured process.

This process is commonly called the Data Science lifecycle.

The lifecycle helps ensure that a project addresses the correct problem, uses appropriate information and produces useful outcomes.

## 3.1 Major Stages

### Stage 1: Business Problem Understanding

The first step is to understand the business requirement.

Questions to ask:

- What problem is the organisation facing?
- Why is the problem important?
- Who is affected?
- What decision needs to be supported?
- How will success be measured?

**Example:**

An online retailer notices that customers are not returning to purchase products.

Possible business objective:

Improve customer retention and increase repeat purchases.

### Stage 2: Data Collection

Once the problem is understood, identify the data required.

Possible sources include:

- Databases.
- Excel and CSV files.
- Business applications.
- APIs.
- Website activity.
- Transaction systems.
- Customer feedback systems.

**Example:**

To understand repeat purchases, the retailer may require:

- Customer identifiers.
- Order dates.
- Order amounts.
- Product categories.
- Customer purchase history.

The required data depends on the business question.

### Stage 3: Data Preparation and Exploration

Collected data may contain:

- Missing values.
- Duplicate records.
- Incorrect data types.
- Inconsistent categories.
- Invalid values.

Data preparation ensures that the information is suitable for analysis.

Exploration helps us understand:

- What information is available?
- What values occur frequently?
- Are there unusual observations?
- Are there patterns between variables?

### Stage 4: Analysis and Modelling

At this stage, appropriate techniques are selected.

Depending on the problem, these may include:

- Descriptive statistics.
- Statistical testing.
- Regression.
- Classification.
- Clustering.
- Forecasting.
- Deep learning.

Not every Data Science project requires machine learning.

For example, a business may obtain sufficient insight through statistical analysis without developing a predictive model.

### Stage 5: Evaluation and Communication

The results must be evaluated and communicated.

Questions include:

- Does the analysis answer the original question?
- Are the findings reliable?
- Are there limitations?
- Can management understand the findings?
- What actions should the organisation consider?

A technically correct result is not automatically a useful business result.

### Stage 6: Deployment and Monitoring

When a solution is ready for operational use, it may be deployed.

Examples:

- A prediction service integrated into a business application.
- A customer-risk dashboard.
- A forecasting system used by inventory planners.
- An automated classification process.

After deployment, performance must be monitored.

Business conditions and customer behaviour can change, so a solution that performs well today may require maintenance or improvement later.

## 3.2 Lifecycle Summary

| Stage | Main Activity | Business Question |
|---|---|---|
| Business Understanding | Define the problem | What are we trying to solve? |
| Data Collection | Obtain relevant information | What data do we need? |
| Preparation and Exploration | Examine and prepare the data | Can we trust and understand the data? |
| Analysis and Modelling | Apply appropriate techniques | What can the data tell us? |
| Evaluation and Communication | Validate and explain findings | Does the result support a decision? |
| Deployment and Monitoring | Put the solution into use and monitor it | Is the solution continuing to work? |

**Remember:** The lifecycle is not always strictly linear. A project may return to earlier stages when new information or problems are discovered.

---

# 4. Understanding and Formulating Business Problems

One of the most important skills in Data Science is the ability to convert a business requirement into an analytical question.

A poorly defined problem can lead to incorrect analysis, even when the code is technically correct.

## 4.1 Business Problem vs Analytical Problem

A business problem describes an organisational challenge.

An analytical problem describes what we need to investigate using data.

### Example: Retail company

**Business problem:**

Monthly revenue has declined over the last quarter.

**Analytical questions:**

- Which product categories experienced the largest decline?
- Has the number of orders decreased?
- Has the average transaction value changed?
- Are certain customer groups purchasing less frequently?
- Is the decline concentrated in particular sales channels?

The analytical questions help identify the information and analysis required to investigate the business problem.

## 4.2 A Practical Problem Formulation Framework

Before starting an analysis, answer the following questions.

| Question | Explanation |
|---|---|
| Business Context | What does the organisation do? |
| Business Problem | What is going wrong or what opportunity exists? |
| Analytical Question | What do we need to investigate? |
| Required Data | What information is necessary? |
| Analytical Approach | How can we investigate the problem? |
| Success Measure | How will the organisation evaluate improvement? |

### Worked Example: Customer Retention

| Component | Example |
|---|---|
| Business Context | Online retail company |
| Business Problem | Customers are not making repeat purchases |
| Analytical Question | What characteristics are associated with repeat purchasing? |
| Required Data | Customer records, orders, dates and transaction amounts |
| Analytical Approach | Purchase frequency analysis and customer segmentation |
| Success Measure | Improvement in repeat-purchase rate |

The success measure should be agreed with the business. It should not be selected arbitrarily by the analyst.

## 4.3 Common Mistake: Starting with an Algorithm

Suppose management says:

"We need to implement a Random Forest model."

A Data Scientist should ask:

- What business problem will the model solve?
- What outcome are we trying to predict?
- Is historical data available?
- How will the predictions be used?
- What would make the model successful?

The choice of algorithm should follow the problem definition, not replace it.

---

# 5. Statistical Foundations

Statistics helps us understand data, summarise information and make informed conclusions.

In Data Science, statistics is essential because raw data alone does not explain what is happening.

Before analysing complex datasets, we must understand some fundamental statistical concepts.

## 5.1 Population and Sample

### Population

A population refers to the complete group of individuals or observations that we want to study.

**Example:**

An online retailer has 100,000 registered customers.

If the organisation wants to study all its registered customers, those 100,000 customers represent the population.

### Sample

A sample is a subset selected from the population for analysis.

If the retailer selects 2,000 customers for a customer satisfaction survey, those 2,000 customers represent the sample.

| Population | Sample |
|---|---|
| Entire group | Selected subset |
| Usually larger | Usually smaller |
| Represents the group of interest | Used to study the group |
| Example: All 100,000 customers | Example: 2,000 surveyed customers |

### Why do organisations use samples?

Studying an entire population may be:

- Expensive.
- Time-consuming.
- Operationally difficult.
- Unnecessary for some investigations.

A properly selected sample can provide useful information about a larger population.

### Important consideration

A sample should represent the population appropriately.

For example, surveying only premium customers may not provide a reliable picture of satisfaction across all customer groups.

This is an example of sampling bias.

## 5.2 Variables and Observations

### Variable

A variable is a characteristic or attribute that can take different values.

Examples:

- Customer age.
- Transaction amount.
- Product category.
- Payment method.
- Delivery status.

### Observation

An observation is an individual recorded instance in a dataset.

For example, one customer transaction may represent one observation in a transaction-level dataset.

Consider this illustrative table:

| Order ID | Customer Age | Order Amount | Category | Payment Status |
|---|---:|---:|---|---|
| 1001 | 25 | 1,500 | Electronics | Paid |
| 1002 | 32 | 2,200 | Clothing | Paid |
| 1003 | 28 | 900 | Grocery | Pending |
| 1004 | 41 | 3,500 | Electronics | Paid |

In this example:

- Each row represents an observation.
- Each column represents a variable.

The correct interpretation depends on the dataset's unit of analysis. A row could represent a customer, transaction, product or another entity.

## 5.3 Types of Data

Data can be classified into qualitative and quantitative categories.

### A. Qualitative Data

Qualitative data describes characteristics or categories.

It is generally non-numeric in meaning.

Examples:

- Gender category.
- Product category.
- Payment method.
- City.
- Order status.

Two common forms are:

**Nominal Data**

Categories without a natural order.

Examples:
- Hyderabad, Mumbai, Delhi.
- Cash, Card, UPI.
- Electronics, Clothing, Grocery.

**Ordinal Data**

Categories that have a meaningful order.

Examples:
- Low, Medium, High.
- Poor, Average, Good, Excellent.
- Bronze, Silver, Gold.

The order is meaningful, but the difference between categories is not necessarily equal.

### B. Quantitative Data

Quantitative data represents numerical quantities.

Examples:

- Revenue.
- Age.
- Number of orders.
- Delivery time.
- Product quantity.

Two common forms are:

**Discrete Data**

Values that are countable.

Examples:
- Number of customers.
- Number of orders.
- Number of products sold.

**Continuous Data**

Values that can take measurements across a range.

Examples:
- Delivery time.
- Weight.
- Temperature.
- Transaction amount, when recorded with decimal precision.

### Summary

| Data Type | Category | Example |
|---|---|---|
| Qualitative | Nominal | Payment Method |
| Qualitative | Ordinal | Satisfaction Level |
| Quantitative | Discrete | Number of Orders |
| Quantitative | Continuous | Delivery Time |

### Why does data type matter?

The type of data influences:

- Which statistical calculations are meaningful.
- Which charts are appropriate.
- How variables should be analysed.
- Which modelling techniques may be suitable later.

For example, calculating the average of payment-method labels does not make sense.

---

# 6. Descriptive Statistics

Descriptive statistics summarises and describes the important characteristics of a dataset.

Instead of examining every record individually, we can use statistical measures to understand the data more efficiently.

The key measures covered today are:

1. Mean.
2. Median.
3. Mode.
4. Minimum and maximum.
5. Range.
6. Variance.
7. Standard deviation.

## 6.1 Mean

The mean is the arithmetic average of a set of values.

Formula:

\[
\text{Mean}=\frac{\sum x_i}{n}
\]

Where:

- \(x_i\) represents each observation.
- \(n\) represents the number of observations.

### Example

Suppose a retail store records the following daily transaction amounts:

₹500, ₹700, ₹800, ₹1,000, ₹1,500

\[
\text{Mean}=\frac{500+700+800+1000+1500}{5}
\]

\[
\text{Mean}=\frac{4500}{5}=900
\]

The average transaction amount is ₹900.

### Business Interpretation

Management can use this measure to understand the average transaction value.

However, the mean can be affected by unusually high or low values.

Consider another set of transaction amounts:

₹500, ₹700, ₹800, ₹1,000, ₹10,000

The mean becomes:

\[
\text{Mean}=\frac{13000}{5}=2600
\]

The average has increased significantly because of one unusually large transaction.

This demonstrates why the mean should not be interpreted in isolation.

## 6.2 Median

The median is the middle value when observations are arranged in ascending or descending order.

### Odd number of observations

Values:

10, 20, 30, 40, 50

The middle value is 30.

Therefore:

\[
\text{Median}=30
\]

### Even number of observations

Values:

10, 20, 30, 40

The median is the average of the two middle values.

\[
\text{Median}=\frac{20+30}{2}=25
\]

### Business Interpretation

Median transaction value can be useful when a dataset contains unusually large transactions.

For example, if a few premium customers make very large purchases, the mean may give an exaggerated impression of typical customer spending.

The median may provide a more representative measure of the middle transaction.

## 6.3 Mode

The mode is the value that occurs most frequently.

Example:

10, 20, 20, 30, 40

\[
\text{Mode}=20
\]

### Business Interpretation

Mode is useful for identifying frequently occurring values or categories.

Examples:

- Most frequently purchased product category.
- Most common payment method.
- Most frequently selected delivery option.

A dataset can have more than one mode, or no unique mode.

## 6.4 Comparing Mean, Median and Mode

| Measure | Meaning | Business Application |
|---|---|---|
| Mean | Arithmetic average | Average sales or transaction value |
| Median | Middle value | Typical customer spending when extreme values exist |
| Mode | Most frequent value | Most popular product category or payment method |

**Important:** These measures answer different questions. No single measure is always the best choice.

## 6.5 Minimum and Maximum

Minimum is the smallest value in a dataset.

Maximum is the largest value.

Example:

Transaction amounts:

₹500, ₹700, ₹800, ₹1,000, ₹1,500

- Minimum = ₹500
- Maximum = ₹1,500

### Business Interpretation

These measures help identify the lower and upper boundaries of observed values.

For example, a delivery company may examine the minimum and maximum delivery times to understand the range of observed performance.

Extreme values should be investigated before conclusions are drawn.

## 6.6 Range

Range measures the difference between the maximum and minimum values.

Formula:

\[
\text{Range}=\text{Maximum}-\text{Minimum}
\]

Example:

Maximum = ₹1,500

Minimum = ₹500

\[
\text{Range}=1500-500=1000
\]

The range is ₹1,000.

### Business Interpretation

Range provides a simple indication of how far apart the smallest and largest observations are.

However, it uses only two observations and can be strongly influenced by extreme values.

## 6.7 Variance

Variance measures how far observations are spread around their mean.

A small variance indicates that values are relatively close to the mean.

A large variance indicates greater spread.

### Population Variance

\[
\sigma^2=\frac{\sum(x_i-\mu)^2}{N}
\]

Where:

- \(x_i\) represents each observation.
- \(\mu\) represents the population mean.
- \(N\) represents the population size.

### Sample Variance

\[
s^2=\frac{\sum(x_i-\bar{x})^2}{n-1}
\]

Where:

- \(\bar{x}\) represents the sample mean.
- \(n\) represents the sample size.

The sample formula uses \(n-1\) in the denominator. This is called Bessel's correction.

### Example

Consider two stores:

Store A daily sales:

₹900, ₹1,000, ₹1,100

Store B daily sales:

₹500, ₹1,000, ₹1,500

Both stores have the same mean:

₹1,000

However, Store B has greater variation in daily sales.

This means that the average alone does not describe the full behaviour of the data.

## 6.8 Standard Deviation

Standard deviation measures the typical spread of observations around the mean.

It is the square root of variance.

Population standard deviation:

\[
\sigma=\sqrt{\frac{\sum(x_i-\mu)^2}{N}}
\]

Sample standard deviation:

\[
s=\sqrt{\frac{\sum(x_i-\bar{x})^2}{n-1}}
\]

### Business Example

Imagine two retail branches with the same average daily sales.

| Store | Average Daily Sales | Standard Deviation |
|---|---:|---:|
| Store A | ₹1,00,000 | ₹5,000 |
| Store B | ₹1,00,000 | ₹30,000 |

Store A has more consistent daily sales.

Store B has greater variation.

Management may investigate whether Store B experiences:
- Irregular customer demand.
- Promotional sales spikes.
- Supply interruptions.
- Seasonal fluctuations.

A high standard deviation does not automatically indicate poor performance. It indicates greater variability that may require investigation.

---

# 7. Understanding Distributions

A distribution describes how values are spread across a dataset.

It helps us understand:

- Which values occur frequently.
- Whether values are concentrated in a particular range.
- Whether the data is symmetrical.
- Whether extreme values exist.
- Whether there are multiple groups or peaks.

## 7.1 Normal Distribution

A normal distribution is a symmetrical, bell-shaped distribution.

Its key characteristics include:

- The mean, median and mode are equal in an ideal normal distribution.
- Most observations are concentrated near the centre.
- Fewer observations occur towards the tails.

Illustrative example:

Customer delivery times may approximately follow a bell-shaped pattern in a suitably selected operational dataset.

However, actual business data does not always follow a normal distribution.

## 7.2 Right-Skewed Distribution

A right-skewed distribution has a longer tail towards larger values.

Example:

Customer transaction amounts.

Most customers may make small or moderate purchases, while a small number make very large purchases.

This can pull the mean above the median.

## 7.3 Left-Skewed Distribution

A left-skewed distribution has a longer tail towards smaller values.

Example:

If most customers have high satisfaction scores but a smaller group gives very low scores, the distribution may be left-skewed.

## 7.4 Why Distribution Matters

Consider two retail stores with the same average transaction amount.

Their transaction distributions may be very different.

- Store A may have most transactions close to the average.
- Store B may have many small transactions and a few very large transactions.

Management may need different strategies for these stores.

**Business takeaway:** Do not rely only on averages. Understand how the observations are distributed.

---

# 8. Understanding Correlation

Correlation measures the strength and direction of the relationship between two numerical variables.

It helps us understand whether two variables tend to move together.

## 8.1 Correlation Coefficient

The Pearson correlation coefficient is represented by \(r\).

Its value ranges from -1 to +1.

\[
-1 \leq r \leq +1
\]

| Correlation | General Interpretation |
|---|---|
| +1 | Perfect positive linear relationship |
| Close to +1 | Strong positive linear relationship |
| Close to 0 | Weak or no linear relationship |
| Close to -1 | Strong negative linear relationship |
| -1 | Perfect negative linear relationship |

These are general descriptions. There are no universal boundaries that classify every correlation as weak, moderate or strong.

## 8.2 Positive Correlation

When one variable increases, the other tends to increase.

Example:

Advertising expenditure and sales revenue may show a positive relationship.

However, correlation alone does not establish that advertising caused the increase in revenue.

## 8.3 Negative Correlation

When one variable increases, the other tends to decrease.

Example:

For some products, price and quantity demanded may show a negative relationship.

The actual relationship depends on market conditions and other influencing factors.

## 8.4 Zero or Weak Correlation

A correlation near zero indicates little or no linear relationship.

It does not necessarily mean that no relationship exists.

For example, two variables may have a nonlinear relationship that Pearson correlation does not capture effectively.

## 8.5 Correlation Does Not Mean Causation

This is one of the most important principles in Data Science.

Suppose ice cream sales and swimming-related accidents both increase during summer.

They may show positive correlation.

It would be incorrect to conclude that ice cream sales cause swimming accidents.

A third factor—hot weather and increased outdoor activity—may influence both.

This is called a confounding factor.

### Business Example

A company notices that customers who receive more promotional emails spend more money.

Does sending more emails cause customers to spend more?

Not necessarily.

Customers who are already highly engaged may receive or open more emails and also purchase more frequently.

To investigate causation, the organisation may need a properly designed experiment, such as an A/B test. This will be explored in Day 2.

---

# 9. Practical Implementation Using Python

This section demonstrates how to calculate descriptive statistics and examine relationships using Python.

The following is a small, illustrative retail dataset created for learning. It is not a claim about the exact structure or contents of the approved classroom CSV file.

## 9.1 Import Required Libraries

```python
# Import pandas for tabular data manipulation
import pandas as pd

# Import NumPy for numerical calculations
import numpy as np

# Import Matplotlib for visualisation
import matplotlib.pyplot as plt

# Import Seaborn for statistical visualisation
import seaborn as sns
```

## 9.2 Create an Illustrative Retail Dataset

```python
# Create a small retail transaction dataset.
# Each row represents one transaction.

retail_data = {
    "order_id": [1001, 1002, 1003, 1004, 1005,
                 1006, 1007, 1008, 1009, 1010],

    "customer_age": [25, 32, 28, 41, 35,
                     29, 45, 31, 27, 38],

    "order_amount": [500, 700, 800, 1000, 1500,
                     600, 2500, 900, 750, 1200],

    "product_category": [
        "Electronics", "Clothing", "Grocery",
        "Electronics", "Clothing", "Grocery",
        "Electronics", "Clothing", "Grocery",
        "Electronics"
    ],

    "payment_method": [
        "UPI", "Card", "UPI", "Card", "UPI",
        "Cash", "Card", "UPI", "Cash", "Card"
    ]
}

# Convert the dictionary into a pandas DataFrame
df = pd.DataFrame(retail_data)

# Display the first five records
df.head()
```

## 9.3 Understand the Dataset

```python
# Display the number of rows and columns
print("Dataset Shape:", df.shape)

# Display the column names
print("\nColumn Names:")
print(df.columns)

# Display data types
print("\nData Types:")
print(df.dtypes)

# Display general dataset information
print("\nDataset Information:")
df.info()
```

### Why is this important?

Before performing calculations, we need to understand what information is available.

We should know:

- How many records exist.
- What each column represents.
- Which columns are numerical.
- Which columns are categorical.
- Whether the data types are appropriate.

## 9.4 Calculate Mean, Median and Mode

```python
# Calculate the average transaction amount
mean_amount = df["order_amount"].mean()

# Calculate the middle transaction amount
median_amount = df["order_amount"].median()

# Identify the most frequently occurring transaction amount
mode_amount = df["order_amount"].mode()

print("Mean:", mean_amount)
print("Median:", median_amount)
print("Mode:")
print(mode_amount)
```

### Interpretation

The mean represents the average transaction amount.

The median represents the middle transaction amount.

The mode identifies the most frequently occurring transaction amount.

Compare these values to understand whether the transaction distribution may be influenced by unusually large or small purchases.

## 9.5 Calculate Minimum, Maximum and Range

```python
# Identify the smallest transaction
minimum_amount = df["order_amount"].min()

# Identify the largest transaction
maximum_amount = df["order_amount"].max()

# Calculate the difference between maximum and minimum
transaction_range = maximum_amount - minimum_amount

print("Minimum:", minimum_amount)
print("Maximum:", maximum_amount)
print("Range:", transaction_range)
```

## 9.6 Calculate Variance and Standard Deviation

```python
# Calculate sample variance
sample_variance = df["order_amount"].var()

# Calculate sample standard deviation
sample_std = df["order_amount"].std()

print("Sample Variance:", sample_variance)
print("Sample Standard Deviation:", sample_std)
```

By default, pandas uses sample variance and sample standard deviation (`ddof=1`).

If the dataset represents the complete population of interest, population measures can be calculated using `ddof=0`.

```python
# Population variance
population_variance = df["order_amount"].var(ddof=0)

# Population standard deviation
population_std = df["order_amount"].std(ddof=0)

print("Population Variance:", population_variance)
print("Population Standard Deviation:", population_std)
```

## 9.7 Generate a Statistical Summary

```python
# Generate descriptive statistics for numerical columns
summary = df.describe()

print(summary)
```

The `describe()` function provides:

| Measure | Meaning |
|---|---|
| count | Number of non-missing observations |
| mean | Arithmetic average |
| std | Standard deviation |
| min | Minimum value |
| 25% | First quartile |
| 50% | Median |
| 75% | Third quartile |
| max | Maximum value |

This is one of the most useful first steps when exploring a numerical dataset.

## 9.8 Understand Category Frequencies

```python
# Count the number of transactions in each product category
category_counts = df["product_category"].value_counts()

print(category_counts)
```

Business question:

Which product category has the highest number of transactions?

The result describes transaction frequency, not necessarily revenue or profitability.

To answer revenue-related questions, we would need to aggregate transaction amounts by category.

## 9.9 Visualise the Distribution

```python
# Create a histogram of transaction amounts

plt.figure(figsize=(8, 5))

sns.histplot(
    data=df,
    x="order_amount",
    bins=5,
    kde=True
)

plt.title("Distribution of Retail Transaction Amounts")
plt.xlabel("Transaction Amount")
plt.ylabel("Frequency")

plt.show()
```

A histogram helps us understand how numerical values are distributed.

Look for:
- Concentration of values.
- Spread.
- Possible skewness.
- Unusually large or small observations.

## 9.10 Identify Possible Outliers Using a Box Plot

```python
# Create a box plot for transaction amounts

plt.figure(figsize=(8, 4))

sns.boxplot(
    data=df,
    x="order_amount"
)

plt.title("Retail Transaction Amounts")
plt.xlabel("Transaction Amount")

plt.show()
```

A box plot displays:

- Median.
- First quartile.
- Third quartile.
- Interquartile range.
- Potential outliers.

A point identified as an outlier is not automatically an error. It may represent a legitimate high-value transaction.

## 9.11 Calculate Correlation

```python
# Calculate Pearson correlation between numerical columns

correlation_matrix = df[
    ["customer_age", "order_amount"]
].corr(method="pearson")

print(correlation_matrix)
```

The output displays the correlation between customer age and transaction amount.

For this small illustrative dataset, the result should not be treated as evidence of a general business relationship.

A meaningful investigation requires adequate data, appropriate variables and consideration of other influencing factors.

## 9.12 Visualise Correlation

```python
# Create a scatter plot to examine the relationship

plt.figure(figsize=(8, 5))

sns.scatterplot(
    data=df,
    x="customer_age",
    y="order_amount"
)

plt.title("Customer Age vs Transaction Amount")
plt.xlabel("Customer Age")
plt.ylabel("Transaction Amount")

plt.show()
```

A scatter plot helps us visually examine whether two numerical variables appear to move together.

---

# 10. Real-World Case Study: Retail Revenue Decline

## 10.1 Business Scenario

An online retail company has noticed that its monthly revenue has declined.

Management wants the Data Science team to investigate the situation.

The company has transaction information containing details such as customer purchases, order amounts, product categories and transaction dates.

The team is asked to identify possible reasons for the revenue decline.

## 10.2 Step 1: Define the Business Problem

**Business problem:**

Monthly revenue is declining, and management wants to understand the contributing factors.

## 10.3 Step 2: Formulate Analytical Questions

The team identifies the following questions:

1. Has the number of transactions decreased?
2. Has the average transaction amount changed?
3. Which product categories experienced a decline?
4. Are certain customer groups purchasing less frequently?
5. Is the decline concentrated in specific periods?

## 10.4 Step 3: Identify Required Data

Potentially useful information includes:

- Order identifier.
- Customer identifier.
- Transaction date.
- Transaction amount.
- Product category.
- Quantity.
- Sales channel.

The exact data requirements depend on the investigation.

## 10.5 Step 4: Select the Analytical Approach

The initial investigation may involve:

- Comparing revenue over time.
- Calculating mean and median transaction amounts.
- Examining transaction distributions.
- Comparing product-category performance.
- Identifying changes in transaction frequency.
- Examining relationships between relevant variables.

## 10.6 Step 5: Interpret Findings

Imagine that a properly conducted analysis produces the following illustrative findings:

| Observation | Possible Business Interpretation |
|---|---|
| Transaction count has declined | Fewer purchases are taking place |
| Average order value has remained stable | Revenue decline may be associated with lower transaction volume |
| One product category shows a substantial decline | Category-specific demand may need investigation |
| High-value purchases have become less frequent | Premium customer purchasing behaviour may have changed |

These are hypothetical examples, not findings from the actual classroom dataset.

## 10.7 Step 6: Communicate Business Recommendations

Depending on the validated findings, management might consider:

- Investigating changes in customer traffic.
- Reviewing product availability.
- Examining pricing and promotional strategies.
- Studying customer retention.
- Evaluating sales-channel performance.

The purpose of analysis is not simply to produce statistical output. It is to help management make better-informed decisions.

---

# 11. Common Mistakes and Best Practices

| Common Mistake | Why It Is a Problem | Better Practice |
|---|---|---|
| Starting with an algorithm | The actual business problem may be misunderstood | Define the problem first |
| Treating mean as the only measure | Extreme values can distort the average | Compare mean and median |
| Confusing population and sample | Can lead to incorrect statistical interpretation | Identify the group being studied |
| Treating correlation as causation | A relationship does not establish cause and effect | Investigate other factors and use appropriate study designs |
| Ignoring data types | Some calculations may be inappropriate | Understand each variable |
| Ignoring outliers | Important observations may be missed | Investigate unusual values |
| Reporting numbers without context | Management may not understand their significance | Explain business implications |

---

# 12. Hands-On Exercise and Challenge

## Assignment: Retail Business Problem Investigation

### Business Scenario

You are working as a junior Data Analyst for an online retail company.

Management wants to understand customer purchasing behaviour and identify possible areas for business improvement.

You have been provided with a retail transaction dataset.

### Tasks

**Part A – Understand the Business Problem**

1. Write a short description of the business problem.
2. Identify three analytical questions.
3. Explain what decisions management may need to make.

**Part B – Understand the Dataset**

4. Identify the observations and variables.
5. Classify the available variables as qualitative or quantitative.
6. Identify which numerical variables are discrete or continuous, where appropriate.

**Part C – Statistical Exploration**

7. Calculate mean transaction amount.
8. Calculate median transaction amount.
9. Identify the mode where meaningful.
10. Calculate minimum, maximum and range.
11. Calculate variance and standard deviation.
12. Generate a descriptive statistical summary.

**Part D – Interpretation**

13. Identify two or three observations from the data.
14. Explain whether the mean and median provide similar information.
15. Identify any unusual values that require investigation.
16. Explain how the observations could support business decisions.

### Expected Output

Each student or group should produce:

- A written business problem statement.
- A list of relevant analytical questions.
- A classification of important variables.
- A statistical summary.
- Two or three meaningful observations.
- A short business interpretation.

### Hint / Starter Framework

```python
# Load the supplied classroom dataset
import pandas as pd
import numpy as np

# Replace the path with the actual dataset location
df = pd.read_csv("synthetic_retail.csv")

# Understand the dataset
print(df.head())
print(df.shape)
print(df.info())

# Generate a descriptive summary
print(df.describe())

# Continue with the relevant numerical and categorical columns.
# Check the actual column names before performing calculations.
```

Do not assume that the actual CSV uses the illustrative column names from the earlier examples. Inspect its schema first.

---

# 13. Knowledge Check

Attempt these questions before referring to the answers.

### Question 1

What is the primary objective of Data Science?

A. To create spreadsheets  
B. To write Python programs  
C. To extract useful insights and support decisions using data  
D. To create charts only  

### Question 2

Which stage should generally come first in the Data Science lifecycle?

A. Model deployment  
B. Business problem understanding  
C. Algorithm selection  
D. Visualisation  

### Question 3

An organisation has 50,000 customers and surveys 1,000 of them. What do the 1,000 surveyed customers represent?

A. Population  
B. Sample  
C. Variable  
D. Observation  

### Question 4

Which measure is generally less affected by extreme values?

A. Mean  
B. Median  
C. Range  
D. Maximum  

### Question 5

Which measure identifies the most frequently occurring value?

A. Mean  
B. Median  
C. Mode  
D. Variance  

### Question 6

What does standard deviation measure?

A. The total number of observations  
B. The spread of values around the mean  
C. The largest value  
D. The most frequently occurring value  

### Question 7

A correlation coefficient of +0.90 generally indicates:

A. Strong positive linear relationship  
B. Strong negative linear relationship  
C. No linear relationship  
D. Perfect negative relationship  

### Question 8

Does correlation always establish causation?

A. Yes  
B. No  

### Question 9

Which of the following is ordinal data?

A. Payment method  
B. Customer city  
C. Satisfaction level: Poor, Average, Good  
D. Customer identifier  

### Question 10

A company wants to predict which customers may stop purchasing. Which discipline is most directly associated with developing such a predictive solution?

A. Traditional reporting only  
B. Data Science  
C. Data entry  
D. Spreadsheet formatting  

## 13.1 Answers for Self-Evaluation

| Question | Correct Answer | Explanation |
|---|---|---|
| 1 | C | Data Science extracts useful insights and supports decisions |
| 2 | B | The business problem should be understood before selecting techniques |
| 3 | B | The 1,000 surveyed customers are a subset of the population |
| 4 | B | Median is generally less sensitive to extreme observations |
| 5 | C | Mode represents the most frequently occurring value |
| 6 | B | Standard deviation measures spread around the mean |
| 7 | A | +0.90 indicates a strong positive linear relationship |
| 8 | B | Correlation alone does not establish causation |
| 9 | C | Satisfaction levels have a meaningful order |
| 10 | B | Predictive modelling is a common Data Science application |

---

# 14. Key Takeaways

By completing Day 1, you should understand the following:

1. Data Science begins with a business problem, not an algorithm.
2. The Data Science lifecycle provides a structured approach to solving data-driven problems.
3. Population and sample describe the groups being studied.
4. Variables represent the characteristics recorded in a dataset.
5. Data types influence how information can be analysed.
6. Mean, median and mode describe central tendency.
7. Variance and standard deviation describe variability.
8. Distributions help explain how observations are spread.
9. Correlation measures the direction and strength of a linear relationship.
10. Correlation does not automatically imply causation.
11. Statistical results must be interpreted in a business context.

---

# 15. Homework Assignment

## Topic: Identify a Business Problem for Data Science

Select an industry of your choice:

- Retail.
- Banking.
- Telecommunications.
- Healthcare.
- E-commerce.
- Manufacturing.
- Logistics.
- Education.

Identify one real-world business problem that could potentially be investigated using data.

Prepare a short submission containing:

1. **Business Problem:** What issue is the organisation facing?
2. **Business Importance:** Why does the problem matter?
3. **Required Data:** What information would be required?
4. **Analytical Approach:** How could the data be investigated?
5. **Success Measure:** How would the organisation know whether the problem has improved?

**Important:** You are not expected to build a machine learning model for this assignment. Focus on understanding the problem and identifying how data could help.

---

# 16. Looking Ahead – Day 2

## Experimental Design and A/B Testing

On Day 1, we learned how to understand business problems and investigate data.

However, identifying a relationship or observing a change does not always tell us what caused it.

On Day 2, we will explore how organisations use controlled experiments to evaluate business decisions.

For example:

An e-commerce company changes the colour and placement of its checkout button.

Management wants to know whether the new design increases completed purchases.

Instead of relying on assumptions, the company can conduct an A/B test.

We will learn how controlled experiments help organisations compare alternatives and make evidence-based decisions.

**End of Day 1 – Data Science Foundations**
