# **Cluster Analysis**

**Cluster Analysis** is a statistical technique used to group a set of similar objects into clusters such that:

* Objects within the same cluster are **highly similar** (high intra-cluster similarity), and
* Objects in different clusters are **dissimilar** (low inter-cluster similarity).

It is one of the primary methods in **unsupervised learning**, where the goal is to discover patterns or structures within unlabeled data.

<img width="312" height="162" alt="image" src="https://github.com/user-attachments/assets/83a17911-b932-480c-8e0d-f87b214fd380" />

Clustering is a fundamental step in data mining, pattern recognition, and machine learning.
It helps identify hidden relationships in data by dividing it into meaningful subgroups (clusters) based on similarity.

* Each cluster represents a group of data points sharing common characteristics.
* Clustering can be used for exploratory data analysis, summarization, anomaly detection, and more.

Example: Grouping customers by purchasing behavior, documents by topic, or genes by expression patterns.

## Dunn Index

Dunn index is the ratio of the minimum of inter-cluster distances and maximum of intracluster distances. 
The more the value of the Dunn index, the better the clusters will be.
![image](https://github.com/user-attachments/assets/c25f5868-6cd0-446a-beec-5ba8242e142d)

| Type                         | Description                                              | Goal               |
| ---------------------------- | -------------------------------------------------------- | ------------------ |
| **Intra-Cluster Similarity** | Similarity among objects **within** the same cluster.    | Should be **high** |
| **Inter-Cluster Similarity** | Similarity among objects **between** different clusters. | Should be **low**  |

Thus, a good clustering method aims to:

* Maximize intra-cluster similarity
* Minimize inter-cluster similarity


---


## **Advantages of Cluster Analysis**

* **No need for labeled data:** Works without predefined class labels.
* **Reveals hidden structures:** Finds natural groupings in data.
* **Flexible:** Can be applied to various data types and domains.
* **Preprocessing support:** Useful for summarizing data before classification or visualization.

---

## **Applications of Cluster Analysis**

* **Market Segmentation**: Businesses use cluster analysis to group customers based on behavior, preferences, demographics, or purchasing patterns. This helps in creating targeted marketing strategies and personalized product offerings.
* **Image Segmentation**: In computer vision, clustering is used to identify regions within images for tasks like object recognition, medical imaging (e.g., tumor detection), or face detection.
* **Fraud Detection**: Banks and financial institutions use cluster analysis to identify unusual transactions that may indicate fraud. By detecting outliers or abnormal patterns, they can flag potential fraud cases.
* **Social Network Analysis**: Clustering is used to analyze relationships and communities within social networks, grouping individuals or entities based on similar interests, connections, or communication patterns.
* **Document Classification**: In text mining, cluster analysis helps group similar documents or articles. This is useful in organizing large sets of unstructured data like research papers, news articles, or customer feedback.
* **Biological Data Analysis**: In genomics and bioinformatics, clustering helps identify groups of genes or proteins with similar functions, aiding in the study of diseases, genetic traits, or drug responses.
* **City Planning**: Governments and urban planners use clustering to identify regions with similar population densities, traffic patterns, or economic activities, helping in efficient resource allocation and urban development.
* **Recommender Systems**: E-commerce and streaming platforms use clustering to group users based on their behavior (like purchases or viewing history), providing personalized recommendations.

---

## **Types of Clustering Methods**
<img width="1447" height="1071" alt="image" src="https://github.com/user-attachments/assets/b7180539-e39f-4c06-a067-4065ac944ee9" />


| Type                         | Description                                                                             | Examples                                          |
| ---------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------- |
| **Hierarchical Clustering**  | Builds a hierarchy of clusters by successively merging or splitting clusters. It can be visualized as a tree. No need to specify the number of clusters in advance         | Agglomerative, Divisive |
| **Partitioning Clustering**  | Divides data into a fixed number of non-overlapping clusters. Construct various partitions and then evaluate them by some criterion. The number of clusters should be defined beforehand. The algorithm typically tries to minimize the distance between data points and their corresponding cluster centers.                     | K-Means, K-Medoids                                |
| **Density-Based Clustering** | Forms clusters based on regions of high density separated by low-density areas.         | DBSCAN, OPTICS                                    |
| **Overlapping Clustering**   | Data points can belong to more than one cluster. It allows more flexible grouping where points can have partial membership to different clusters.         | Gaussian Mixture Models (GMM)  , Fuzzy C means                   |   

---
## **Common Distance Metrics**
- **Euclidean Distance** :  $d(x, y) = \sqrt{\sum_i (x_i - y_i)^2} =  \sqrt{ (x_1 - y_1)^2+ (x_2 - y_2)^2+...(x_n - y_n)^2}$
- **Manhattan Distance** : $d(x, y) = \sum_i| x_i - y_i| = | x_1 - y_1|+| x_2 - y_2|+...+| x_n - y_n|$
- **Minkowski Distance** : $d(x, y) = (\sum_i| x_i - y_i| ^p)^{1/p}$
- **Chebyshev Maximum Distance** : $d(x, y) = max(| x_i - y_i|) = max(| x_1 - y_1|,| x_2 - y_2|,...,| x_n - y_n|)$ 

---

## **Overlapping vs Non-Overlapping Clustering**

### **Overlapping Clustering**

* Allows data points to belong to multiple clusters simultaneously.
* Unlike traditional clustering methods, where each data point is assigned to a single cluster, overlapping clustering recognizes that many real-world data points may naturally fit into more than one category.
* This approach is particularly useful in scenarios where categories are not mutually exclusive

  #### Example:
  In a movie recommendation system, consider four users with varying preferences for genres: User 1 enjoys Action (70%) and Comedy (30%), User 2 prefers Action (60%) and Drama (40%), User 3 likes Comedy (50%) and Drama (50%), while User 4 exclusively enjoys Action (80%).
Using overlapping clustering, such as Fuzzy C-Means, we can assign users to multiple genres. For instance, User 1 belongs primarily to the Action cluster but also partially to the Comedy cluster. This approach allows the system to recommend movies that cater to each user's diverse interests across multiple genres, rather than restricting them to a single category 

#### Features
1. Partial Membership: Each data point can belong to multiple clusters with different degrees of membership.
   
2. Flexibility: It allows for a more realistic representation of complex datasets, accommodating ambiguity and shared characteristics.

3. Use Cases: Ideal for applications such as social network analysis, recommendation systems, and text categorization.

#### Common Algorithms
##### **(1) Fuzzy C-Means** (FCM):
* Fuzzy C-Means is one of the most widely used overlapping clustering methods.
* Instead of assigning each data point to one cluster, it assigns a degree of membership to each data point for every cluster.
* Each data point has a membership value between 0 and 1, representing its degree of belonging to each cluster.

##### **(2) Probabilistic Clustering** (Gaussian Mixture Models - GMM):

* In GMM, each cluster is modeled as a Gaussian distribution, and the probability that a data point belongs to a particular cluster is calculated.
* Data points can belong to multiple clusters with different probabilities
  
### **Non-Overlapping (Exclusive / Partitioning) Clustering** 

Each object belongs to exactly one cluster. Each data point belongs to one cluster only and the objective is to optimize the placement of points in these clusters based on some criteria, typically minimizing the distance between the points and their respective cluster centroids.

#### Features

* **Fixed Number of Clusters**: The user must specify the number of clusters (k) in advance.
* **Non-overlapping Clusters**: Each data point is assigned to one cluster only.
* **Iterative Process**: The algorithms often involve iterations to refine the clusters based on distances.
* **Simplicity**: Easy to understand and implement.
* **Speed**: Generally faster than hierarchical methods, especially for large datasets.
* **Scalability**: Efficient for large datasets when using algorithms like K-Means.

  #### Common Algorithms

##### **(1) K-Means Clustering**:

* One of the most popular partitioning clustering methods.
* The algorithm randomly selects k initial centroids and assigns each data point to the nearest centroid.
* The centroids are then recalculated as the mean of the points in each cluster, and the process repeats until convergence.
* Suitable for large datasets but assumes clusters are spherical and equally sized.
* Example: In customer segmentation, K-Means might identify distinct groups of customers based on purchasing behavior, such as "frequent buyers," "occasional buyers," and "one-time buyers

##### **(2) K-Medoids Clustering**:

* Similar to K-Means, but instead of centroids, it uses actual data points (medoids) as the center of clusters.
* More robust to noise and outliers than K-Means.
* The algorithm iterates to find the medoids that minimize the total distance to all points in the cluster.

##### **(3) CLARA (Clustering LARge Applications)**:

* An extension of K-Medoids designed for larger datasets.
* It randomly samples a subset of data points to form medoids and applies K-Medoids to these samples.
* The clusters are then evaluated and refined based on the entire dataset.
