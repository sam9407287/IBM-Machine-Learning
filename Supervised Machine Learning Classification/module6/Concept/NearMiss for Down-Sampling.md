# NearMiss for Down-Sampling

NearMiss is a set of under-sampling techniques used to handle imbalanced datasets in machine learning. These methods selectively reduce the number of samples from the majority class to improve the performance of classification models, especially for minority classes. Below is an overview of the three main variants of NearMiss: NearMiss-1, NearMiss-2, and NearMiss-3.

---

## NearMiss-1: Closest to Nearby Minority Points

### Strategy
NearMiss-1 selects majority class samples that are closest to the **average distance** of nearby minority class samples.

### Key Features
- Focuses on preserving majority class samples that are near the minority class boundary.
- Helps the model learn the decision boundary more effectively.
- Suitable for datasets where the boundary between classes is crucial.

### Example
If a minority class sample is surrounded by several majority class samples, NearMiss-1 will retain the majority class samples closest to the minority sample.

---

## NearMiss-2: Closest to Distant Minority Points

### Strategy
NearMiss-2 selects majority class samples that are closest to the **farthest minority class samples**.

### Key Features
- Retains majority class samples that are distributed more broadly across the dataset.
- Avoids over-concentration of samples near the minority class boundary.
- Useful for datasets where the minority class is spread out.

### Example
If a minority class sample is far from other samples, NearMiss-2 will retain the majority class samples closest to this distant minority sample.

---

## NearMiss-3: Closest to Majority Neighbors of Minority Points

### Strategy
NearMiss-3 selects majority class samples that are closest to the **nearest neighbors of minority class samples**.

### Key Features
- Ensures that each minority class sample has a sufficient number of majority class samples around it.
- Reduces the impact of noise in the dataset.
- Ideal for datasets with local imbalances or noisy data.

### Example
For each minority class sample, NearMiss-3 identifies its nearest neighbors and retains the majority class samples closest to these neighbors.

---

## Comparison of NearMiss Variants

| **Variant**   | **Selection Criteria**                          | **Use Case**                              | **Advantages**                              | **Disadvantages**                          |
|---------------|------------------------------------------------|-------------------------------------------|---------------------------------------------|--------------------------------------------|
| **NearMiss-1**| Closest to average minority samples            | Boundary-sensitive classification         | Preserves boundary information              | May over-concentrate near minority samples |
| **NearMiss-2**| Closest to farthest minority samples           | Datasets with spread-out minority classes | Broadens sample distribution                | May retain irrelevant majority samples     |
| **NearMiss-3**| Closest to neighbors of minority samples       | Noisy or locally imbalanced datasets      | Reduces noise impact, handles local imbalance| Computationally more expensive             |

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

NearMiss down-sampling algorithms are powerful tools for addressing class imbalance in machine learning. By selectively reducing the majority class samples, these methods help improve the model's ability to learn from minority classes. The choice of NearMiss variant depends on the specific characteristics of the dataset and the problem at hand:

- Use **NearMiss-1** for boundary-sensitive tasks.
- Use **NearMiss-2** for datasets with widely spread minority classes.
- Use **NearMiss-3** for noisy or locally imbalanced datasets.

By understanding and applying these techniques, you can enhance the performance of your classification models on imbalanced datasets.