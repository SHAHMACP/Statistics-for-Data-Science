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

Absolutely! Here’s another **simple, relatable example** that makes **PCA** easier to understand for students and readers of your GitHub repo. It complements your “height and weight” example, and can be used as a second introduction or analogy.

---

### Simple PCA Example: Fruit Size and Sweetness

Imagine you have a dataset of fruits with two features:

* **Size** (in cm)
* **Sweetness** (measured on a scale from 1 to 10)

Each fruit is a point on a 2D graph (Size vs Sweetness).
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/01662b02-6d7e-4938-96f4-7c3f77a123b0" />


Let’s say you want to classify or compare these fruits, but you're limited to only **one feature**.

You might think: "Just use size!" or "only use sweetness!"..

But both features are important. Just like some fruits might be big but not very sweet or others might be small but extremely sweet. 
If you drop one of these features, you lose important details

Instead of choosing one feature and discarding the other, PCA helps you:

* Create a **new axis** that’s a combination of size and sweetness
* This new axis points in the direction of **maximum variance**
* When you project the data onto this new axis, you get a **1D representation** that still captures most of the differences among the fruits <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/d157ed16-d883-46dd-883d-b8d934d402a1" />


---

#### Feature Selection vs Feature Extraction**

| Feature Selection                                             | Feature Extraction                                           |
| ------------------------------------------------------------- | ------------------------------------------------------------ |
| Selecting a **subset** of the original features               | Creating **new features** from combinations of original ones |
| Original meaning of features is preserved                     | New features may not have intuitive meaning                  |
| Examples: Removing low variance or highly correlated features | Examples: PCA, LDA                             |


---



