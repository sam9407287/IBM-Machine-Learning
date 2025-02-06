# Non-negative Matrix Factorization

## Introduction

Non-negative Matrix Factorization (NMF) is a dimensionality reduction technique that decomposes a non-negative matrix **V** into two non-negative matrices, **W** and **H**.  This means all elements in **V**, **W**, and **H** must be greater than or equal to zero.  NMF is particularly useful when the data being analyzed represents counts, intensities, or other quantities that are inherently non-negative (e.g., pixel intensities in images, word counts in documents, spectral data).

## How NMF Works

Given a non-negative data matrix **V** ( *n x m*, where *n* is the number of samples and *m* is the number of features), NMF aims to find two non-negative matrices:

*   **W** ( *n x k* ):  Often called the "basis" or "feature" matrix.  Each column of **W** represents a "basis vector" or a learned feature.
*   **H** ( *k x m* ):  Often called the "coefficient" or "encoding" matrix.  Each row of **H** represents the weights or coefficients that combine the basis vectors in **W** to reconstruct the original data.

The goal is to find **W** and **H** such that:

**V** ≈ **WH**

Where *k* (the number of components) is typically chosen to be smaller than both *n* and *m*, achieving dimensionality reduction. The approximation is minimized using a cost function, typically one of the following:

1.  **Euclidean Distance:**
    *   Cost Function:  ||**V** - **WH**||<sub>F</sub><sup>2</sup>  (Frobenius norm squared)
    *   This measures the squared difference between the original matrix **V** and the reconstruction **WH**.

2.  **Kullback-Leibler (KL) Divergence:**
    *   Cost Function:  D<sub>KL</sub>(**V** || **WH**) = Σ<sub>ij</sub> (**V**<sub>ij</sub> log (**V**<sub>ij</sub> / (**WH**)<sub>ij</sub>) - **V**<sub>ij</sub> + (**WH**)<sub>ij</sub>)
    *   KL divergence is often preferred when dealing with count data or probabilities, as it is a measure of how one probability distribution diverges from another.

3. **Itakura-Saito (IS) Divergence**
    *   Cost Function:  D<sub>IS</sub>(**V** || **WH**) = Σ<sub>ij</sub> ( **V**<sub>ij</sub> / (**WH**)<sub>ij</sub> - log( **V**<sub>ij</sub> / (**WH**)<sub>ij</sub>) - 1)
    * IS divergence is useful for signal processing, particularly audio processing.

The optimization problem is generally non-convex, meaning there is no guarantee of finding a global minimum. Common algorithms to find **W** and **H** are iterative and include:

*   **Multiplicative Update Rules:**  A popular and relatively simple algorithm.  Separate update rules are derived for **W** and **H** based on the chosen cost function.  These updates ensure non-negativity.

    *   **Euclidean Distance Update Rules:**
        *   **H**<sub>aj</sub> ← **H**<sub>aj</sub> * ((**W**<sup>T</sup>**V**)<sub>aj</sub> / (**W**<sup>T</sup>**WH**)<sub>aj</sub>)
        *   **W**<sub>ia</sub> ← **W**<sub>ia</sub> * ((**VH**<sup>T</sup>)<sub>ia</sub> / (**WHH**<sup>T</sup>)<sub>ia</sub>)

    *   **KL Divergence Update Rules:**
        *    **H**<sub>aj</sub> ← **H**<sub>aj</sub> * (Σ<sub>i</sub> **W**<sub>ia</sub>**V**<sub>ij</sub> / (**WH**)<sub>ij</sub> ) / (Σ<sub>i</sub>**W**<sub>ia</sub>)
        *   **W**<sub>ia</sub> ← **W**<sub>ia</sub> * (Σ<sub>j</sub> **H**<sub>aj</sub>**V**<sub>ij</sub> / (**WH**)<sub>ij</sub> ) / (Σ<sub>j</sub>**H**<sub>aj</sub>)

*   **Projected Gradient Descent:** Uses gradient descent with projections to ensure non-negativity.
*   **Alternating Least Squares (ALS):**  Alternates between optimizing **W** while keeping **H** fixed, and optimizing **H** while keeping **W** fixed. Each subproblem is a convex non-negative least squares problem.
* **Block Coordinate Descent** A more generalized version of ALS.

