# Decision Tree

## Introduction
A Decision Tree is a supervised learning algorithm used for both classification and regression tasks. It models decisions using a tree-like structure, where each node represents a decision based on feature values.

## Concept
A Decision Tree splits data into subsets based on feature values, aiming to maximize information gain or minimize impurity at each step. The process continues recursively until reaching a stopping criterion, such as a maximum depth or minimum number of samples per leaf.

### Steps in Decision Tree Construction
1. **Select the Best Feature**: Choose the feature that best splits the data based on a chosen criterion (e.g., Gini impurity, entropy, or variance reduction).
2. **Split the Data**: Partition the dataset into subsets according to the selected feature’s values.
3. **Recursively Build Subtrees**: Repeat steps 1 and 2 until a stopping condition is met.
4. **Assign Class Labels (for Classification)** or **Predict Values (for Regression)** at leaf nodes.

## Mathematical Formulation
For classification tasks, common impurity measures include:

### 1. Gini Impurity
The Gini impurity for a node is defined as:
\[
G = 1 - \sum_{i=1}^{C} p_i^2
\]
where \( p_i \) is the probability of class \( i \) in the node, and \( C \) is the total number of classes.

### 2. Entropy
Entropy measures information gain and is given by:
\[
H = - \sum_{i=1}^{C} p_i \log_2 p_i
\]
A lower entropy indicates a purer node.

For regression tasks, Decision Trees minimize variance:

\[
Var = \frac{1}{n} \sum_{i=1}^{n} (y_i - \bar{y})^2
\]
where \( y_i \) are the target values and \( \bar{y} \) is the mean of the values in the node.

## Advantages
- Easy to interpret and visualize
- Requires little data preprocessing
- Can handle both numerical and categorical data
- Non-parametric, making no assumptions about data distribution

## Disadvantages
- Prone to overfitting
- Sensitive to noisy data
- Can be biased toward dominant classes in imbalanced datasets

## Conclusion
Decision Trees are powerful and interpretable models for classification and regression tasks. They form the basis of ensemble methods like Random Forest and Gradient Boosting, which mitigate individual tree weaknesses while improving predictive performance.
