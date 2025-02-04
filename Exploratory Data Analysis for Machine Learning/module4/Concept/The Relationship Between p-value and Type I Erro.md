# The Relationship Between p-value and Type I Error

In statistical hypothesis testing, the **p-value** and **Type I error** are closely related concepts. Understanding their relationship is crucial for interpreting the results of statistical tests.

---

## 1. **p-value**
- **Definition**: The probability of observing the current data, or more extreme data, assuming that the null hypothesis (H₀) is true.
- **Interpretation**:
  - A small p-value indicates that the observed data is unlikely under the null hypothesis.
  - A large p-value suggests that the data is consistent with the null hypothesis.

---

## 2. **Type I Error**
- **Definition**: The error of rejecting the null hypothesis (H₀) when it is actually true.
- **Probability**: Denoted by α (alpha), the significance level.
- **Common Values**: α is typically set at 0.05 (5%) or 0.01 (1%).
The Relationship Between p-value and Type I Erro
---

## 3. **The Relationship Between p-value and Type I Error**
- **Decision Rule**:
  - If the **p-value ≤ α**, reject the null hypothesis (H₀).
  - If the **p-value > α**, fail to reject the null hypothesis (H₀).
- **Interpretation**:
  - When you reject H₀ based on p-value ≤ α, there is a risk of committing a Type I error.
  - The probability of committing a Type I error is exactly α.

---

## 4. **Example**
- **Scenario**: You conduct a hypothesis test with α = 0.05.
- **Result**: The p-value calculated from your data is 0.03.
- **Conclusion**:
  - Since 0.03 ≤ 0.05, you reject the null hypothesis.
  - There is a 5% chance that this rejection is a Type I error (false positive).

---

## 5. **Key Points**
- **p-value** is a measure of the evidence against the null hypothesis.
- **Type I Error** is the risk of falsely rejecting a true null hypothesis.
- **α (Significance Level)** is the threshold for determining statistical significance and controls the probability of Type I error.

---

## 6. **Controlling Type I Error**
- **Lower α**: Reduces the probability of Type I error but increases the risk of Type II error (failing to reject a false null hypothesis).
- **Higher α**: Increases the probability of Type I error but reduces the risk of Type II error.

---

## 7. **Summary**
- The **p-value** helps determine whether to reject the null hypothesis.
- The **Type I error rate (α)** is the probability of incorrectly rejecting a true null hypothesis.
- By setting α, you control the trade-off between Type I and Type II errors in your hypothesis testing.

Understanding this relationship ensures accurate interpretation of statistical results and helps avoid misleading conclusions.