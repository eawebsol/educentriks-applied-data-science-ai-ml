# Day 3: ML Pipeline and Bias–Variance

**Programme:** Educentriks – Applied Data Science, AI/ML & Generative AI  
**Module:** Foundations  
**Session Duration:** 90 minutes  
**Primary Technology:** Python 3.13, Jupyter Notebook, pandas, NumPy and scikit-learn  
**Practical Dataset:** TabReD – Delivery ETA

---

## 1. Day Overview & Objectives

### Learning Objectives

By the end of this session, you should be able to:

1. Explain the stages of a basic machine-learning workflow.
2. Understand why data must be divided into training and testing sets.
3. Explain overfitting, underfitting, bias and variance.
4. Recognise data leakage and understand why a model must be evaluated on unseen data.

### Prerequisites

Students should have a basic understanding of:

- Python variables, functions and libraries.
- pandas DataFrames and NumPy arrays.
- Basic descriptive statistics.
- The concepts of independent and dependent variables.
- The A/B testing concepts covered in Day 2.

### What We Will Build

We will examine a basic machine-learning workflow using a delivery ETA prediction scenario.

The objective is not to develop an advanced prediction model today. Instead, we will understand how data moves through a machine-learning process and why reliable evaluation is essential before a model is used in a business environment.

---

## 2. Conceptual Deep Dive

### 2.1 What Is a Machine-Learning Workflow?

A machine-learning workflow is a structured sequence of activities through which data is prepared, used to train a model and evaluated to determine whether the model can make reliable predictions.

Think of it as training a new employee.

- First, the employee receives information and instructions.
- Next, the employee practises using examples.
- Finally, the employee is given unfamiliar situations to determine whether the learning can be applied independently.

Machine learning follows a similar approach.

**A basic machine-learning workflow:**

```text
Business Problem
       |
       v
Data Collection
       |
       v
Data Preparation
       |
       v
Feature and Target Selection
       |
       v
Train-Test Split
       |
       v
Model Training
       |
       v
Model Evaluation
       |
       v
Business Interpretation
```

Each stage has a specific purpose.

| Stage | Purpose | Business Example |
|---|---|---|
| Business problem | Define what needs to be predicted | Estimate delivery time |
| Data collection | Obtain relevant historical information | Previous delivery records |
| Data preparation | Prepare usable data | Handle missing or invalid values |
| Feature selection | Identify useful input variables | Distance, order characteristics |
| Target selection | Identify the value to predict | Delivery ETA |
| Train-test split | Separate learning and evaluation data | Historical records divided into two sets |
| Model training | Allow the algorithm to learn patterns | Learn relationships between delivery information and ETA |
| Evaluation | Measure model performance | Calculate prediction error |
| Interpretation | Assess business usefulness | Determine whether predictions are reliable enough for operations |

**Business importance:** A model is not successful merely because it produces predictions. It must produce predictions that are sufficiently reliable for the business decision it supports.

### 2.2 Understanding Features and Target

A machine-learning dataset generally contains two important components: features and a target.

**Features (X)** are the input variables supplied to a model.

**Target (y)** is the outcome the model is expected to predict.

Consider a delivery prediction scenario.

| Distance | Order Size | Traffic Level | Delivery Time |
|---:|---:|---|---:|
| 5 km | Small | Low | 25 min |
| 12 km | Medium | High | 65 min |
| 8 km | Large | Medium | 48 min |
| 20 km | Medium | High | 105 min |

In this simplified illustration:

- Distance, order size and traffic level are features.
- Delivery time is the target.

The model attempts to learn patterns connecting the input information to the outcome.

**Important distinction:**

- X represents the information used to make a prediction.
- y represents the value the model is learning to predict.

A feature must be available at the time the prediction is made. Information that becomes available only after delivery cannot legitimately be used to predict the original ETA.

### 2.3 Why Do We Split Data?

One of the most important principles in machine learning is that a model must be evaluated using data it has not trained on.

Imagine a student who memorises the answers to a set of practice questions.

The student may score perfectly on those same questions. However, this does not establish that the student understands the subject or can solve unfamiliar problems.

A machine-learning model can behave similarly.

If we evaluate a model using only the records it has already seen, we may get an overly optimistic impression of its performance.

We therefore divide the available data into separate portions.

| Dataset | Purpose |
|---|---|
| Training data | Used to learn patterns and model parameters |
| Testing data | Used to evaluate performance on unseen observations |

A common introductory split is:

- 80% training data
- 20% testing data

This is an example, not a mandatory ratio for every project. The appropriate split depends on the dataset, the problem and the evaluation design.

