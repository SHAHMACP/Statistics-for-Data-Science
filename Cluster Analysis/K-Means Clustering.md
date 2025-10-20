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

1. **Optimal k selection:**  
   - Use the **Elbow Method** or **Silhouette Score** to find the right number of clusters.  

2. **Multiple initializations:**  
   - Run K-Means multiple times with different random centroids and choose the lowest error.  

3. **Data normalization:**  
   - Standardize features before clustering to avoid bias due to scale differences.  

4. **Outlier handling:**  
   - Detect and remove outliers that can distort cluster centers.  

5. **Dimensionality reduction:**  
   - Use **PCA** to improve performance on high-dimensional data.

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
