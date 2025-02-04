# Core Metrics in Regression Analysis

In regression analysis, SSE (Sum of Squared Errors), TSS (Total Sum of Squares), R² (R-squared), and MSE (Mean Squared Error) are four key metrics used to evaluate the performance and predictive ability of a model. These metrics are interconnected and together provide a comprehensive understanding of how well a model fits the data. Below is a detailed explanation of each metric and their relationships.

---

## 1. **SSE (Sum of Squared Errors)**
SSE measures the total squared difference between the actual values and the predicted values, representing the portion of variability that the model fails to explain.

### Formula:
\[ SSE = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 \]

- \( y_i \): The \( i \)-th actual value
- \( \hat{y}_i \): The \( i \)-th predicted value
- \( n \): Number of samples

### Interpretation:
- A smaller SSE indicates lower prediction errors and a better fit.
- SSE is influenced by the sample size; larger datasets may result in a larger SSE.

---

## 2. **TSS (Total Sum of Squares)**
TSS measures the total squared difference between the actual values and their mean, representing the total variability in the data.

### Formula:
\[ TSS = \sum_{i=1}^{n} (y_i - \bar{y})^2 \]

- \( \bar{y} \): Mean of the actual values

### Interpretation:
- TSS reflects the total variability in the data.
- TSS is a fixed value and does not depend on the model.

---

## 3. **R² (R-squared)**
R², also known as the coefficient of determination, measures the proportion of variability in the data that is explained by the model. Its value ranges from 0 to 1.

### Formula:
\[ R^2 = 1 - \frac{SSE}{TSS} \]

### Interpretation:
- An R² close to 1 indicates that the model explains most of the variability in the data.
- An R² close to 0 indicates that the model explains little to no variability.
- R² can be interpreted as the "explanatory power" of the model.

---

## 4. **MSE (Mean Squared Error)**
MSE is the average of the squared differences between the actual and predicted values, representing the average prediction error per data point.

### Formula:
\[ MSE = \frac{SSE}{n} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 \]

### Interpretation:
- A smaller MSE indicates lower prediction errors and a better fit.
- MSE normalizes SSE by dividing by the sample size, making it suitable for comparing models across different datasets.

---

## 5. **Relationships Between the Metrics**
SSE, TSS, R², and MSE are closely related and together form the core evaluation framework for regression analysis.

### (1) **SSE and MSE**
- MSE is the normalized version of SSE, obtained by dividing SSE by the sample size.
- Relationship:
  \[ MSE = \frac{SSE}{n} \]

### (2) **SSE and TSS**
- SSE represents the unexplained variability, while TSS represents the total variability.
- Relationship:
  \[ R^2 = 1 - \frac{SSE}{TSS} \]

### (3) **MSE and R²**
- MSE measures the average prediction error, while R² measures the explanatory power of the model.
- Relationship:
  \[ R^2 = 1 - \frac{MSE \cdot n}{TSS} \]

### (4) **Overall Relationship**
- When **MSE is small**, SSE is also small, and R² is close to 1, indicating a good fit.
- When **MSE is large**, SSE is also large, and R² is close to 0, indicating a poor fit.

---

## 6. **Practical Implications**
- **SSE** and **MSE** are used to measure prediction errors and optimize model parameters.
- **TSS** provides a baseline for total variability in the data and is used to calculate R².
- **R²** is used to evaluate the explanatory power of the model and compare the performance of different models.

---

## 7. **Summary**
- **SSE** and **MSE** focus on prediction errors; smaller values indicate better performance.
- **TSS** represents the total variability in the data and is independent of the model.
- **R²** measures the explanatory power of the model; values closer to 1 indicate better performance.

These four metrics form the foundation of regression analysis, providing a comprehensive framework for evaluating and improving model performance.