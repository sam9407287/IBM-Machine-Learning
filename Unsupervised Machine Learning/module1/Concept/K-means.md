# K-means Clustering Algorithm

## 1. Introduction

K-means is a widely used unsupervised learning algorithm for partitioning a dataset into K distinct, non-overlapping clusters. Its core idea is to iteratively assign data points to the nearest centroid and update the centroid's position until convergence.

## 2. Algorithm Steps

The K-means algorithm consists of the following main steps:

1.  **Initialization:** Randomly select K data points as the initial cluster centroids.
2.  **Assignment:** For each data point, calculate its distance to each of the K centroids and assign it to the cluster represented by the nearest centroid.
3.  **Update:** For each cluster, recalculate its centroid based on the data points currently assigned to that cluster. Typically, the new centroid is the mean of all data points in the cluster.
4.  **Iteration:** Repeat steps 2 and 3 until the centroids no longer change significantly or a predefined number of iterations is reached.

## 3. Iterative Process of the Algorithm

During each iteration of the K-means algorithm, data points may be reassigned to different clusters. This is because:

1.  **Centroid Update:** Each iteration recalculates the centroid of each cluster based on the data points currently assigned to it.
2.  **Distance Recalculation:** After the centroids are updated, the distance from each data point to the new centroids changes.
3.  **Reassignment:** Based on the new distances, data points are reassigned to the cluster represented by the nearest centroid.

Data points will seek out the nearest **existing centroid** and join the cluster represented by that centroid. Then, each centroid will recalculate its own position based on the **data points currently assigned to its cluster**.

## 4. Algorithm Evaluation using Inertia

Evaluating the clustering performance of the K-means algorithm often involves considering metrics like Inertia.

### 4.1 Inertia

Inertia measures the sum of squared distances between each data point and the centroid of its assigned cluster. It represents the compactness of the data points within each cluster.

**Formula:**

```
Inertia = Σ Σ (x<sub>i</sub> - μ<sub>j</sub>)<sup>2</sup>
```

Where:

*   x<sub>i</sub> represents the i-th data point
*   μ<sub>j</sub> represents the centroid of the j-th cluster
*   The first summation iterates over all data points
*   The second summation iterates over all clusters

**Lower Inertia values indicate tighter clusters, suggesting better clustering performance.**

**Using Inertia for K Selection (Elbow Method):**

The Elbow Method is a common technique to aid in determining the optimal number of clusters (K). This involves plotting the Inertia values against different values of K and looking for the "elbow" point on the curve.

**Rationale:**

*   As the K value increases, Inertia generally decreases.
*   When K is small, increasing K will lead to a significant drop in Inertia.
*   After a certain point, increasing K further results in diminishing returns, with smaller reductions in Inertia.

The K value at the "elbow" point is often considered a good choice, as it suggests that the benefit of adding more clusters is starting to decrease.

## 5. Advantages and Disadvantages of the Algorithm

**Advantages:**

*   Relatively simple and efficient, easy to understand and implement.
*   Fast computation speed, especially for large datasets.

**Disadvantages:**

*   Requires pre-specifying the number of clusters (K).
*   Sensitive to the choice of initial centroids.
*   Susceptible to the influence of outliers.
*   Not suitable for non-spherical clusters or clusters with significant size differences.
*   May converge to a local optimum instead of the global optimum.

## 6. Conclusion

K-means is a popular clustering algorithm that partitions data into K clusters through iterative assignment of data points and centroid updates. Evaluating the K-means algorithm's clustering performance is crucial and can be done by using metrics like Inertia, especially with the Elbow method. Understanding the principles, advantages, disadvantages, and evaluation methods of the K-means algorithm is essential for data analysis and machine learning applications.


