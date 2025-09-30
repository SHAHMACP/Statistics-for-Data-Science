# Factor Analysis

Factor Analysis is a statistical method used to simplify complex datasets by identifying patterns among observed variables.
It reduces many variables into fewer hidden factors (latent variables), showing how they are related.
The main idea is to group correlated variables together into underlying dimensions (factors).


## Latent Variables

Latent variables are variables that cannot be directly measured, but can be inferred from observed data.

They represent underlying constructs that influence the observed values.


### Examples:

* In psychology: "Intelligence" (latent) is measured using test scores (observed).
* In marketing: "Customer satisfaction" (latent) is inferred from survey responses (observed).
* In education: "Language ability" (latent) is inferred from essay, reading, vocabulary scores.



## Examples

#### Example 1 – Classroom

Math, Physics, Chemistry marks → Science Ability (latent factor).

Essay writing, Reading comprehension, Vocabulary → Language Ability (latent factor).


#### Example 2 – Restaurant Survey

Survey with 6 items: Taste, Presentation, Ambience, Cleanliness, Friendliness, Speed.
Factor Analysis result:

Factor 1 = Food Quality (Taste, Presentation)

Factor 2 = Service & Environment (Ambience, Cleanliness, Friendliness, Speed)



---

## Assumptions of Factor Analysis

1. No outliers – extreme values distort results.
2. Sufficient sample size – at least 5–10 observations per variable.
3. Interrelated variables – observed variables must be correlated.
4. Linearity – relationships among variables assumed linear.
5. Normality – ideally variables follow normal distribution.
6. Homogeneity of variance – variances should be roughly equal.
7. Measurement scale – interval or ratio scale preferred.


---

## Purpose of Factor Analysis

* Simplify data into fewer factors.
* Discover hidden patterns.
* Group similar variables together.
* Improve predictions.
* Help design and validate surveys/tests.
* Generate new insights about relationships.



---

## Types of Factor Analysis

### Exploratory Factor Analysis (EFA)

Used when we don’t know the number of factors.

Goal: Discover structure in data.


### Confirmatory Factor Analysis (CFA)

Used when we already know or hypothesize the factor structure.

Goal: Confirm if data fits the model.



---

## Factor Analysis Model

The general model:

$$X_i = \mu + \lambda_{i1}F_1 + \lambda_{i2}F_2 + \cdots + \lambda_{im}F_m + \epsilon_i$$

In matrix form,
$$X=\mu + \Lambda F + \epsilon $$

Where:

- $X: p * 1$ = vector of observed variables
- $\mu : p*1$ = vector of means of observed variables
- $\Lambda: p*m$ = matrix of factor loadings( p is the number of  observed  variables and m is the number of latent factors)
- $F: m*1$ = vector of common factors (latent)
- $\epsilon:p*1$ = vector of error terms (unique/error variance which are specific to each observed variable)


Factor Analysis Model is a statistical framework used to describe the relationships between observed variables and underlying latent factors. The model assumes that the observed variables are influenced by a smaller set of unobserved variables (factors), which explain the correlations among them.

---

## Model Assumptions

### Mean Assumptions

1. The specific factors (errors) are random and have mean zero: $$E(\epsilon_i) = 0, \quad i = 1,2,\dots,p$$

2. The common factors also have mean zero: $$E(F_j) = 0, \quad j = 1,2,\dots,m$$

3. The expected value of each observed variable is: $$E(X_i) = \mu_i$$


### Variance Assumptions

1. The common factors are standardized, with variance equal to 1: $$Var(F_j) = 1, \quad j = 1,2,\dots,m$$

2. The specific factors have variances: $$Var(\epsilon_i) = \psi_i, \quad i = 1,2,\dots,p$$
   Here, $\psi_i$ is called the **specific variance** of variable $i$.

3. The variance of the $i$th observed variable is: $$Var(X_i) = \sum_{j=1}^{m} \lambda_{ij}^2 + \psi_i$$

   * The term $$h_i^2 = \sum_{j=1}^{m} \lambda_{ij}^2$$
     is called the **communality** of variable $i$.
   * Larger communality → better representation of the variable by common factors.


### Correlation Assumptions

1. The common factors are uncorrelated with one another: $$Cov(F_j, F_k) = 0, \quad j \neq k$$

2. The specific factors are uncorrelated with one another: $$Cov(\epsilon_i, \epsilon_k) = 0, \quad i \neq k$$

3. The specific factors are uncorrelated with the common factors: $$Cov(\epsilon_i, F_j) = 0$$


### Covariance Structure of Observed Variables

1. Covariance between two observed variables $X_i$ and $X_k$: $$Cov(X_i, X_k) = \sum_{j=1}^{m} \lambda_{ij} \lambda_{kj}, \quad i \neq k$$

