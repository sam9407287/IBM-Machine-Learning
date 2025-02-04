# ROC Curve and Precision-Recall Curve

## **1. Introduction**
When evaluating classification models, especially in binary classification tasks, two essential evaluation metrics are:
- **Receiver Operating Characteristic (ROC) Curve**
- **Precision-Recall (PR) Curve**

These curves provide insights into a model's performance under different decision thresholds. Understanding their differences and appropriate use cases is crucial for selecting the best model and threshold.

---

## **2. ROC Curve**
### **2.1 What is the ROC Curve?**
The **ROC curve** plots the relationship between:
- **True Positive Rate (TPR) = Sensitivity = Recall**  
  \[
  TPR = \frac{TP}{TP + FN}
  \]
- **False Positive Rate (FPR)**  
  \[
  FPR = \frac{FP}{FP + TN}
  \]

It illustrates how well the model distinguishes between positive and negative classes across different thresholds.

### **2.2 How is the ROC Curve Generated?**
- Vary the decision threshold (from 0 to 1).
- Calculate **TPR** and **FPR** at each threshold.
- Plot **TPR (y-axis) vs. FPR (x-axis)**.

### **2.3 Advantages and Disadvantages of ROC Curve**
| **Advantages** | **Disadvantages** |
|--------------|----------------|
| Provides a complete view of the trade-off between sensitivity and specificity. | Can be misleading when dealing with highly imbalanced datasets. |
| Useful for selecting the best threshold using Youden’s J statistic. | Not ideal when false positives and false negatives have different costs. |

---

## **3. Precision-Recall (PR) Curve**
### **3.1 What is the PR Curve?**
The **Precision-Recall curve** focuses on the performance of the positive class. It plots:
- **Precision (Positive Predictive Value):**  
  \[
  Precision = \frac{TP}{TP + FP}
  \]
- **Recall (Sensitivity, TPR):**  
  \[
  Recall = \frac{TP}{TP + FN}
  \]

### **3.2 How is the PR Curve Generated?**
- Vary the decision threshold (from 0 to 1).
- Compute **Precision** and **Recall** at each threshold.
- Plot **Precision (y-axis) vs. Recall (x-axis)**.

### **3.3 Advantages and Disadvantages of PR Curve**
| **Advantages** | **Disadvantages** |
|--------------|----------------|
| More informative when dealing with imbalanced datasets. | Does not consider true negatives, so it may not reflect full model performance. |
| Directly evaluates model’s ability to identify the positive class. | Requires additional metrics (like F1-score) for a single threshold evaluation. |

---

<img src="images/ROC and PR curve.png" alt="ROC and PR curve" width="800" />

*Figure: ROC and PR curve*

---

## **4. When to Use ROC vs. PR Curve**
| **Scenario** | **Recommended Curve** |
|------------|----------------------|
| Balanced dataset | ROC Curve |
| Imbalanced dataset (rare positive cases) | PR Curve |
| When false positives and false negatives have equal importance | ROC Curve |
| When minimizing false positives is critical | PR Curve |

---

## **5. Choosing the Optimal Threshold**
- **From the ROC Curve:**  
  - Use **Youden’s J statistic**, which maximizes:  
    \[
    J = TPR - FPR
    \]
- **From the PR Curve:**  
  - Choose the threshold that **maximizes the F1-score**, which balances precision and recall:  
    \[
    F1 = \frac{2 \times Precision \times Recall}{Precision + Recall}
    \]

---

## **6. Summary**
- **ROC Curve** is useful for balanced datasets and overall model evaluation.
- **PR Curve** is more informative when the dataset is highly imbalanced.
- **Choosing a threshold** depends on the problem: Youden’s J statistic (ROC) or F1-score (PR).

Understanding these metrics helps optimize model performance based on the problem at hand.