The algorithms are typically initialized with random non-negative values for **W** and **H** and then iteratively updated until a convergence criterion is met (e.g., a small change in the cost function or a maximum number of iterations).

## Advantages of NMF

*   **Non-negativity:**  The non-negativity constraints often lead to a parts-based representation of the data, making the results more interpretable, especially in domains where negative values are meaningless.
*   **Sparsity:** NMF often produces sparse solutions for **W** and **H**, even without explicit sparsity constraints. This can further enhance interpretability and reduce storage requirements.  Sparsity can also be explicitly encouraged by adding regularization terms to the cost function.
*   **Dimensionality Reduction:** Reduces the dimensionality of the data, similar to PCA.
*   **Feature Extraction:**  Learns meaningful features (basis vectors) from the data.

## Disadvantages of NMF

*   **Non-convexity:**  The optimization problem is non-convex, so there's no guarantee of finding the global optimum.  Results can depend on the initialization.
*   **Choice of *k*:** The number of components (*k*) needs to be chosen appropriately, which can require experimentation or domain knowledge.
*   **Linearity Assumption:** While the components are additive, the relationships between the original features captured by the basis vectors are effectively linear combinations. NMF does not capture interactions between the *basis vectors themselves*.
*   **Non-negative Data Only:**  NMF is only applicable to non-negative data.

## Comparison with PCA, Kernel PCA, and MDS

| Feature           | NMF                                      | PCA                                       | Kernel PCA                                    | MDS                                          |
| ----------------- | ---------------------------------------- | ----------------------------------------- | --------------------------------------------- | -------------------------------------------- |
| **Non-negativity** | Enforces non-negativity                 | No non-negativity constraint             | No non-negativity constraint             | No non-negativity constraint               |
| **Linearity**     | Linear combinations of non-negative parts | Linear combinations (can be positive or negative) | Non-linear                                  | Can be linear or non-linear (depending on MDS type) |
| **Input Data**    | Non-negative matrix                       | Any matrix                                | Original data features                       | Dissimilarity matrix                          |
| **Interpretability** | High (parts-based representation)     | Moderate                                  | Low                                         | Low                                       |
| **Sparsity**     | Often sparse, can be enforced           | Generally not sparse                       | Generally not sparse                      | Generally not sparse                     |
| **Optimization**  | Non-convex, iterative                    | Convex, closed-form solution (eigenvalue decomposition) | Convex in the feature space, but via eigenvalue decomposition of the kernel matrix| Typically iterative (e.g., stress minimization)  |
| **Assumptions**   | Data is non-negative and can be represented as additive combinations of non-negative parts | Data has linear relationships, and principal components capture the directions of maximum variance | Data lies on a non-linear manifold that can be captured by the chosen kernel | Dissimilarities represent meaningful distances or relationships |
| **Goal**       | Find non-negative basis vectors and coefficients that reconstruct the original data| Find orthogonal basis vectors that maximize variance|Find non-linear basis vectors in a high dimensional feature space | Find a low-dimensional representation that preserves (or approximates) dissimilarities |

**Key Differences Summarized:**

*   **NMF vs. PCA:**  The most significant difference is the non-negativity constraint in NMF.  This leads to a parts-based representation, which is often more interpretable than PCA's principal components, which can have both positive and negative values.  PCA finds orthogonal components that maximize variance, while NMF finds additive components that reconstruct the data. PCA has a closed-form solution, while NMF uses iterative algorithms.
*   **NMF vs. Kernel PCA:** Kernel PCA extends PCA to handle non-linear relationships, while NMF remains fundamentally a linear technique (although applied to non-negative data).  Kernel PCA uses the kernel trick to implicitly map data to a high-dimensional feature space, while NMF operates directly on the original (non-negative) data. Both can be computationally expensive.
*   **NMF vs. MDS:**  MDS operates on a dissimilarity matrix, while NMF operates directly on the non-negative data matrix.  MDS aims to preserve distances (or dissimilarities) between data points, while NMF aims to reconstruct the original data from additive parts. MDS can be more flexible in handling different types of relationships, but NMF's non-negativity constraint often leads to more interpretable results when applicable.

In summary, NMF is a valuable technique when dealing with non-negative data and seeking an interpretable, parts-based representation. It offers a different perspective on dimensionality reduction compared to PCA, Kernel PCA, and MDS, each of which has its own strengths and weaknesses.