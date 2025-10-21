# Hierarchical-Clustering-Analysis


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


#####  **Start** with *5* clusters, each containing one data point (singleton). **Given Distance Matrix**

|        | {P1} | {P2} | {P3} | {P4} | {P5} |
| :----: | -: | -: | -: | -: | -: |
| {**P1**} |  0 |  9 |  3 |  6 | 11 |
| {**P2**} |  9 |  0 |  7 |  5 | 10 |
| {**P3**} |  3 |  7 |  0 |  9 |  2 |
| {**P4**} |  6 |  5 |  9 |  0 |  8 |
| {**P5**} | 11 | 10 |  2 |  8 |  0 |


##### Step 1 — Identify the smallest distance

We look for the **minimum non-zero value** in the matrix.

* Minimum = **2**, between **P3 and P5**.

**Merge C1 = {P3, P5}**


##### Step 2 — Recompute the distance matrix

Since we are using **Complete Linkage**, the new distance between a merged cluster and another cluster is the **maximum** of pairwise distances.

$$
D(C_{new}, X) = \max(D(P3,X), D(P5,X))
$$

* $d({P3, P5},P1)=max({d(P3,P1),d(P5,P1)})=max(3,11)=11$
* $d({P3, P5},P2)=max({d(P3,P2),d(P5,P2)})=max(7,10)=10$
* $d({P3, P5},P4)=max({d(P3,P4),d(P5,P4)})=max(9,8)=9$

So the new distance matrix becomes:

|             | {P1} | {P2} | {P4} | {P3,P5} |
| :---------: | -: | -: | -: | ------: |
|    {**P1**}   |  0 |  9 |  6 |      11 |
|    {**P2** }  |  9 |  0 |  5 |      10 |
|    {**P4**}   |  6 |  5 |  0 |       9 |
| {**P3,P5**} | 11 | 10 |  9 |       0 |


##### Step 3 — Find the next minimum distance

From the updated matrix,
the smallest value = **5**, between **P2 and P4**.

**Merge C2 = {P2, P4}**


##### Step 4 — Recompute the distance matrix again

Now clusters are:

* **C1 = {P3,P5}**
* **C2 = {P2,P4}**
* **P1**

We update distances using **maximum distance rule** (complete linkage).

* $d({P2,P4},P1)=max({d(P2,P1),d(P4,P1)})=max({9,6})=9$
* $d({P2,P4},{P3,P5})=max({d(P2,{P3,P5}),d(P4,{P3,P5})})=max({d(P3,P2),d(P5,P2),d(P3,P4),d(P5,P4)}=max{7,10,9,8})=10$


|             | P1 | (P2,P4) | (P3,P5) |
| :---------: | -: | ------: | ------: |
|    **P1**   |  0 |       9 |      11 |
| **(P2,P4)** |  9 |       0 |      10 |
| **(P3,P5)** | 11 |      10 |       0 |


##### Step 5 — Find the next smallest distance

The smallest distance now is **9**, between **P1 and (P2,P4)**.

**Merge C3 = {P1, P2, P4}**


##### Step 6 — Recompute distance matrix

Clusters now:

* **C1 = {P3,P5}**
* **C3 = {P1,P2,P4}**

Compute the distance between the two clusters using the **maximum** pairwise distance.

* $d({P1,P2,P4},{P3,P5})=max({d(P1,{P3,P5}),d({P2,P4},{P3,P5})})=max({d(P3,P1),d(P1,P5),d(P3,P2),d(P2,P5),d(P3,P4),d(P5,P4)})= \max(3, 7, 9, 11, 10, 8) = 11$

So the final merge distance = **11**.


#### Step 7 — Construct the Dendrogram

| Merge Step | Clusters Merged      | Distance (Level) |
| ---------- | -------------------- | ---------------- |
| 1          | (P3, P5)             | 2                |
| 2          | (P2, P4)             | 5                |
| 3          | (P1, P2, P4)         | 9                |
| 4          | (P1, P2, P3, P4, P5) | 11               |

---


##### **Final Results**

* **Number of iterations:** 4
* **Final cluster formed at distance = 11**
* **Final 2 clusters before full merge:**

  * **Cluster A:** {P1, P2, P4}
  * **Cluster B:** {P3, P5}



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
