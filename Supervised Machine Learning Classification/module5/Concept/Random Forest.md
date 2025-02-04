# Random Forest

## Introduction
Random Forest is an ensemble learning method that combines multiple decision trees to improve prediction accuracy and reduce overfitting. It is used for both classification and regression tasks.

## Concept
Random Forest builds multiple decision trees and aggregates their results to produce a final prediction. Each tree is trained on a random subset of the data using a technique called **bootstrap sampling**, and each split in a tree considers a random subset of features.

### Steps in Random Forest
1. **Bootstrap Sampling**: Randomly select samples from the dataset with replacement to create multiple training sets.
2. **Feature Subsampling**: At each split in a tree, a random subset of features is considered.
3. **Train Multiple Decision Trees**: Each tree is trained independently on a different subset of data.
4. **Aggregate Predictions**:
   - **For classification**: Use majority voting among all trees.
   - **For regression**: Use the average of all tree predictions.

## Mathematical Formulation
Given a dataset with features \( X \) and target values \( y \), the Random Forest model consists of \( T \) decision trees:

\[
F(X) = \frac{1}{T} \sum_{t=1}^{T} h_t(X)
\]

where \( h_t(X) \) is the prediction from the \( t \)-th decision tree.

For classification, the final prediction is determined by majority voting:

\[
F(X) = \arg\max_{c} \sum_{t=1}^{T} I(h_t(X) = c)
\]

where \( I(\cdot) \) is an indicator function that counts the votes for class \( c \).

For regression, the final prediction is the average of all tree predictions:

\[
F(X) = \frac{1}{T} \sum_{t=1}^{T} h_t(X)
\]

## Advantages
- Reduces overfitting compared to individual decision trees
- Handles high-dimensional data well
- Works for both classification and regression
- Robust to noisy data

## Disadvantages
- Computationally expensive
- Less interpretable compared to a single decision tree
- Can be biased if data is imbalanced

## Conclusion
Random Forest is a powerful and widely used ensemble method that leverages multiple decision trees to improve predictive accuracy and robustness. By combining multiple models, it mitigates overfitting and enhances generalization.