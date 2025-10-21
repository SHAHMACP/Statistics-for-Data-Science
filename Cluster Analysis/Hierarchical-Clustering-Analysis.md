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

## **Algorithm 1: Agglomerative Hierarchical Clustering (AGNES)**

Agglomerative Hierarchical Clustering (also known as **AGNES**-Agglomerative Nesting ) is a **bottom-up** approach:
Each data point starts as its own cluster, and clusters are **iteratively merged** based on similarity (or distance) until one single cluster remains.


### **Algorithm Steps**

1. **Start** with *n* clusters, each containing one data point (singleton). 
2. **Compute** the pairwise **distance matrix** between all clusters.
3. **Find** the two clusters with the **minimum distance** (most similar).
4. **Merge** these two clusters into one new cluster.
5. Compute the distance between the new cluster and each of the old clusters.
6. **Update** the distance matrix to reflect the new distances between clusters, using a chosen **linkage method**:

   * *Single linkage:* minimum distance
   * *Complete linkage:* maximum distance
   * *Average linkage:* mean distance
7. **Repeat** steps 3–5 until all points are merged into a single cluster.
8. The process can be visualized as a **dendrogram**, showing how clusters are merged step by step.

---

## **Algorithm 2: Divisive Hierarchical Clustering (DIANA)**

Divisive Hierarchical Clustering (also known as **DIANA**-Divisive Analysis) is a **top-down** approach:
Start with **one large cluster** containing all data points, and then **split** clusters recursively into smaller clusters until each data point stands alone.


### **Algorithm Steps**

1. **Start** with all data points in one cluster.
2. **Compute** the dissimilarity (distance) between all objects in the cluster.
3. **Find** the most dissimilar object — the point farthest from all others.
4. **Use** this object as the **seed** of a new cluster.
5. **Assign** each remaining point to one of the two clusters:

   * If it is **closer to the seed**, move it to the new cluster.
   * Otherwise, keep it in the existing cluster.
6. **Recalculate** dissimilarities within each cluster.
7. **Select** the cluster with the **largest average dissimilarity** and **repeat the split**.
8. **Continue** until every data point forms its own cluster or until the desired number of clusters is reached.

---


## Types of Linkage Methods

Linkage defines how the distance between two clusters is computed.

| Method | Description | Formula |
|---------|--------------|----------|
| **Single Linkage (Nearest Neighbor)** | Minimum distance between any two points in two clusters. | $D(C_1, C_2) = \min_{i \in C_1, j \in C_2} d(i, j)$ |
| **Complete Linkage (Farthest Neighbor)** | Maximum distance between any two points in two clusters. | $D(C_1, C_2) = \max_{i \in C_1, j \in C_2} d(i, j)$ |
| **Average Linkage** | Average distance between all points in the two clusters. |  |

![image](https://github.com/user-attachments/assets/a3f77b15-c862-4ee9-ad5e-e9d9e767f5b1)

---


## Example 

### Problem 1 

Distance Matrix

|   | P1 | P2 | P3 | P4 | P5 |
|:-:|---:|---:|---:|---:|---:|
| **P1** | 0 |   |   |   |   |
| **P2** | 9 | 0 |   |   |   |
| **P3** | 3 | 7 | 0 |   |   |
| **P4** | 6 | 5 | 9 | 0 |   |
| **P5** | 11 | 10 | 2 | 8 | 0 |

Perform clustering using **Complete and single Linkage Method**.

### Step-by-Step:



📺 **Reference Video:** [Complete Linkage HCA Example](https://www.youtube.com/watch?v=JeY9P-Vw9hg)



---

## Advantages of Hierarchical Clustering

* No need to specify number of clusters (k) in advance.
* Produces a **hierarchical structure** that’s easy to interpret.
* Works well with small datasets and **non-spherical** clusters.
* **Flexible distance metrics** supported.

---

## Disadvantages of Hierarchical Clustering

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
| Cluster type       | Different partiitions   | Single partition          |
| Number of clusters | Not needed initially    | Must specify (k)          |
| Scalability        | Low                     | High                      |
| Output             | Dendrogram              | Centroids                 |
| Runtime Efficiency | Less                    | More                      |

---
