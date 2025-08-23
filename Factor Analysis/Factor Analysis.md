# Factor Analysis

Factor Analysis is a statistical method used to simplify complex datasets by identifying patterns among observed variables.
It reduces many variables into fewer hidden factors (latent variables), showing how they are related.
The main idea is to group correlated variables together into underlying dimensions (factors).


## Latent Variables

Latent variables are variables that cannot be directly measured, but can be inferred from observed data.

They represent underlying constructs that influence the observed values.


### Examples:

In psychology: "Intelligence" (latent) is measured using test scores (observed).

In marketing: "Customer satisfaction" (latent) is inferred from survey responses (observed).

In education: "Language ability" (latent) is inferred from essay, reading, vocabulary scores.



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

Simplify data into fewer factors.

Discover hidden patterns.

Group similar variables together.

Improve predictions.

Help design and validate surveys/tests.

Generate new insights about relationships.



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

X_i = \lambda_{i1}F_1 + \lambda_{i2}F_2 + \cdots + \lambda_{im}F_m + \epsilon_i

Where:

 = observed variable

 = common factors (latent)

 = factor loadings

 = unique/error variance



---

## Important Terms

Factor Loadings: Correlation between observed variable & factor.

Eigenvalues: Amount of variance explained by each factor.

Factor Scores: Each individual’s score on the latent factors.



---

## Methods of Extracting Common Factors

1. Principal Component Analysis (PCA) – explains maximum variance.


2. Principal Axis Factoring (PAF) – focuses only on common variance.


3. Maximum Likelihood (ML) – model fitting with statistical tests.


4. Image Factoring – based on partial correlations.


5. Other methods: Alpha factoring, ULS, GLS.




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
