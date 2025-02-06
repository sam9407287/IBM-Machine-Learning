# Kernel PCA and Multidimensional Scaling

This document introduces and compares Kernel Principal Component Analysis (Kernel PCA) and Multidimensional Scaling (MDS), two powerful dimensionality reduction techniques. It also clarifies the relationship between classical MDS and standard PCA.

## 1. Kernel PCA

### Introduction

Kernel PCA is a non-linear extension of Principal Component Analysis (PCA). While standard PCA is limited to identifying linear relationships in data, Kernel PCA uses the "kernel trick" to perform PCA in a high-dimensional feature space, enabling it to capture non-linear relationships.

### How Kernel PCA Works

1.  **Kernel Function Selection:** A kernel function, *k(x<sub>i</sub>, x<sub>j</sub>)*, is chosen. This function implicitly calculates the dot product of the data points *x<sub>i</sub>* and *x<sub>j</sub>* in a high-dimensional feature space *without explicitly mapping the data to that space*.  Common kernel functions include:
    *   **Linear Kernel:**  *k(x<sub>i</sub>, x<sub>j</sub>) = x<sub>i</sub><sup>T</sup>x<sub>j</sub>* (equivalent to standard PCA)
    *   **Polynomial Kernel:** *k(x<sub>i</sub>, x<sub>j</sub>) = (x<sub>i</sub><sup>T</sup>x<sub>j</sub> + c)<sup>d</sup>*  (where *c* is a constant and *d* is the degree)
    *   **Gaussian (RBF) Kernel:** *k(x<sub>i</sub>, x<sub>j</sub>) = exp(-||x<sub>i</sub> - x<sub>j</sub>||<sup>2</sup> / (2σ<sup>2</sup>))* (where σ is a parameter controlling the width of the Gaussian)
    *   **Sigmoid Kernel:** *k(x<sub>i</sub>, x<sub>j</sub>) = tanh(αx<sub>i</sub><sup>T</sup>x<sub>j</sub> + c)* (where α and *c* are parameters)

2.  **Kernel Matrix Construction:** A kernel matrix, **K**, is constructed. The element at row *i* and column *j* of **K** is *k(x<sub>i</sub>, x<sub>j</sub>)*. This matrix represents the pairwise similarities between all data points in the high-dimensional feature space.

3.  **Centering the Kernel Matrix (Important!):** The kernel matrix needs to be centered.  This is analogous to centering the data in standard PCA.  The centered kernel matrix, **K'**, is calculated as:

    **K'** = **K** - **1<sub>n</sub>K** - **K1<sub>n</sub>** + **1<sub>n</sub>K1<sub>n</sub>**

    Where **1<sub>n</sub>** is an *n x n* matrix where all elements are 1/n, and *n* is the number of data points.  This centering step is crucial for Kernel PCA to work correctly.

4.  **Eigenvalue Decomposition:** The eigenvectors and eigenvalues of the *centered* kernel matrix **K'** are calculated.

    **K'v** = λ**v**

5.  **Normalization of Eigenvectors:** The eigenvectors are normalized. In Kernel PCA, the eigenvectors are typically normalized such that:
     λ<sub>i</sub> * (**v<sub>i</sub>**<sup>T</sup>**v<sub>i</sub>**) = 1. This is different than standard PCA.

6.  **Projection:** To project a new data point *x* onto the principal components, we calculate:

    *y<sub>i</sub>* = Σ<sub>j=1</sub><sup>n</sup> α<sub>ji</sub> *k(x<sub>j</sub>, x)*

    Where:
    *   *y<sub>i</sub>* is the projection of *x* onto the *i*-th principal component.
    *   α<sub>ji</sub> is the *j*-th element of the *i*-th normalized eigenvector.
    *    *x<sub>j</sub>* represents the original training data.
    *   *k(x<sub>j</sub>, x)* is the kernel function evaluated between the new data point *x* and the *j*-th training data point.

