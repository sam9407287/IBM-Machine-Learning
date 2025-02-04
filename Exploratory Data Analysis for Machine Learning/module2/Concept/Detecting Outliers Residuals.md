# Detecting Outliers: Residuals

Residuals represent the differences between actual and predicted values of the outcome variable and are crucial for identifying model failures.

## Approaches to Calculating Residuals

### 1. Standardized Residuals
- **Definition**: Standardized residuals are calculated by dividing the residual by its standard error.
- **Formula**: 
  \[
  \text{Standardized Residual} = \frac{\text{Residual}}{\text{Standard Error of Residuals}}
  \]
- **Purpose**: Standardized residuals help identify data points that deviate significantly from the model's predictions. They typically follow a standard normal distribution, so values with absolute magnitudes greater than 2 or 3 may indicate outliers.

### 2. Deleted Residuals
- **Definition**: Deleted residuals are calculated by fitting the model on all data excluding the current observation and then computing the residual for the excluded observation.
- **Calculation Steps**:
  1. Remove the current observation from the dataset.
  2. Fit the regression model using the remaining data.
  3. Predict the value for the excluded observation.
  4. Calculate the deleted residual: 
     \[
     \text{Deleted Residual} = \text{Actual Value} - \text{Predicted Value (without current observation)}
     \]
- **Purpose**: Deleted residuals help identify observations that have a significant impact on the model. A large deleted residual suggests that the observation is influential or potentially an outlier.

### 3. Studentized Residuals
- **Definition**: Studentized residuals are calculated by dividing the deleted residual by its standard error, which is computed either from all data or from all data excluding the current observation.
- **Formula**:
  \[
  \text{Studentized Residual} = \frac{\text{Deleted Residual}}{\text{Standard Error of Residuals (without current observation)}}
  \]
- **Purpose**: Studentized residuals provide a more refined measure for identifying outliers by standardizing the deleted residuals. They also typically follow a standard normal distribution, making it easier to spot outliers with absolute values greater than 2 or 3.

## Summary
- **Standardized Residuals**: Simple standardization of residuals for easier comparison and outlier detection.
- **Deleted Residuals**: Assess the impact of individual observations by excluding them from the model fitting process.
- **Studentized Residuals**: Combine the benefits of deleted and standardized residuals for more precise outlier detection.

These methods are essential in regression analysis for diagnosing model fit and detecting outliers, thereby enhancing the accuracy and robustness of the model.