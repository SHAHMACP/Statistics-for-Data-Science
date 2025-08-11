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


#### Curse of Dimensionality

> The **curse of dimensionality** refers to various phenomena that arise when analyzing data in high-dimensional spaces. As the number of features increases, data becomes **sparse**, making it difficult to find meaningful patterns, **Model performance** can degrade due to overfitting and increased computational cost, and **Visualization becomes impossible** beyond 3 dimensions.

Absolutely! Here’s another **simple, relatable example** that makes **PCA** easier to understand for students and readers of your GitHub repo. It complements your “height and weight” example, and can be used as a second introduction or analogy.

#### Feature Selection vs Feature Extraction

| Feature Selection                                             | Feature Extraction                                           |
| ------------------------------------------------------------- | ------------------------------------------------------------ |
| Selecting a **subset** of the original features               | Creating **new features** from combinations of original ones |
| Original meaning of features is preserved                     | New features may not have intuitive meaning                  |
| Examples: Removing low variance or highly correlated features | Examples: PCA, LDA                             |

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

## Principal Component

A **Principal Component (PC)** is a **new feature** (or axis/direction) formed by a **linear combination of original features**, such that:

* It **captures the maximum possible variance** in the data.
* Each component is **uncorrelated** (orthogonal) to the previous ones.
* It’s **ordered**: PC1 captures the most variance, PC2 the next most, and so on.


> A **Principal Component** is like a **new perspective** from which your data makes the most sense — where the differences between the points are most noticeable.


### Geometric Intuition:

Imagine a cloud of points in 2D. The direction along which these points are **most spread out** is the **first principal component (PC1)**. The **second principal component (PC2)** is the direction that is **perpendicular** to PC1 captures the **next highest variance** in the data. These new axes (PC1, PC2, ...) form a new **coordinate system** for your data.



### Properties of Principal Components:

| Property   | Description                                           |
| ---------- | ----------------------------------------------------- |
| Orthogonal | All PCs are at 90° to each other (uncorrelated)       |
| Ranked     | PC1 > PC2 > PC3 … in terms of variance captured       |
| Linear     | Each PC is a linear combination of original variables |
| Compact    | Often, a few PCs explain most of the variance         |

---

### Advantages of PCA

| Advantage                       | Description                                                                                      |
| ------------------------------- | ------------------------------------------------------------------------------------------------ |
|  **Easy Computation**         | PCA is computationally easy to solve by computers.                |
|  **Faster Computation**       | With fewer features, machine learning models train and run faster. It speeds up machine learning algorithms.|
|  **Noise Reduction**          | Eliminates irrelevant or redundant features that may cause overfitting.                          |
|  **Data Visualization**       | Allows high-dimensional data to be visualized in 2D or 3D by using the top principal components. |


###  Disadvantages of PCA

| Disadvantage                    | Description                                                                                        |
| ------------------------------- | -------------------------------------------------------------------------------------------------- |
|  **Loss of Interpretability** | New features (principal components) are linear combinations — they don’t carry real-world meaning. |
|  **Assumes Linearity**        | Cannot capture non-linear patterns in data (unlike techniques like t-SNE or Kernel PCA).           |
|  **The Trade-off between Information Loss and Dimensionality Reduction**| If you drop too many components, some important information may be lost. Balancing the trade-off between information loss and dimensionality reduction is unfortunately a necessary compromise that we have to make when using PCA.|

---

### Properties of PCA

| Property                     | Description                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------- |
| **Orthogonality**         | All principal components are mutually orthogonal (uncorrelated).              |
|  **Ordered Variance**      | PC1 > PC2 > PC3 in terms of the variance they capture.                        |
|  **Linear Transformation** | PCA projects data linearly onto a new set of axes.                            |
| **Variance-Based**        | Selection of principal components is based on how much variance they explain. |
| **Basis Vectors**         | The principal components form a new basis for the data space.                 |

---

### Applications of PCA

| Field                    | Application                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------ |
|  **Image Compression** | Reduce the number of pixels while retaining important visual information.            |
|  **Genomics**          | Reduce thousands of gene features to key principal components for disease detection. |
|  **Neuroscience**      | Simplify EEG/fMRI data for pattern analysis and brain activity detection.            |
|  **Finance**           | Reduce correlated stock market indicators into a few principal trends.               |
|  **Medical Diagnosis** | Simplify large diagnostic datasets (e.g., cancer, diabetes) for prediction.          |
|  **Signal Processing** | Remove noise and detect meaningful signals in audio and sensor data.                 |
|  **Chemometrics**      | Analyze chemical mixtures or reactions using spectrometry data.                      |

---

### Limitations of PCA

| Limitation                          | Description                                                                         |
| ----------------------------------- | ----------------------------------------------------------------------------------- |
|  **Linear Only**                  | Cannot model nonlinear patterns — Kernel PCA or t-SNE are better for that.          |
|  **Feature Interpretability**     | Principal components often lack clear interpretation or naming.                     |
|  **Correlation between features**     | PCA assumes some correlation between the features. If not, PCA will be unable to determine the principal component.                     |
|  **Sensitive to Feature Scaling** | Without standardization, features with larger magnitudes dominate PCA (For a house price prediction, house size might range from 1,000 to 10,000 square feet and number of bedrooms might range from 1 to 5. Without scaling, a machine learning model might give far more importance to the difference of 100 square feet than to the difference of one bedroom, even though the number of bedrooms is often a more critical factor in determining a house's value or classification. ).            |
|  **No Class Awareness**           | PCA is unsupervised — it doesn’t consider target/output labels.                     |
|  **Not robust to outliers**                  | The algorithm will be biased in datasets with strong outliers. Should remove outliers before PCA. |
|  **No missing values**                  | Technical implementation often assumes no missing values present in the feature sets. |

---