### Advantages of Kernel PCA

*   **Non-linear Dimensionality Reduction:** Can capture non-linear relationships in the data.
*   **Flexibility:**  The choice of kernel function allows you to tailor the method to different types of data.
*   **Implicit Mapping:**  Avoids explicit mapping to the high-dimensional feature space, which can be computationally expensive.

### Disadvantages of Kernel PCA

*   **Kernel Choice:** The performance of Kernel PCA is highly dependent on the choice of the kernel function and its parameters.  Choosing the right kernel requires domain knowledge or experimentation.
*   **Computational Cost:** Calculating the kernel matrix can be computationally expensive for large datasets.
*   **Interpretability:** The principal components in the feature space are often even harder to interpret than in standard PCA.
*   **Out-of-Sample Extension:** Projecting *new* data points (not in the original training set) requires computing the kernel function with all training points (as seen in the projection step). This can be slow for large datasets.

## 2. Multidimensional Scaling (MDS)

### Introduction

Multidimensional Scaling (MDS) is a family of techniques that aim to create a low-dimensional representation of data based on pairwise dissimilarities (or distances) between data points.  Unlike PCA, which operates directly on the data features, MDS takes a dissimilarity matrix as input.

### How MDS Works (Classical MDS)

1.  **Dissimilarity Matrix (Δ):**  The input to MDS is a dissimilarity matrix, Δ.  Element δ<sub>ij</sub> of this matrix represents the dissimilarity between data points *i* and *j*.  This dissimilarity can be measured using various metrics, such as Euclidean distance, correlation distance, or any other suitable measure.

2.  **Double Centering:** The dissimilarity matrix is transformed into a matrix **B** using a process called "double centering":

    **B** = -1/2 * **JΔ<sup>(2)</sup>J**

    Where:
    *   **Δ<sup>(2)</sup>** is a matrix where each element is the *square* of the corresponding element in Δ (δ<sub>ij</sub><sup>2</sup>).
    *   **J** is the centering matrix: **J** = **I** - (1/n) **11<sup>T</sup>** (**I** is the identity matrix, **1** is a column vector of ones, and *n* is the number of data points).

3.  **Eigenvalue Decomposition:** The eigenvectors and eigenvalues of matrix **B** are calculated.

    **Bv** = λ**v**

4.  **Coordinate Matrix:**  The coordinates of the data points in the reduced-dimensional space are obtained by taking the top *k* eigenvectors (corresponding to the *k* largest eigenvalues) and scaling them by the square root of their corresponding eigenvalues:

    **X** = **V<sub>k</sub>Λ<sub>k</sub><sup>1/2</sup>**

    Where:
    *   **X** is the *n x k* matrix of coordinates in the reduced space.
    *   **V<sub>k</sub>** is the matrix containing the top *k* eigenvectors.
    *   **Λ<sub>k</sub>** is a diagonal matrix containing the top *k* eigenvalues.

### Types of MDS

*   **Classical MDS (cMDS):**  As described above.  Assumes Euclidean distances.  It is *equivalent* to PCA when the dissimilarities are Euclidean distances calculated from centered data.
*   **Metric MDS:**  A more general term that includes cMDS. It tries to preserve the original distances as well as possible.
*   **Non-metric MDS (nMDS):**  Focuses on preserving the *rank order* of the dissimilarities, rather than the exact distances.  This is useful when the dissimilarities are ordinal (e.g., representing "similarity" ratings on a scale).

### Advantages of MDS

*   **Flexibility in Dissimilarity Measures:** Can handle various types of dissimilarity data, not just Euclidean distances.
*   **Non-linear Relationships:** Can capture non-linear relationships, especially with non-metric MDS.
*   **Visualization:**  Excellent for visualizing high-dimensional data in low dimensions based on their similarities.

### Disadvantages of MDS

