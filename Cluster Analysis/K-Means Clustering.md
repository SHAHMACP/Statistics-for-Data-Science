# K-Means Clustering

**K-Means Clustering** is a **partitioning-based unsupervised learning algorithm** used to group data points into *k* clusters based on feature similarity.  
Each cluster is represented by its **centroid**, which is the mean position of all the points in that cluster.


## Definition

K-Means clustering aims to divide *n* observations into *k* clusters such that each observation belongs to the cluster with the **nearest mean (centroid)**.

> **Objective:** Minimize the total intra-cluster distance (compactness of clusters).

---

## Algorithm Steps

1. **Initialize** the number of clusters *k*.  
2. **Select k initial centroids** randomly from the dataset.  
3. Calculate the **distance** between each data point and each cluster centroid.
4. **Assign each point** to the nearest centroid (based on Euclidean distance) for which the distance is minimum.  
5. **Recalculate each centroid** as the mean of all points assigned to each cluster.  
6. **Repeat** steps 3–5 until:
   - Centroids no longer move, or  
   - No reassignment of data points happened.

---

## Objective Function

The K-Means algorithm minimizes the **Within-Cluster Sum of Squares (WCSS)**:

$$
J = \sum_{i=1}^{k} \sum_{x \in C_i} ||x - \mu_i||^2
$$

where:
- $C_i$ → cluster i  
- $\mu_i$ → centroid of cluster i  
- $||x - \mu_i||^2$ → squared distance between data point and centroid  

---

## Distance Measure

The most common distance metric used in K-Means is the **Euclidean distance**:

$$
d(x, y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}
$$

---

## Properties of K-Means

| Property | Description |
|-----------|--------------|
| **Type** | Partitioning, Unsupervised Learning |
| **Shape of clusters** | Spherical / Convex |
| **Cluster representation** | By centroids (mean of points) |
| **Objective** | Minimize within-cluster variance |
| **Output** | Cluster labels and centroids |
| **Scalability** | Efficient for medium to large datasets |
| **Distance metric** | Usually Euclidean distance |

---

## Advantages

- Simple and easy to implement  
- Scales well with large datasets  
- Works well with well-separated spherical clusters  
- Produces easily interpretable results  

---

## Limitations

- Must predefine the number of clusters k 
- Sensitive to initial centroid positions  
- Struggles with non-spherical or unequal-sized clusters  
- Sensitive to outliers and noise  

---

## Improving K-Means Results

1. **Optimal k selection:**  Use the **Elbow Method** or **Silhouette Score** to find the right number of clusters.  

2. **Multiple initializations:**  Run K-Means multiple times with different random centroids and choose the lowest error.  

3. **Data normalization:**  Standardize features before clustering to avoid bias due to scale differences.  

4. **Outlier handling:**  Detect and remove outliers that can distort cluster centers.  

5. **Dimensionality reduction:**  Use **PCA** to improve performance on high-dimensional data.

---

## Methods to Find Optimal Number of Clusters (k)

