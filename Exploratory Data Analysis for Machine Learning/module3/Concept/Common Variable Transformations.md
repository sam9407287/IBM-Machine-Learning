# Common Variable Transformations

## Feature Types and Transformations

### Continuous: Numerical Values
- **Standard Scaling**: Transforms data to have a mean of 0 and a standard deviation of 1. It is useful when the data follows a Gaussian distribution and is required for algorithms like SVM, PCA, and linear regression.
- **Min-Max Scaling**: Scales data to a specified range, typically [0, 1]. It is suitable for data that does not follow a Gaussian distribution and is often used in neural networks and k-nearest neighbors (KNN).
- **Robust Scaling**: Uses the median and interquartile range, making it robust to outliers. It is ideal for datasets with significant outliers.

### Nominal: Categorical, Unordered Features
- **Binary Encoding**: Converts categories into binary values (0 or 1). It is useful for reducing dimensionality compared to One-Hot Encoding while preserving categorical information.
- **One-Hot Encoding**: Converts categories into a binary matrix where each category is represented by a binary vector (e.g., [1, 0, 0], [0, 1, 0], [0, 0, 1]). It is essential for algorithms that cannot handle categorical data directly, such as linear regression.

### Ordinal: Categorical, Ordered Features
- **Ordinal Encoding**: Assigns integer values to categories based on their order (e.g., 0, 1, 2, 3 for movie ratings). It is suitable for ordinal data where the order of categories matters, such as in tree-based models.

### Skewed Data: Non-Normal Distributions
- **Log Transformation**: Applies a logarithmic function to reduce skewness in highly skewed data (e.g., right-skewed data). It is useful for making the data more normally distributed and reducing the impact of outliers.
- **Box-Cox Transformation**: Applies a power transformation to make data more normally distributed. It is effective for positively skewed and non-negative data.

### Feature Interaction and Non-Linear Relationships
- **Polynomial Features**: Generates polynomial and interaction features to capture non-linear relationships. It is useful for linear models to model complex patterns in the data.
- **Feature Binning**: Converts continuous data into discrete bins to handle non-linear relationships. It is often used to group continuous data into categories for better interpretability.

### High-Cardinality Categorical Features
- **Target Encoding**: Encodes categorical variables using the mean of the target variable. It is effective for high-cardinality categorical features and is commonly used in tree-based models and gradient boosting.
- **Frequency Encoding**: Encodes categories based on their frequency of occurrence. It is useful when the frequency of categories is informative for the target variable.

---

## Summary
Feature transformation is a critical step in preparing data for machine learning models. The choice of transformation depends on the type of data (continuous, nominal, ordinal), its distribution, and the specific requirements of the model. Understanding the strengths and limitations of each transformation method helps in selecting the most appropriate technique for a given problem.