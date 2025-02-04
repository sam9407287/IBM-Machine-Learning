# Gradient Boosting

## Introduction
Gradient Boosting is a machine learning technique used for regression and classification tasks. It builds a strong predictive model by combining multiple weak learners, typically decision trees.

## Concept
Gradient Boosting works by iteratively improving predictions using gradient descent optimization. The model corrects errors made by previous iterations, gradually reducing the overall prediction error.

### Steps in Gradient Boosting
1. **Initialize Model**: Start with a simple model (e.g., a decision tree) that makes initial predictions.
2. **Compute Residuals**: Calculate the difference (residuals) between the actual values and predicted values.
3. **Fit New Model to Residuals**: Train a new model to predict the residuals.
4. **Update Predictions**: Adjust previous predictions using the new model.
5. **Repeat**: Continue adding new models iteratively until convergence or a stopping criterion is met.

## Mathematical Formulation
Given a dataset with input features \( X \) and target values \( y \), the goal is to minimize a loss function \( L(y, F_m(X)) \), where \( F_m(X) \) is the model at iteration \( m \).

### 1. Initialize the Model
The first model \( F_0(X) \) is initialized to minimize the loss function:
\[
F_0(X) = \arg\min_c \sum_{i=1}^{n} L(y_i, c)
\]

### 2. Compute Residuals
For each iteration \( m \), compute the negative gradient (residuals) as an approximation of the loss function's gradient:
\[
 r_{im} = - \left( \frac{\partial L(y_i, F(X_i))}{\partial F(X_i)} \right)_{F(X) = F_{m-1}(X)}
\]

### 3. Fit a Weak Learner
A weak learner \( h_m(X) \) (e.g., a decision tree) is trained to predict \( r_{im} \):
\[
 h_m(X) = \arg\min_h \sum_{i=1}^{n} (r_{im} - h(X_i))^2
\]

### 4. Update the Model
The model is updated by adding the weak learner multiplied by a learning rate \( \nu \):
\[
F_m(X) = F_{m-1}(X) + \nu h_m(X)
\]

where \( \nu \) (learning rate) controls the contribution of each new model.

## Advantages
- Effective for structured data
- Can handle both regression and classification
- Works well with minimal preprocessing
- Robust to overfitting with proper tuning

## Disadvantages
- Computationally expensive
- Requires careful hyperparameter tuning
- Sensitive to noisy data

## Conclusion
Gradient Boosting is a powerful machine learning method that enhances predictive performance by iteratively correcting errors. With proper tuning, it achieves state-of-the-art results in many applications.