*   **Computational Cost:** Can be computationally expensive for large datasets, especially the eigenvalue decomposition step.
*   **Interpretation:**  The dimensions in the reduced space may not have a clear interpretation.
*   **Stress:**  A measure called "stress" is used to evaluate how well MDS preserves the original dissimilarities.  High stress indicates a poor fit.  Choosing the right number of dimensions (*k*) involves balancing dimensionality reduction with minimizing stress.

## 3. Relationship Between Classical MDS and PCA

Classical MDS and PCA are closely related.  In fact, **when the dissimilarity matrix in classical MDS is computed using Euclidean distances on centered data, classical MDS is mathematically equivalent to PCA.** Here's why:

1.  **Centered Data and Euclidean Distance:** If we have centered data (mean of each feature is 0), the squared Euclidean distance between two data points *x<sub>i</sub>* and *x<sub>j</sub>* is:

    d<sub>ij</sub><sup>2</sup> = ||x<sub>i</sub> - x<sub>j</sub>||<sup>2</sup> = (x<sub>i</sub> - x<sub>j</sub>)<sup>T</sup>(x<sub>i</sub> - x<sub>j</sub>) = x<sub>i</sub><sup>T</sup>x<sub>i</sub> - 2x<sub>i</sub><sup>T</sup>x<sub>j</sub> + x<sub>j</sub><sup>T</sup>x<sub>j</sub>

2.  **Double Centering and the Covariance Matrix:** The double centering operation in cMDS transforms the squared Euclidean distance matrix into a matrix **B** that is proportional to the covariance matrix of the original data.  Specifically:

    **B** = **XX<sup>T</sup>** (for centered data)

    Where **X** is the data matrix (with centered columns).

3.  **Eigenvalue Decomposition Equivalence:** Since **B** is equivalent to the covariance matrix (up to a scaling factor), the eigenvalue decomposition of **B** in cMDS is equivalent to the eigenvalue decomposition of the covariance matrix in PCA.  The eigenvectors are the same, and the eigenvalues are proportional.

4.  **Coordinate Calculation Equivalence:** The final coordinate calculation in cMDS (scaling eigenvectors by the square root of eigenvalues) produces the same result as projecting the data onto the principal components in PCA.

**In summary:**  Classical MDS *with Euclidean distances on centered data* is equivalent to PCA.  This equivalence highlights the fundamental connection between distance-based methods (MDS) and variance-based methods (PCA).

## 4. Comparison Table: Kernel PCA vs. MDS vs. PCA

| Feature           | Kernel PCA                                    | MDS (Classical)                                | PCA                                       |
| ----------------- | --------------------------------------------- | ---------------------------------------------- | ----------------------------------------- |
| **Linearity**     | Non-linear                                  | Can be linear or non-linear (depending on MDS type) | Linear                                    |
| **Input Data**    | Original data features                       | Dissimilarity matrix                            | Original data features                     |
| **Kernel Trick**  | Yes                                           | No                                             | No                                        |
| **Computation**  | Kernel matrix calculation & eigenvalue decomposition | Double centering & eigenvalue decomposition         | Covariance matrix & eigenvalue decomposition |
| **Interpretability** | Low (feature space)                        | Low (dissimilarity-based)                      | Moderate (principal components)             |
| **Out-of-Sample**| Requires kernel evaluations with training data | Requires recomputing the embedding.        | Simple matrix multiplication                 |
| **Relationship** | Non-linear extension of PCA                 | Equivalent to PCA with Euclidean distance on centered data | Foundational linear dimensionality reduction |
| **Parameter** |Kernel type and parameters| Dissimilarity type| Number of components|
## Conclusion

Kernel PCA and MDS are powerful tools for dimensionality reduction, each with its strengths and weaknesses. Kernel PCA excels at capturing non-linear relationships through the kernel trick, while MDS provides flexibility in handling various types of dissimilarity data. Understanding the relationship between classical MDS and PCA provides valuable insight into the underlying principles of these techniques. Choosing the best method depends on the specific characteristics of your data and your analysis goals.