**Why this matters in business**

A delivery prediction model might perform very well on historical records but produce inaccurate estimates for new deliveries.

If a logistics company uses unreliable predictions, it could:

- Promise unrealistic delivery times.
- Allocate delivery personnel inefficiently.
- Increase customer complaints.
- Damage customer confidence.

The testing dataset helps us assess whether the model's performance extends beyond the data used for training.

### 2.4 Understanding Model Generalisation

Generalisation is the ability of a machine-learning model to perform reasonably well on new, unseen data.

A model that memorises its training examples but fails on new observations has poor generalisation.

A useful model should learn meaningful patterns rather than simply memorise the historical records.

| Training Performance | Testing Performance | Possible Interpretation |
|---|---|---|
| Good | Good | Model may generalise reasonably well |
| Very good | Poor | Possible overfitting |
| Poor | Poor | Possible underfitting |
| Poor | Good | Investigate the split, sample size and evaluation reliability |

These patterns are diagnostic clues, not automatic proof of a particular problem.

### 2.5 What Is Overfitting?

Overfitting occurs when a model learns the training data too closely, including random variation or noise that does not represent a stable business pattern.

**Analogy:**

A student memorises every answer in a textbook but struggles when the examination contains different questions testing the same concepts.

Similarly, an overfitted model may perform extremely well on training data but poorly on unseen data.

**Example: Delivery ETA**

Suppose a model learns very specific patterns from historical deliveries.

It may perform well on the training records but struggle when:

- A new delivery route is introduced.
- Traffic conditions change.
- New combinations of delivery characteristics appear.

The model may have learned details that do not generalise.

**Common signs:**

- Training error is very low.
- Testing error is substantially higher.
- Performance changes significantly when evaluated on new data.

### 2.6 What Is Underfitting?

Underfitting occurs when a model is too simple or has not learned enough from the available data to capture important patterns.

**Analogy:**

A student reads only the chapter headings and expects to answer detailed examination questions.

The preparation is insufficient to understand the subject.

**Example: Delivery ETA**

Suppose delivery time depends on several factors, but a model uses only one simplistic relationship.

It may fail to capture important variation in delivery times.

**Common signs:**

- Training performance is poor.
- Testing performance is also poor.
- Important patterns are not captured.

### 2.7 Understanding Bias and Variance

Bias and variance help explain why models can perform poorly.

**Bias** refers to error associated with overly simplistic assumptions made by a model.

**Variance** refers to how sensitive a model's learned behaviour is to changes in the training data.

A useful conceptual comparison:

| Concept | Meaning | Typical Problem |
|---|---|---|
| High Bias | Model is too simple to capture important patterns | Underfitting |
| High Variance | Model is overly sensitive to the training data | Overfitting |
| Better Balance | Model captures useful patterns without excessive sensitivity | Better potential generalisation |

Think of the relationship this way:

- High bias: the model consistently misses important patterns.
- High variance: the model changes too much depending on the training examples.
- Good balance: the model learns useful patterns that remain reasonably stable.

**Business importance:** A model that performs well only under one historical dataset may not be dependable when business conditions change.

### 2.8 What Is Data Leakage?

Data leakage occurs when information that should not be available to the model during training or prediction improperly influences the learning process.

It can make a model appear more accurate than it really is.

**Example: Delivery ETA**

Imagine predicting delivery time using a column that records the actual delivery completion timestamp.

The actual completion time is only known after delivery. Using it to predict the delivery time would provide information that is unavailable when the prediction is needed.

This is a form of target leakage.

Other possible sources of leakage include:

- Using information collected after the prediction point.
- Allowing duplicated or related observations to appear in both training and testing sets when they should be kept together.
- Performing preprocessing using the complete dataset before splitting when the transformation learns information from the data.

**Best practice:** Split the data first. Fit data-dependent preprocessing steps using training data only, then apply the fitted transformations to testing data.

---

## 3. Practical Implementation & Code

### 3.1 Practical Scenario: Delivery ETA Prediction

A logistics company wants to estimate delivery time using historical delivery information.

The approved TabReD Delivery ETA dataset is part of this course's dataset collection.

The earlier inspection report recorded:

| Attribute | Inspected Finding |
|---|---:|
| Records | 416,451 |
| Numerical features | 221 |
| Categorical features | 1 |
| Binary features | 1 |
| Target file | `y.npy` |
| Task | Regression |
| Evaluation metric | RMSE |

The dataset contains separate feature groups:

