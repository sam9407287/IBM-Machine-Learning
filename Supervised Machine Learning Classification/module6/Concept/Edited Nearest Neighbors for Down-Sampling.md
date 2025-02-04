# Edited Nearest Neighbors for Down-Sampling

Edited Nearest Neighbors (ENN) is a data cleaning technique used to address class imbalance and improve the performance of classification models. Unlike traditional down-sampling methods, ENN focuses on removing noisy or misclassified samples from both the majority and minority classes. This helps to refine the dataset and enhance the model's ability to generalize.

---

## What is Edited Nearest Neighbors (ENN)?

### Definition
ENN is an under-sampling method that removes samples that are misclassified by their nearest neighbors. It evaluates each sample in the dataset and removes it if its class label does not match the majority class label of its nearest neighbors.

### Key Idea
- Remove samples that are inconsistent with their local neighborhood.
- This helps to reduce noise and improve the clarity of the decision boundary.

---

## How Edited Nearest Neighbors (ENN) Works

### Step-by-Step Process
1. **Identify Nearest Neighbors**: For each sample in the dataset, find its k nearest neighbors.
2. **Evaluate Consistency**: Check if the sample's class label matches the majority class label of its nearest neighbors.
3. **Remove Inconsistent Samples**: Remove samples that are misclassified by their nearest neighbors.

---

## Advantages of Edited Nearest Neighbors (ENN)

1. **Noise Reduction**:
   - ENN effectively removes noisy or misclassified samples, leading to a cleaner dataset.

2. **Improved Model Performance**:
   - By refining the dataset, ENN helps the model to better generalize and make more accurate predictions.

3. **Applicability to Both Classes**:
   - ENN can remove samples from both the majority and minority classes, making it versatile for various types of datasets.

---

## Limitations of Edited Nearest Neighbors (ENN)

1. **Potential Over-Cleaning**:
   - ENN may remove too many samples, leading to a loss of valuable information.

2. **Computational Cost**:
   - Finding nearest neighbors can be computationally expensive, especially for large datasets.

3. **Dependence on Neighborhood Size**:
   - The effectiveness of ENN depends on the choice of the number of nearest neighbors (k), which may require tuning.

---

## When to Use Edited Nearest Neighbors (ENN)

- **Noisy Datasets**: When the dataset contains many misclassified or noisy samples.
- **Imbalanced Datasets**: When the class distribution is skewed, and cleaning the dataset can help improve model performance.
- **Preprocessing Step**: As a data cleaning step before applying other sampling techniques or model training.

---

## Comparison with Other Down-Sampling Methods

| **Aspect**          | **Edited Nearest Neighbors (ENN)**          | **Tomek Links**                              | **NearMiss**                              |
|----------------------|---------------------------------------------|---------------------------------------------|-------------------------------------------|
| **Goal**            | Remove misclassified samples                | Remove ambiguous samples near the boundary  | Selectively reduce majority class samples |
| **Focus**           | Data cleaning and noise reduction           | Data cleaning and noise reduction           | Balancing class distribution              |
| **Sample Removal**  | Removes inconsistent samples from both classes | Removes only problematic samples            | Removes samples based on distance metrics |
| **Computational Cost** | Moderate to high (nearest neighbor search) | Moderate (nearest neighbor search)          | High (distance calculations)              |
| **Use Case**        | Noisy datasets with misclassified samples   | Noisy datasets with borderline samples      | Highly imbalanced datasets                |

---

## Conclusion

Edited Nearest Neighbors (ENN) is a powerful technique for cleaning datasets by removing noisy or misclassified samples. It helps to improve the clarity of the decision boundary and enhances the model's ability to generalize. While ENN is effective for noise reduction, it should be used carefully to avoid over-cleaning and loss of valuable information. Combining ENN with other sampling techniques can further improve the performance of classification models on imbalanced datasets.