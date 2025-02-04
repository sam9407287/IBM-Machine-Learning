# Tomek Links for Down-Sampling

Tomek Links are a data cleaning technique used to address class imbalance in datasets. They focus on removing ambiguous or noisy samples from the majority class that are close to minority class samples. This helps to clarify the decision boundary between classes and improves the performance of classification models.

---

## What are Tomek Links?

### Definition
A Tomek Link is a pair of samples (one from the majority class and one from the minority class) that are each other's nearest neighbors. These pairs are considered "ambiguous" because they lie close to the decision boundary, making it difficult for the model to classify them correctly.

### Key Idea
- Remove majority class samples that form Tomek Links with minority class samples.
- This reduces overlap between classes and sharpens the decision boundary.

---

## How Tomek Links Work

### Step-by-Step Process
1. **Identify Nearest Neighbors**: For each sample in the dataset, find its nearest neighbor.
2. **Find Tomek Links**: Identify pairs of samples (one from the majority class and one from the minority class) that are each other's nearest neighbors.
3. **Remove Majority Class Samples**: Remove the majority class samples involved in Tomek Links to reduce class overlap.

---

## Advantages of Tomek Links

1. **Improved Class Separation**:
   - By removing ambiguous samples, Tomek Links help clarify the decision boundary between classes.

2. **Noise Reduction**:
   - Tomek Links effectively remove noisy or borderline samples that can confuse the model.

3. **Preserves Data Integrity**:
   - Unlike random under-sampling, Tomek Links selectively remove only problematic samples, preserving the overall structure of the dataset.

---

## Limitations of Tomek Links

1. **Limited Reduction**:
   - Tomek Links may not remove enough samples to fully balance a highly imbalanced dataset.

2. **Computational Cost**:
   - Finding nearest neighbors can be computationally expensive for large datasets.

3. **Risk of Over-Cleaning**:
   - In some cases, removing too many samples may lead to loss of useful information.

---

## When to Use Tomek Links

- **Imbalanced Datasets**: When the majority class significantly outweighs the minority class.
- **Noisy Data**: When the dataset contains ambiguous or borderline samples.
- **Preprocessing Step**: As a data cleaning step before applying other sampling techniques (e.g., SMOTE or random under-sampling).

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

Tomek Links are a powerful technique for cleaning imbalanced datasets by removing ambiguous samples near the decision boundary. They help improve class separation and reduce noise, making them a valuable preprocessing step in machine learning workflows. However, they are best used in combination with other sampling techniques to fully address class imbalance.