2. Covariance between an observed variable $X_i$ and a factor $F_j$: $$Cov(X_i, F_j) = \lambda_{ij}$$

3. In **matrix form**, the variance–covariance matrix of observed variables is: $$\Sigma = \Lambda \Lambda^\top + \Psi$$

Where

$$\Psi =\begin{bmatrix}
\psi_1 & 0 & \cdots & 0 \
0 & \psi_2 & \cdots & 0 \
\vdots & \vdots & \ddots & \vdots \
0 & 0 & \cdots & \psi_p
\end{bmatrix}
$$

---


## Important Terms

### Factor Loadings: 
● Higher factor loadings (closer to 1) indicate that the variable strongly relates to the factor, while lower loadings (closer to 0)
show a weaker relationship.

● Example: In a restaurant survey, if "Food Taste" has a factor loading of 0.8 on a "Food Quality" factor, it means "Food Taste" is
strongly associated with that factor.

### Eigenvalues: 
● Eigenvalues measure the amount of variance in the observed variables that a particular factor explains.

● Factors with larger eigenvalues explain more variance. Typically, factors with eigenvalues greater than 1 are considered
important.

### Factor Scores: 
● Factor scores are calculated values that estimate an individual's or an observation’s position on the identified
latent factors.

● Factor scores represent how much each individual scores on the underlying factors based on the observed
variables.

● Example: If a customer scores high on the "Food Quality" factor, it means they had a positive experience
related to food in a restaurant.



---


## Methods for Estimating Factor Scores from the Data

After extracting common factors in Factor Analysis, we may want to **estimate factor scores** (the values of the latent factors for each observation). Several methods exist for this estimation:



### 1. Regression Method

* Uses a **regression model** to predict factor scores based on factor loadings.
* Factor scores are a **linear combination of observed variables**, adjusted for loadings.

