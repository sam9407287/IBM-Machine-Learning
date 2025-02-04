# Logistic Regression

## Overview
Logistic Regression is a statistical method used for classification tasks, particularly binary classification. Despite its name, it is not a regression algorithm but a classification algorithm. It models the probability of an event occurring by transforming the output of a linear regression model using the logistic function (also known as the sigmoid function).

---

## Derivation from Linear Regression

### Linear Regression Recap
In linear regression, the relationship between the dependent variable \( y \) and the independent variables \( X \) is modeled as:

\[
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n + \epsilon
\]

Here, \( y \) is a continuous variable, and the goal is to predict its value based on the input features.

### Problem with Linear Regression for Classification
For classification tasks, \( y \) is a categorical variable (e.g., 0 or 1 for binary classification). Directly applying linear regression to predict \( y \) is problematic because:
1. The output of linear regression can range from \(-\infty\) to \(+\infty\), while probabilities must lie between 0 and 1.
2. Linear regression does not guarantee that the predicted values will be interpretable as probabilities.

### Introducing the Logistic Function
To address these issues, logistic regression applies the **logistic function** (sigmoid function) to the output of linear regression. The logistic function is defined as:

\[
\sigma(z) = \frac{1}{1 + e^{-z}}
\]

Here, \( z \) is the linear combination of the input features:

\[
z = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n
\]

The logistic function maps \( z \) to a value between 0 and 1, which can be interpreted as the probability of the positive class:

\[
P(y = 1 | X) = \sigma(z) = \frac{1}{1 + e^{-z}}
\]

---

## Concept of Odds

### Odds and Log-Odds
In logistic regression, the relationship between the probability \( P(y = 1 | X) \) and the input features is expressed in terms of **odds**. The odds of an event are defined as the ratio of the probability of the event occurring to the probability of it not occurring:

\[
\text{Odds} = \frac{P(y = 1 | X)}{1 - P(y = 1 | X)}
\]

Taking the natural logarithm of the odds gives the **log-odds** (also called the logit function):

\[
\log(\text{Odds}) = \log\left(\frac{P(y = 1 | X)}{1 - P(y = 1 | X)}\right) = z = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n
\]

This equation shows that the log-odds are a linear combination of the input features. This is why logistic regression is considered a **generalized linear model (GLM)**.

### Interpretation of Coefficients
The coefficients \( \beta_1, \beta_2, \dots, \beta_n \) in logistic regression represent the change in the log-odds of the outcome for a one-unit increase in the corresponding feature, holding all other features constant.

---

## Extending Binary Classification to Multiclass Classification

### Limitations of Binary Logistic Regression
Binary logistic regression is designed for problems with two classes (e.g., 0 and 1). However, many real-world problems involve more than two classes. To handle multiclass classification, logistic regression can be extended using the following approaches:

### 1. One-vs-Rest (OvR) Strategy
- Train \( K \) separate binary logistic regression models, where \( K \) is the number of classes.
- For each model, one class is treated as the positive class, and all other classes are treated as the negative class.
- During prediction, the class with the highest predicted probability is selected.

### 2. Multinomial Logistic Regression (Softmax Regression)
- A single model is trained to predict the probabilities of all \( K \) classes simultaneously.
- The softmax function is used instead of the sigmoid function to normalize the outputs into probabilities:

\[
P(y = k | X) = \frac{e^{z_k}}{\sum_{j=1}^K e^{z_j}}
\]

Here, \( z_k \) is the linear combination of features for class \( k \), and the denominator ensures that the probabilities sum to 1.

---

## Summary
- Logistic regression extends linear regression by applying the logistic function to model probabilities.
- The concept of odds and log-odds provides a way to interpret the relationship between features and the probability of an event.
- Binary logistic regression can be extended to multiclass classification using strategies like One-vs-Rest or Multinomial Logistic Regression.

Logistic regression is a powerful and interpretable method for classification tasks, widely used in fields such as medicine, finance, and social sciences.