### **a. Elbow Method**
Plot *k* vs. WCSS and choose the “elbow point” where the decrease slows down.
![image](https://github.com/user-attachments/assets/799c1b7a-48ba-4563-a5a2-d959976871b3)

### **b. Silhouette Score**
Measures how well each point fits within its cluster.  
Range: `-1 to +1`  
Higher values indicate better clustering.

---

## Interpreting K-Means Clusters

- **Centroids:** Represent the “average” feature values in each cluster.  
- **Feature Comparison:** Compare centroid values to understand what defines each cluster.  
- **Visualization:** Scatter plots, bar plots, and 3D visualizations help interpret results.

---

## Example

 ### Problem 1

 Use K-Means clustering algorithm to divide the following data into two clusters
  |  X |  Y |
| -: | -: |
|  1 |  1 |
|  2 |  1 |
|  2 |  3 |
|  3 |  2 |
|  4 |  3 |
|5   |  5 |

> **Given points:** (1,1), (2,1), (2,3), (3,2), (4,3), (5,5)

Let **k = 2**.

#### Initial centroids:

* **C1 = (2,1)**
* **C2 = (2,3)**

#### Compute Distances (Iteration 1)

Use **Euclidean Distance Formula:**

$$
d(x,y) = \sqrt{(x_1 - y_1)^2 + (x_2 - y_2)^2}
$$

| Point | (x, y) | d(C1) | d(C2) | Assigned Cluster |
| :---- | :----- | ----: | ----: | :--------------: |
| P1    | (1,1)  |  1.00 |  2.24 |      **C1**      |
| P2    | (2,1)  |  0.00 |  2.00 |      **C1**      |
| P3    | (2,3)  |  2.00 |  0.00 |      **C2**      |
| P4    | (3,2)  |  1.41 |  1.41 |      **C1**      |
| P5    | (4,3)  |  2.83 |  2.00 |      **C2**      |
| P6    | (5,5)  |  5.00 |  3.61 |      **C2**      |


#### **Clusters After Iteration 1**

* **Cluster 1 (C1):** P1(1,1), P2(2,1), P4(3,2)
* **Cluster 2 (C2):** P3(2,3), P5(4,3), P6(5,5)

#### Compute New Centroids

$$
\text{Centroid} = \left(\frac{\sum x}{n}, \frac{\sum y}{n}\right)
$$


* $$C1= \frac{1}{3} ((1,1)+ (2,1)+ (3,2))=  (2.0, 1.33) $$
* $$C2=\frac{1}{3} ( (2,3)+ (4,3)+ (5,5))=   (3.67, 3.67)   $$

#### Recalculate Distances (Iteration 2)

| Point | (x, y) | d(C1:2.0,1.33) | d(C2:3.67, 3.67) | Assigned Cluster |
| :---- | :----- | -------------: | ------------: | :--------------: |
| P1    | (1,1)  |           1.05 |          3.78 |      **C1**      |
| P2    | (2,1)  |           0.33 |          3.15 |      **C1**      |
| P3    | (2,3)  |           1.67 |          1.8 |      **C1**      |
| P4    | (3,2)  |           1.204 |          1.8|      **C1**      |
| P5    | (4,3)  |           2.605 |          0.75 |      **C2**      |
| P6    | (5,5)  |           4.74 |          1.88 |      **C2**      |

#### **Clusters After Iteration 2**

* **Cluster 1 (C1):** P1(1,1), P2(2,1),P3(2,3), P4(3,2)
* **Cluster 2 (C2):** P5(4,3), P6(5,5)

#### Compute New Centroids


* $$C1= \frac{1}{4} ((1,1)+ (2,1)+(2,3)+ (3,2))=  (2.0, 1.75) $$
* $$C2=\frac{1}{2} ((4,3)+ (5,5))=   (4.5, 4)   $$

#### Recalculate Distances (Iteration 3)

| Point | (x, y) | d(C1:2.0,1.75) | d(C2:4.5, 4) | Assigned Cluster |
| :---- | :----- | -------------: | ------------: | :--------------: |
| P1    | (1,1)  |           1.25 |          4.61 |      **C1**      |
| P2    | (2,1)  |           0.75 |          3.9 |      **C1**      |
| P3    | (2,3)  |           1.25 |          2.69 |      **C1**      |
| P4    | (3,2)  |           1.03 |          2.5|      **C1**      |
| P5    | (4,3)  |           2.36 |          1.12 |      **C2**      |
| P6    | (5,5)  |           4.42 |          1.12 |      **C2**      |

#### **Clusters After Iteration 3**

* **Cluster 1 (C1):** P1(1,1), P2(2,1),P3(2,3), P4(3,2)
* **Cluster 2 (C2):** P5(4,3), P6(5,5)
  
✅ No change in cluster assignments → **Algorithm converged.**

---