$$
\hat{F} = (\Lambda' \Sigma^{-1} \Lambda)^{-1} \Lambda' \Sigma^{-1} X
$$

Where:

* $\hat{F}$ = estimated factor score
* $\Lambda$ = factor loading matrix
* $\Sigma$ = covariance matrix of observed variables
* $X$ = observed data



### 2. Bartlett Method

* Minimizes the **error variance**.
* Produces factor scores that are **uncorrelated with the unique errors**.

$$
\hat{F} = (\Lambda' \Psi^{-1} \Lambda)^{-1} \Lambda' \Psi^{-1} X
$$

Where:

* $\Psi$ = diagonal matrix of unique variances (specific errors).


### 3. Anderson–Rubin Method

* Produces factor scores that are **standardized and orthogonal**.
* Ensures factor scores are **uncorrelated**, with **mean 0** and **variance 1**.
* Commonly used when independence between estimated factor scores is required.


### 4. Thurstone’s Method

* Transforms raw variables into standardized scores.
* Factor scores are then computed from these standardized values.
* Frequently used in **psychological research**.


### 5. Principal Component Analysis (PCA) Method

* PCA is not technically a factor score method, but often used in **Exploratory Factor Analysis (EFA)**.
* Component scores maximize the variance explained by each component.
* Scores are **linear combinations of observed variables**.

$$
Z = XW
$$

Where:

* $Z$ = matrix of principal component scores
* $X$ = observed variable matrix
* $W$ = weight matrix (eigenvectors of covariance matrix)


### 6. Maximum Likelihood Estimation (MLE)

* Estimates factor scores by **maximizing the likelihood** that the observed data fits the factor model.
* Attempts to find parameters (factor loadings, factor scores, unique variances) that best explain the data.

$$
L(\theta | X) = \prod_{i=1}^{n} f(X_i | \theta)
$$

Where:

* $L$ = likelihood function
* $\theta$ = parameters (factor loadings, scores, variances)
* $X_i$ = observed data for the $i^{th}$ individual

---

## Methods of Extracting Common Factors

### 1. Principal Component Analysis (PCA) – explains maximum variance :
  
   A technique to reduce the dimensionality of data by transforming original variables into a smaller set of uncorrelated components. PCA identifies components that explain the maximum variance in the data. It doesn’t differentiate between shared and unique variance.


### 2. Principal Axis Factoring (PAF) – focuses only on common variance:

   method to identify the underlying latent factors that explain the correlations among observed variables by focusing only on the shared variance
(common variance). CFA estimates factors that account for the variance shared among the observed variables, excluding the unique (error) variance.


### 3. Maximum Likelihood (ML) – model fitting with statistical tests:

   A statistical method used to estimate factor loadings and assess how well the model fits the data. MLE maximizes the likelihood that the factor model reproduces the observed data. It also provides statistical tests to
evaluate model fit and offers confidence intervals for factor estimates.


### 4. Image Factoring – based on partial correlations:

   A method that uses partial correlations to estimate factors, focusing on maximizing the amount of shared variance among variables. Image factoring extracts factors by analyzing the partial correlations among variables, grouping variables that have similar correlation patterns.


### 5. Other methods: Alpha factoring, ULS, GLS:
● Alpha Factoring: Focuses on maximizing the reliability (internal consistency) of the factors.

● Unweighted Least Squares (ULS): A simpler method that minimizes the difference between observed and
reproduced correlation matrices.

● Generalized Least Squares (GLS): Similar to ML but more computationally efficient for large samples.




---

## Determining Number of Factors

1. Eigenvalue Criterion (Kaiser’s Rule) – retain factors with eigenvalue > 1.

2. Scree Plot – look for the “elbow.”

3. Cumulative Variance Explained – keep enough factors to explain 70–80% variance.

4. Parallel Analysis – compare with random data eigenvalues.



---

## Transformation of Factor Analysis Solutions

In factor analysis, after extracting the initial factors, you often apply **transformations** to make the results easier to interpret.
These transformations help clarify the relationships between **factors** and **observed variables**.

The most common types of transformations are **rotation methods**.



### Two Types of Rotation Methods

#### 1. Orthogonal Rotation

* Keeps factors **uncorrelated (independent)** while making factor loadings easier to interpret.
* Each factor remains at right angles (**90°**) to one another.

**Types:**

* **Varimax**: Maximizes the variance of squared loadings for each factor.
  → Makes factors more interpretable, with each variable loading highly on only one factor.
* **Quartimax**: Minimizes the number of factors needed to explain each variable.
  → Focuses more on simplifying variables rather than factors.
* **Equamax**: A combination of Varimax and Quartimax, balancing both objectives.


#### 2. Oblique Rotation

* Allows factors to be **correlated**.
* More realistic, since factors in real-world data are usually related.

**Types:**

* **Promax**: A quick method that allows correlation between factors by relaxing the orthogonality constraint.
* **Direct Oblimin**: Allows correlations between factors and adjusts the solution accordingly.



### Why Transformation is Important

* **Improved Interpretability**:
  Raw factor solutions often have variables loading on multiple factors. Rotation simplifies this, making it clearer which variables belong to which factors.

* **Realistic Representation**:
  Orthogonal methods assume no correlation between factors. Oblique methods allow related factors, providing a more accurate picture of the data.


---

## Factor Scores

Numerical values for each observation’s position on factors.

Methods: Regression, Bartlett, Anderson-Rubin, ML.


Interpretation:

Positive score → strong presence of factor.

Negative score → weak presence.

Zero → average level.



---

## Applications of Factor Analysis

###  Market Research:
● Used to identify key factors influencing consumer behavior, such as brand perception, customer satisfaction, and
purchasing decisions.

● Example: Grouping product attributes (e.g., price, quality, design) to find common factors influencing customer
preferences.
### Psychometrics and Behavioral Research:
● Applied to develop and validate psychological tests by identifying underlying traits or factors (e.g., intelligence,
personality).

● Example: In personality assessments, factor analysis can reveal key dimensions like extraversion and openness.
### Healthcare and Medical Research:
● Helps in reducing variables like symptoms or diagnostic criteria into meaningful factors (e.g., mental health
conditions or disease risk factors).

● Example: Grouping symptoms of anxiety and depression into common underlying mental health factors.
### Education:
Used to simplify academic performance metrics, identifying key areas of student learning or educational outcomes.

Example: Analyzing student performance across subjects to identify core competencies like critical thinking or problem-solving.
### Finance:
Used to reduce a large number of financial indicators (e.g., stock prices, interest rates) into a few underlying factors influencing
market trends.

Example: In portfolio management, identifying factors like market risk or interest rate risk.
### Social Sciences:
Helps in exploring complex social issues by reducing multiple variables (e.g., income, education, and occupation) into common
social factors like socioeconomic status.

Example: Identifying key factors influencing social mobility.
### Human Resources:
Applied to identify key competencies or employee attributes influencing job performance.

Example: Grouping employee skills and behavior into factors like leadership, teamwork, or technical ability.


---
## Advantages of Factor Analysis

1. Both objective and subjective attributes can be used.

2. It can be used to identify the hidden dimensions or constraints which may or may not be
apparent from direct analysis.

3. It is not extremely difficult to do and at the same time it's inexpensive and gives accurate
results.

4. There is flexibility in naming and using dimensions.

---

## Disadvantages of Factor Analysis

1. The usefulness depends on the researcher’s ability to develop a complete and accurate set of
product attributes. If important attributes are missed the value of procedure is reduced
accordingly.

2. Naming of the factors can be difficult multiple attributes can be highly correlated with no
apparent reasons.

3. If the observed variables are completely unrelated the factor analysis is unable to produce
meaningful pattern.

4. It is not possible to know factors actually represents, only theory can help inform the
researcher’s on this.

---
