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

Eigenvalue Criterion (Kaiser’s Rule) – retain factors with eigenvalue > 1.

Scree Plot – look for the “elbow.”

Cumulative Variance Explained – keep enough factors to explain 70–80% variance.

Parallel Analysis – compare with random data eigenvalues.



---

## Transformation of Factor Analysis Solutions

Factors are often rotated to improve interpretation.

Orthogonal Rotations (factors independent):

Varimax

Quartimax

Equamax


Oblique Rotations (factors correlated):

Promax

Direct Oblimin


Rotation makes loadings easier to interpret.


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

Market Research: Identify drivers of customer satisfaction.

Psychology: Personality & intelligence testing.

Healthcare: Grouping symptoms into disorders.

Education: Identifying core competencies.

Finance: Finding hidden risk factors.

HR: Grouping employee skills.



---
## Advantages of Factor Analysis

✅ Reveals hidden patterns.
✅ Reduces dimensionality.
✅ Simplifies survey/test analysis.
✅ Useful in predictive modeling.


---

## Disadvantages of Factor Analysis

❌ Naming factors is subjective.
❌ Results depend on assumptions.
❌ Factors are not directly measurable.
❌ If variables are unrelated → no useful factors.


---
