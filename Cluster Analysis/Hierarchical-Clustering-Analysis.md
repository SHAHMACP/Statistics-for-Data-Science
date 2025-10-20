# Hierarchical-Clustering-Analysis/


**Hierarchical Cluster Analysis (HCA)** is an **unsupervised learning technique** that groups data into a hierarchy of clusters.  
Unlike partitioning methods such as K-Means, HCA **does not require specifying the number of clusters (k)** in advance.

---

## Definition

Hierarchical clustering is a method of cluster analysis that seeks to build a hierarchy of clusters by either:
- **Agglomerative (bottom-up)** merging of smaller clusters, or
- **Divisive (top-down)** splitting of larger clusters.

Clusters are formed based on **distance or similarity** between data points.

Represented using a **dendrogram**:
A dendrogram is like a family tree for clusters. It shows how individual data points or groups of data merge together.

---

## Steps in Hierarchical Clustering

1. Compute the **distance matrix** between all pairs of objects.
2. Each object starts as a **single cluster**.
3. Merge the **two closest clusters** based on a chosen **linkage criterion**.
4. Update the distance matrix to reflect the new merged cluster.
5. Repeat steps 3–4 until all objects are grouped into a single cluster.

---

## Approaches of HCA

| Approach | Description | Method |
|-----------|--------------|---------|
| **Agglomerative (Bottom-Up)** | Start with each point as a single cluster and recursively merge the nearest clusters until one cluster remains. | **AGNES (Agglomerative Nesting)** |
| **Divisive (Top-Down)** | Start with all data points in a single cluster and recursively divide it into smaller clusters. | **DIANA (Divisive Analysis)** |
<img width="660" height="360" alt="image" src="https://github.com/user-attachments/assets/7f03c7ca-b580-4f5f-9ccd-9c096949b880" />

---

## Types of Linkage Methods

Linkage defines how the distance between two clusters is computed.

| Method | Description | Formula |
|---------|--------------|----------|
| **Single Linkage (Nearest Neighbor)** | Minimum distance between any two points in two clusters. | $D(C_1, C_2) = \min_{i \in C_1, j \in C_2} d(i, j)$ |
| **Complete Linkage (Farthest Neighbor)** | Maximum distance between any two points in two clusters. | $D(C_1, C_2) = \max_{i \in C_1, j \in C_2} d(i, j)$ |
| **Average Linkage** | Average distance between all points in the two clusters. | $D(C_1, C_2) = \frac{1}{|C_1||C_2|}\sum_{i\in C_1}\sum_{j\in C_2} d(i,j)$ |

![image](https://github.com/user-attachments/assets/a3f77b15-c862-4ee9-ad5e-e9d9e767f5b1)

---


## 🧮 7. Example Problem – Complete Linkage

### Distance Matrix

|   | P1 | P2 | P3 | P4 | P5 |
|:-:|---:|---:|---:|---:|---:|
| **P1** | 0 |   |   |   |   |
| **P2** | 9 | 0 |   |   |   |
| **P3** | 3 | 7 | 0 |   |   |
| **P4** | 5 | 6 | 8 | 0 |   |
| **P5** | 10 | 12 | 2 | 9 | 0 |

Perform clustering using **Complete Linkage Method**.

### Step-by-Step:

1. Identify the smallest distance → 2 (P3, P5).  
   Merge (P3, P5) into one cluster.

2. Recalculate the distance of this new cluster to others using **maximum** (since complete linkage).

3. Continue merging clusters with smallest maximum distances until all points belong to one cluster.

📺 **Reference Video:** [Complete Linkage HCA Example](https://www.youtube.com/watch?v=JeY9P-Vw9hg)

---

## 🌿 8. Dendrogram Representation

A **dendrogram** visually represents how clusters merge.

- **X-axis:** Data points  
- **Y-axis:** Distance (or dissimilarity) at which clusters are combined  

```python
import matplotlib.pyplot as plt
from scipy.cluster.hierarchy import linkage, dendrogram
import numpy as np

X = np.array([[2,6],[3,4],[6,8],[7,10],[5,8],[4,7]])

Z = linkage(X, method='complete')

plt.figure(figsize=(7,5))
dendrogram(Z)
plt.title('Hierarchical Clustering Dendrogram (Complete Linkage)')
plt.xlabel('Data Points')
plt.ylabel('Distance')
plt.show()
````

---

## 🧠 9. Advantages of Hierarchical Clustering

* No need to specify number of clusters (k) in advance.
* Produces a **hierarchical structure** that’s easy to interpret.
* Works well with small datasets and **non-spherical** clusters.
* **Flexible distance metrics** supported.

---

## ⚠️ 10. Disadvantages of Hierarchical Clustering

* **Computationally expensive** (O(n³) time complexity).
* **Not scalable** to very large datasets.
* **Sensitive to noise/outliers**.
* **Irreversible:** Once clusters are merged, they can’t be undone.

---

## Applications

| Domain               | Application                             |
| -------------------- | --------------------------------------- |
| **Marketing**        | Customer segmentation                   |
| **Healthcare**       | Grouping patients with similar symptoms |
| **Education**        | Grouping students based on performance  |
| **Image Processing** | Identifying similar image regions       |
| **Finance**          | Portfolio or stock grouping             |

---

## Comparison – HCA vs K-Means

| Feature            | Hierarchical Clustering | K-Means Clustering        |
| ------------------ | ----------------------- | ------------------------- |
| Cluster type       | Hierarchical            | Flat                      |
| Number of clusters | Not needed initially    | Must specify (k)          |
| Scalability        | Low                     | High                      |
| Output             | Dendrogram              | Centroids                 |
| Determinism        | Deterministic           | Depends on initialization |

---
