# Support Vector Machine 

## Introduction
Support Vector Machine (SVM) is a supervised learning algorithm used for classification and regression tasks. It is particularly effective for high-dimensional spaces and works well even when the number of samples is smaller than the number of dimensions.

## Concept
SVM works by finding an optimal **hyperplane** that best separates data points of different classes. The key idea is to maximize the **margin** between the closest data points (support vectors) of different classes.

### Types of SVM
- **Linear SVM**: Used when data is linearly separable.
- **Non-Linear SVM**: Uses kernel functions to transform data into a higher-dimensional space where it becomes linearly separable.

## Mathematical Formulation
### 1. Linear SVM
For a given dataset with feature vectors \( x_i \) and corresponding labels \( y_i \in \{-1,1\} \), the decision function is:

\[ f(x) = w^T x + b \]

where \( w \) is the weight vector and \( b \) is the bias.

To maximize the margin, we solve the optimization problem:

\[ \min_{w,b} \frac{1}{2} ||w||^2 \]

subject to the constraints:

\[ y_i (w^T x_i + b) \geq 1, \quad \forall i \]

### 2. Non-Linear SVM with Kernel Trick
When data is not linearly separable, we use kernel functions \( K(x_i, x_j) \) to map data into a higher-dimensional space where it can be separated linearly. The optimization problem is then solved in this transformed space.

Common kernel functions:
- **Linear Kernel**: \( K(x_i, x_j) = x_i^T x_j \)
- **Polynomial Kernel**: \( K(x_i, x_j) = (x_i^T x_j + c)^d \)
- **Radial Basis Function (RBF) Kernel**: \( K(x_i, x_j) = \exp(-\gamma ||x_i - x_j||^2) \)

### 3. Soft Margin SVM
When data is not perfectly separable, we introduce slack variables \( \xi_i \) and a regularization parameter \( C \) to allow misclassification:

\[ \min_{w,b,\xi} \frac{1}{2} ||w||^2 + C \sum \xi_i \]

subject to:

\[ y_i (w^T x_i + b) \geq 1 - \xi_i, \quad \xi_i \geq 0 \]

where \( C \) controls the trade-off between maximizing the margin and minimizing misclassification errors.

## Conclusion
SVM is a powerful tool for classification and regression tasks. It works well in high-dimensional spaces and is effective even with limited data. The choice of the kernel function plays a crucial role in handling non-linearly separable data.

---


