# Principal Component Analysis (PCA)

- Principal Component Analysis (PCA) is an **unsupervised machine learning** technique used for **dimensionality reduction**. 
- It transforms a dataset with potentially correlated features into a set of linearly uncorrelated features, called **principal components**, with the help of an orthogonal transformation.
- It is one of the popular tools that is used for Exploratory Data Analysis(EDA) and Predictive modeling.

---

## Why PCA?

- To reduce high-dimensional data to lower dimensions
- To **visualize** data in 2D or 3D
- To **remove noise** and redundant features
- To **speed up** machine learning models by reducing the number of input features
- To **reduce overfitting**

---

## Dimensionality Reduction

Dimensionality reduction is a crucial preprocessing step in data science and machine learning, especially when working with high-dimensional data. 
It refers to the process of reducing the number of input variables or features in a dataset while retaining as much relevant information as possible.

---

#### Curse of Dimensionality

> The **curse of dimensionality** refers to various phenomena that arise when analyzing data in high-dimensional spaces. As the number of features increases, data becomes **sparse**, making it difficult to find meaningful patterns, **Model performance** can degrade due to overfitting and increased computational cost, and **Visualization becomes impossible** beyond 3 dimensions.



---

#### Feature Selection vs Feature Extraction**

| Feature Selection                                             | Feature Extraction                                           |
| ------------------------------------------------------------- | ------------------------------------------------------------ |
| Selecting a **subset** of the original features               | Creating **new features** from combinations of original ones |
| Original meaning of features is preserved                     | New features may not have intuitive meaning                  |
| Examples: Removing low variance or highly correlated features | Examples: PCA, LDA                             |


---



