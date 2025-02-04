# k-Nearest Neighbors

## Introduction
k-Nearest Neighbors (k-NN) is a simple, non-parametric, and lazy learning algorithm used for classification and regression tasks. It relies on the idea that similar data points exist in close proximity to each other.

## Concept
The k-NN algorithm classifies a given data point based on the majority class of its **k** nearest neighbors. The closeness of neighbors is determined by a distance metric, such as **Euclidean distance**.

### Steps of k-NN:
1. Choose the number of neighbors, **k**.
2. Compute the distance between the new data point and all existing points.
3. Select the **k** nearest neighbors.
4. Assign the class based on a majority vote (for classification) or compute the average (for regression).

## Mathematical Formulation

### 1. Distance Metrics
The choice of distance metric affects the performance of k-NN. Some commonly used metrics include:

- **Euclidean Distance**:
  \[
  d(x, y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}
  \]

- **Manhattan Distance**:
  \[
  d(x, y) = \sum_{i=1}^{n} |x_i - y_i|
  \]

- **Minkowski Distance** (Generalized form):
  \[
  d(x, y) = \left( \sum_{i=1}^{n} |x_i - y_i|^p \right)^{1/p}
  \]
  where \( p = 1 \) (Manhattan) and \( p = 2 \) (Euclidean).

### 2. Classification
For a classification problem, the predicted class \( C(x) \) is determined by the majority class among its **k** nearest neighbors:
  \[
  C(x) = \arg\max_{c} \sum_{i \in k-NN} I(y_i = c)
  \]
where \( I(y_i = c) \) is an indicator function that counts votes for class \( c \).

### 3. Regression
For regression tasks, the output is computed as the mean (or weighted mean) of the **k** nearest neighbors' values:
  \[
  f(x) = \frac{1}{k} \sum_{i \in k-NN} y_i
  \]

## Choosing the Value of k
- A **small k** may lead to a noisy decision boundary and overfitting.
- A **large k** smoothens the decision boundary but may ignore local structures.
- A common approach is to use cross-validation to find the optimal **k**.

## Conclusion
k-NN is a simple yet powerful algorithm that works well for small datasets. However, its performance decreases with high-dimensional data and large datasets due to its computational cost.

---