- `x_num`: numerical features
- `x_cat`: categorical feature data
- `x_bin`: binary feature data
- `y.npy`: target values

The actual feature names, target interpretation and feature-file loading procedure must follow the dataset's accompanying metadata and inspection report. Do not assume that the target is expressed directly in minutes.

### 3.2 Understanding the Training and Testing Process

Before fitting a model, we need to understand how the data is divided.

The following example uses a prepared feature matrix `X` and target array `y`. It demonstrates the split operation independently of the dataset-specific loading process.

```python
# Import the required function
from sklearn.model_selection import train_test_split

# X contains prepared input features
# y contains the target values

# Divide the dataset into training and testing portions
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)

# Display the resulting dataset sizes
print("Training records:", len(X_train))
print("Testing records:", len(X_test))
```

**Understanding the code**

| Code | Explanation |
|---|---|
| `train_test_split()` | Divides the dataset into separate portions |
| `test_size=0.20` | Allocates 20% to testing |
| `random_state=42` | Makes the random split reproducible |
| `X_train` | Features used during training |
| `X_test` | Features reserved for evaluation |
| `y_train` | Training target values |
| `y_test` | Actual target values for testing |

For a random 80:20 split of 416,451 observations, the expected sizes are:

| Portion | Records |
|---|---:|
| Training | 333,160 |
| Testing | 83,291 |
| Total | 416,451 |

This is an illustrative split of the complete record count. It is not a claim that this replaces TabReD's supplied train, validation and test partitions.

### 3.3 Establishing a Baseline Model

Before evaluating a more sophisticated model, analysts should establish a simple baseline.

A baseline helps answer an important question:

**Does the model provide useful predictive value beyond a simple reference prediction?**

For a regression problem, a mean-based baseline predicts the average target value observed in the training data.

```python
# Import baseline model and evaluation metric
from sklearn.dummy import DummyRegressor
from sklearn.metrics import root_mean_squared_error

# Create a simple baseline model
baseline_model = DummyRegressor(strategy="mean")

# Train the baseline using training data only
baseline_model.fit(X_train, y_train)

# Generate predictions for training and testing data
train_predictions = baseline_model.predict(X_train)
test_predictions = baseline_model.predict(X_test)

# Calculate RMSE
train_rmse = root_mean_squared_error(
    y_train,
    train_predictions
)

test_rmse = root_mean_squared_error(
    y_test,
    test_predictions
)

# Display the results
print("Training RMSE:", train_rmse)
print("Testing RMSE:", test_rmse)
```

**Understanding RMSE**

RMSE stands for Root Mean Squared Error.

It measures the typical magnitude of prediction errors, with larger errors receiving greater weight.

\[
RMSE = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2}
\]

Where:

- \(y_i\) = actual value
- \(\hat{y}_i\) = predicted value
- \(n\) = number of observations

A lower RMSE generally indicates better prediction accuracy when comparing models on the same target scale and evaluation dataset.

**Important:** RMSE is expressed in the same units as the target. If the target is transformed, the resulting RMSE is also on that transformed scale.

The baseline is a reference point, not a production-ready delivery prediction solution.

### 3.4 Comparing Training and Testing Performance

The next step is to compare the two results.

| Observation | Possible Explanation |
|---|---|
| Training and testing RMSE are both high | The baseline may not capture useful predictive relationships |
| Training and testing RMSE are similar | The model behaves consistently, but may still have weak predictive value |
| Training RMSE is much lower than testing RMSE | A gap exists; investigate model complexity and evaluation design |

A mean-based DummyRegressor does not learn complex feature relationships. Therefore, it is useful as a baseline but cannot demonstrate all forms of overfitting and underfitting.

In later sessions, we will compare actual predictive algorithms.

### 3.5 Important Implementation Notes

Before using TabReD in the complete instructor notebook:

1. Confirm the feature arrays have compatible row counts.
2. Confirm the exact feature-file paths and array dimensions.
3. Confirm how the categorical feature should be represented.
4. Confirm the supplied dataset partitions and their intended use.
5. Confirm whether the target is transformed and how predictions should be interpreted.

The code above assumes that `X` and `y` have already been prepared correctly. It is a workflow demonstration, not a complete TabReD loader.

**Professional best practices**

- Never evaluate a model only on training data.
- Keep testing data separate until evaluation.
- Fit preprocessing transformations on training data only.
- Do not use information that would be unavailable at prediction time.
- Use reproducible random seeds where appropriate.
- Compare against a simple baseline.
- Interpret evaluation metrics in the context of the business problem.

---

## 4. Real-World Case Study: Delivery ETA Prediction

