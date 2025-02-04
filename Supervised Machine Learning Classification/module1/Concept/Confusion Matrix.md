# Confusion Matrix

## 1. Introduction
A Confusion Matrix is a table used to evaluate the performance of a classification model. It compares the predicted labels with the actual labels, providing insights into the model’s accuracy, precision, recall, and other metrics.

## 2. Confusion Matrix Structure

<img src="images/Confusion Matrix.avif" alt="Confusion Matrix" width="600" />

*Figure: Confusion Matrix.*

### Explanation:
- **True Positive (TP):** Correctly predicted positive cases.
- **False Negative (FN):** Model incorrectly predicts a negative label when the actual is positive.
- **False Positive (FP):** Model incorrectly predicts a positive label when the actual is negative.
- **True Negative (TN):** Correctly predicted negative cases.

## 3. Performance Metrics
Using values from the confusion matrix, various performance metrics can be calculated:

### Accuracy
\[
Accuracy = \frac{TP + TN}{TP + TN + FP + FN}
\]
Represents the overall correctness of the model.

### Precision (Positive Predictive Value, PPV)
\[
Precision = \frac{TP}{TP + FP}
\]
Measures how many predicted positives are actually correct.

### Recall (Sensitivity, True Positive Rate, TPR)
\[
Recall = \frac{TP}{TP + FN}
\]
Measures how many actual positives are correctly identified.

### F1 Score
\[
F1 Score = 2 \times \frac{Precision \times Recall}{Precision + Recall}
\]
Balances precision and recall.

### Specificity (True Negative Rate, TNR)
\[
Specificity = \frac{TN}{TN + FP}
\]
Measures how many actual negatives are correctly identified.

### False Positive Rate (FPR)
\[
FPR = \frac{FP}{FP + TN}
\]
Probability of incorrectly classifying a negative sample as positive.

### False Negative Rate (FNR)
\[
FNR = \frac{FN}{FN + TP}
\]
Probability of incorrectly classifying a positive sample as negative.

## 4. Interpretation and Use Cases
- **High Precision, Low Recall:** The model is conservative in predicting positives, reducing false positives but missing some true positives. Useful in applications like spam detection.
- **High Recall, Low Precision:** The model tries to capture all positive cases, leading to more false positives. Useful in medical diagnostics where missing a disease is costly.
- **Balanced F1 Score:** Used when both precision and recall are important.