### Business Background

A logistics company handles thousands of deliveries every day.

Customers want realistic delivery estimates, while operations managers need accurate information to plan routes and allocate delivery resources.

The company decides to use historical delivery information to develop a machine-learning model.

### The Problem

The initial model appears to perform extremely well on historical training data.

However, when the company evaluates it on unseen records, prediction errors are considerably higher.

### What Could Have Gone Wrong?

The analytics team investigates four possible issues:

**1. Overfitting**

The model may have learned specific patterns from historical records instead of general delivery behaviour.

**2. Underfitting**

The model may be too simple to represent important relationships in delivery data.

**3. Data leakage**

The training process may have used information that would not be available when making a real-time prediction.

**4. Poor evaluation design**

The training and testing records may not represent the intended real-world prediction scenario.

### Business Consequences

Unreliable ETA predictions can result in:

- Increased customer complaints.
- Inefficient delivery planning.
- Poor resource allocation.
- Missed service-level commitments.
- Reduced customer confidence.

### Recommended Approach

The analytics team should:

1. Verify the data and target definitions.
2. Check that features are available at prediction time.
3. Use an appropriate training and evaluation split.
4. Establish a baseline.
5. Compare training and testing performance.
6. Investigate suspiciously large performance differences.
7. Assess the model against business requirements before deployment.

**Key lesson:** A model should be evaluated on its ability to handle unseen business situations, not simply on how accurately it reproduces its training data.

---

## 5. Hands-On Exercise & Challenge

### Assignment Title: Evaluate a Basic Machine-Learning Workflow

**Scenario**

You are working as a junior data analyst in a logistics company.

Your manager wants you to understand whether a machine-learning workflow is being evaluated correctly before the company considers using it for delivery ETA prediction.

### Tasks

1. Identify the features and target in the prepared dataset.
2. Explain why the dataset must be divided into training and testing portions.
3. Create a training/testing split using scikit-learn.
4. Train a simple baseline regression model.
5. Calculate training and testing RMSE.
6. Compare the two results.
7. Explain what the results suggest about model performance.
8. Identify at least two possible sources of data leakage in a delivery prediction scenario.

### Expected Output

Submit a Jupyter Notebook containing:

- Dataset and feature/target identification.
- Training and testing split.
- Baseline model implementation.
- Training and testing RMSE.
- A comparison of both results.
- A short written business interpretation.

### Hint / Starter Framework

```python
# Step 1: Import the required libraries

# Step 2: Confirm the prepared feature matrix and target

# Step 3: Split the data

# Step 4: Create a baseline regression model

# Step 5: Train the model

# Step 6: Generate predictions

# Step 7: Calculate RMSE

# Step 8: Compare the results

# Step 9: Write your business interpretation
```

### Business Interpretation Challenge

Imagine that the training RMSE is significantly lower than the testing RMSE.

Write a short explanation addressing:

- What could this difference indicate?
- Why should the company investigate it?
- What could happen if the model is deployed without further evaluation?

---

## 6. Knowledge Check

Try answering these questions before referring to the explanations.

### Questions

**1. What is the difference between training and testing data?**

**2. Why can a machine-learning model perform well on training data but poorly on unseen data?**

**3. What is the difference between bias and variance?**

**4. What is data leakage? Give one delivery prediction example.**

**5. Why is generalisation important in a production environment?**

### Self-Evaluation Answers

**1.** Training data is used to learn model parameters. Testing data is kept separate to evaluate how the trained model performs on unseen observations.

**2.** The model may have overfitted the training data, learning noise or overly specific patterns that do not generalise.

**3.** Bias is associated with overly simplistic model assumptions. Variance describes how sensitive model behaviour is to changes in the training data.

**4.** Data leakage occurs when information that should not be available during training or prediction improperly influences the model. For example, using the actual delivery completion timestamp to predict delivery time.

**5.** A production model receives new data. Generalisation helps determine whether the model can make useful predictions beyond the historical records used during training.

---

## Key Takeaways

By completing Day 3, you should understand that:

- Machine learning follows a structured workflow.
- Features are the inputs and the target is the value being predicted.
- Training and testing data serve different purposes.
- A model must be evaluated on unseen observations.
- Overfitting and underfitting can reduce predictive reliability.
- Bias and variance help explain model behaviour.
- Data leakage can create misleading evaluation results.
- A baseline provides a useful starting point for model comparison.

**Next Session – Day 4:** Regression Analysis and Predictive Modelling.

We will move from understanding the machine-learning workflow to exploring how regression models learn relationships between variables and make numerical predictions.
