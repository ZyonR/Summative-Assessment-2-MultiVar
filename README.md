# Summative-Assessment-2-MultiVar
- Reproducible Code
- Slide Deck for the Results
- Executive Summary

# Prelimenary Statistical Analysis of Variables

Perform a one-way ANOVA for the following chemical variables: `density`, `alcohol`, `citric_acid`, `volatile_acidity`, `pH`, `total_sulfur_dioxide`,`free_sulfur_dioxide`, and `residual_sugar`. Use `quality_group` (Low, Medium, High) as the independent variable. Use ANOVA to determine which variables significantly differ across wine quality groups.

### Interpretation of ANOVA Results

Based on the ANOVA and TukeyHSD post-hoc test results for each chemical variable against the `quality_group` (Low, Medium, High), we can identify which variables show significant differences across these quality categories.

**ANOVA Findings:**

1.  **Density**
    *   **ANOVA (p < 2e-16)**: Significant difference across quality groups.
    *   **TukeyHSD**:
        *   `High` quality wine has significantly **lower** density than `Low` quality wine (diff = -0.725, p = 0.009).
        *   `High` quality wine has significantly **lower** density than `Medium` quality wine (diff = -0.693, p < 0.000).

2.  **Alcohol**
    *   **ANOVA (p < 2e-16)**: Significant difference across quality groups.
    *   **TukeyHSD**:
        *   `High` quality wine has significantly **higher** alcohol content than `Low` quality wine (diff = 0.842, p = 0.002).
        *   `High` quality wine has significantly **higher** alcohol content than `Medium` quality wine (diff = 0.949, p < 0.000).

3.  **Citric Acid**
    *   **ANOVA (p = 4.49e-12)**: Significant difference across quality groups.
    *   **TukeyHSD**:
        *   `High` quality wine has significantly **higher** citric acid than `Medium` quality wine (diff = 0.210, p < 0.000).

4.  **Volatile Acidity**
    *   **ANOVA (p < 2e-16)**: Significant difference across quality groups.
    *   **TukeyHSD**:
        *   `Medium` quality wine has significantly **lower** volatile acidity than `Low` quality wine (diff = -0.583, p = 0.049).
        *   `High` quality wine has significantly **lower** volatile acidity than `Low` quality wine (diff = -0.950, p < 0.001).
        *   `High` quality wine has significantly **lower** volatile acidity than `Medium` quality wine (diff = -0.367, p < 0.000).

5.  **pH**
    *   **ANOVA (p = 0.23)**: **No significant difference** across quality groups.

6.  **Total Sulfur Dioxide**
    *   **ANOVA (p = 0.338)**: **No significant difference** across quality groups.

7.  **Residual Sugar**
    *   **ANOVA (p = 0.000745)**: Significant difference across quality groups.
    *   **TukeyHSD**:
        *   `High` quality wine has significantly **lower** residual sugar than `Medium` quality wine (diff = -0.121, p < 0.001).

8. **Free Sulfur Dioxide**
    *   **ANOVA (p = 0.00344)**: Significant difference across quality groups.
    *   **TukeyHSD**:
        *   `High` quality wine has significantly **higher** free sulfur dioxide than `Medium` quality wine (diff = 0.0950, p = 0.0042).

**Significant Variables:**

*   `density`, `alcohol`, `citric_acid`, `volatile_acidity`,`free_sulfur_dioxide`, and `residual_sugar` show statistically significant differences across wine quality groups.
*   `pH` and `total_sulfur_dioxide` do **not** show significant differences across quality groups in this analysis.

### Important and Necessary Findings:

The ANOVA analysis reveals that `density`, `alcohol`, `citric_acid`, `volatile_acidity`, `free_sulfur_dioxide`,and `residual_sugar` significantly differ across wine quality groups (Low, Medium, High), while `pH` and `total_sulfur_dioxide` do not. These relationships contribute to identifying wine quality as follows:

*   **Higher Quality Indicators**: Wines with `High` quality tend to have significantly higher `alcohol` content and `citric_acid` levels.
*   **Lower Quality Indicators**: `High` quality wines show significantly lower `density` and `volatile_acidity`.
*   **Medium Quality Indicators**: `Residual sugar` also shows significant differences, with `High` quality wine having lower levels than `Medium` quality wine, further, a `Medium` quality wine tends to have lower levels of `free_sulfur_dioxide` that with a `High` quality wine.
*   **Factors that does not affect quality classification significantly**: `pH` and `total_sulfur_dioxide` do not appear to be significant discriminators of wine quality based on this analysis.

# Canonical Correlation Analysis (CCA)

### Structural Correlations and Significance Tests

Based on the `summary(cca_model)` output:

**1. Canonical Correlations:**
The canonical correlations represent the strength of the relationship between the canonical variate pairs where higher values indicate stronger relationships.

*   **CV 1**: 0.9613
*   **CV 2**: 0.6942
*   **CV 3**: 0.5795
*   **CV 4**: 0.2536
*   **CV 5**: 0.1089

The first canonical correlation (0.9613) is very high, indicating a strong linear relationship between the first pair of canonical variates from set A and set B. The subsequent canonical correlations decrease, suggesting progressively weaker relationships.

**2. Bartlett's Chi-Squared Test:**
This test evaluates the statistical significance of each canonical variate pair where it tests the hypothesis that the current and all subsequent canonical correlations are zero.

| Canonical Variate | rho^2      | Chisq      | df | Pr(>X)    | Significance |
|-------------------|------------|------------|----|-----------|--------------|
| CV 1              | 9.2419e-01 | 2.2263e+04 | 30 | < 2.2e-16 | *** (Highly Significant) |
| CV 2              | 4.8195e-01 | 6.8449e+03 | 20 | < 2.2e-16 | *** (Highly Significant) |
| CV 3              | 3.3577e-01 | 2.9140e+03 | 12 | < 2.2e-16 | *** (Highly Significant) |
| CV 4              | 6.4303e-02 | 4.6860e+02 | 6  | < 2.2e-16 | *** (Highly Significant) |
| CV 5              | 1.1865e-02 | 7.1344e+01 | 2  | 3.331e-16 | *** (Highly Significant) |

**Determination of Significant Canonical Dimensions:**
All five canonical variate pairs (CV 1 through CV 5) show a p-value much less than 0.05. This indicates that all five canonical correlations are statistically significant. Therefore, there are **5 statistically significant canonical dimensions** linking the two sets of variables.

## Interpretation of Structure Correlations (Loadings) from Canonical Correlation Analysis

The structure correlations, also known as canonical loadings, reveal the correlation between each original observed variable and the canonical variates. Correlations between the original variables and the identified Canonical Varaites was due to the multicollinearity that the variables exhibit, and given these variables are actually linear combinations, interpretations of coefficients are not ideal.

### Set A Variables (free_sulfur_dioxide, total_sulfur_dioxide, citric_acid, alcohol, residual_sugar)

| Variable             | Can.Var 1 | Can.Var 2 | Can.Var 3 | Can.Var 4 | Can.Var 5 |
|:---------------------|:----------|:----------|:----------|:----------|:----------|
| free_sulfur_dioxide  | -0.26     | 0.68      | -0.15     | -0.50     | 0.44      |
| total_sulfur_dioxide | -0.27     | 0.88      | -0.17     | -0.31     | -0.16     |
| citric_acid          | -0.08     | 0.48      | 0.87      | 0.09      | 0.01      |
| alcohol              | 0.83      | 0.23      | -0.07     | 0.42      | 0.28      |
| residual_sugar       | -0.81     | 0.39      | -0.14     | 0.35      | 0.22      |

-   **Canonical Variate 1 (Can.Var 1 - X)**:
    -   Strongest positive correlation with `alcohol` (0.83).
    -   Moderately correlated with `residual_sugar` (-0.81).
    -   This variate appears to be primarily influenced by both `alcohol` content and its inverse relationship with `residual_sugar`.

-   **Canonical Variate 2 (Can.Var 2 - X)**:
    -   Strongest positive correlation with `total_sulfur_dioxide` (0.88) and `free_sulfur_dioxide`(0.68).
    -   Positive moderate correlation with `citric_acid` (0.48).
    -   This variate primarily represents the positive relationship with `sulfur dioxide` levels.

-   **Canonical Variate 3 (Can.Var 3 - X)**:
    -   Extremely strong positive correlation with `citric_acid` (0.87).
    -   This variate is almost entirely defined by `citric_acid` content.

-   **Canonical Variate 4 (Can.Var 4 - X)**:
    -   Moderately correlated positively with `alcohol` (0.42).
    -   Moderately correlated positively with `residual_sugar` (0.35).
    -   Wines scoring higher on this dimension tend to have moderately higher `alcohol` and `residual_sugar`.

-   **Canonical Variate 5 (Can.Var 5 - X)**:
    -   Moderately correlated positively with `free_sulfur_dioxide` (0.44).
    -   Wines scoring higher on this dimension tend to have moderately higher `free_sulfur_dioxide`.

### Set B Variables (volatile_acidity, fixed_acidity, chlorides, density, sulphates, pH)

| Variable         | Can.Var 1 | Can.Var 2 | Can.Var 3 | Can.Var 4 | Can.Var 5 |
|:-----------------|:----------|:----------|:----------|:----------|:----------|
| volatile_acidity | 0.02      | -0.82     | -0.39     | 0.40      | -0.05     |
| fixed_acidity    | -0.05     | -0.43     | 0.78      | 0.43      | -0.15     |
| chlorides        | -0.18     | -0.86     | 0.20      | -0.33     | -0.22     |
| density          | -0.85     | -0.44     | 0.23      | 0.06      | 0.11      |
| sulphates        | 0.07      | -0.46     | 0.31      | -0.09     | 0.74      |
| pH               | 0.21      | -0.45     | -0.30     | -0.34     | 0.45      |

-   **Canonical Variate 1 (Can.Var 1 - Y)**:
    -   Extremely strong negative correlation with `density` (-0.85).
    -   This variate is almost exclusively defined by `density`.

-   **Canonical Variate 2 (Can.Var 2 - Y)**:
    -   Strong negative correlation with `volatile_acidity` (-0.82) and `chlorides` (-0.86).
    -   Moderate negative correlation with `fixed_acidity` (-0.43), `density` (-0.44), `pH` (-0.45) and `sulphates` (-0.46).
    -   This variate represents wines that have low levels of all variables within this set, especially for `volatile_acidity` and `chlorides`.

-   **Canonical Variate 3 (Can.Var 3 - Y)**:
    -   Strong positive correlation with `fixed_acidity` (0.78).
    -   This variate is primarily influenced by `fixed_acidity`.

-   **Canonical Variate 4 (Can.Var 4 - Y)**:
    -   Moderate positive correlation with `volatile_acidity` (0.40) and `fixed_acidity` (0.43).
    -    Moderate negative correlation with `pH` (-0.34) and `chlorides` (-0.33).
    - Wines that score high within this dimension tend to have a moderately higher acidity levels with lower levels of `pH` and `chlorides`.

-   **Canonical Variate 5 (Can.Var 5 - Y)**:
    -   Strong positive correlation with `sulphates` (0.74).
    -   This variate is primarily influenced by `sulphates` content.

 ### Canonical Communality

Canonical Communality refers to how much of the variance is represented within each identified canonical varaites of each set.

### Set A Variables (free_sulfur_dioxide, total_sulfur_dioxide, citric_acid, alcohol, residual_sugar)

| Variable             | Canonical Communality |
|:--------------------|:-------------------|
| free_sulfur_dioxide  | 1.00                |
| total_sulfur_dioxide | 1.00                |
| citric_acid          | 1.00                |
| alcohol              | 1.00                |
| residual_sugar       | 1.00                |

### Set B Variables (volatile_acidity, fixed_acidity, chlorides, density, sulphates, pH)

| Variable         | Canonical Communality |
|:----------------|:-------------------|
| volatile_acidity | 0.99               |
| fixed_acidity    | 1.00               |
| chlorides        | 0.97               |
| density          | 0.99               |
| sulphates        | 0.87               |
| pH               | 0.65               |

Based on the canonical communalities, most variables in both sets have nearly all of their variance captured by the identified canonical variates. This indicates that the canonical variates provide a good summary of the original variables’ patterns within each set. Exceptions are `pH`, with only about 65% of its variance captured, and `sulphates`, which is slightly lower, suggesting that these variables are less fully represented by the canonical variates.

Implications of these results indicates that there is a unique varaince for both these variables that are not strongly aligned with the multivariate patterns, thus indicating a low or independent influence over cross set relationships.

### Canonical Variate Adequacies

Canonical Variate Adequacies refers to how much of the variance for each set is explained by the identified canonical variates.

| Canonical Variate | Set A    | Set B     |
|:-----------------|:----------|:----------|
| CV 1             | 0.30      | 0.14      |
| CV 2             | 0.34      | 0.37      |
| CV 3             | 0.17      | 0.17      |
| CV 4             | 0.13      | 0.10      |
| CV 5             | 0.07      | 0.14      |

-   **SET A**:
    -   Based on the table, we can observe that the variate that capture more than half of the variance from set A are `CV 1`(0.3) and `CV 2` (0.34). `CV 1` refers to high sulfur dioxide and alcohol levels while having low `residual_sugar`.
    -   Other variates `CV 3` (0.17), `CV 4` (0.13), and `CV 5` (0.07) capture smaller or more nuanced portions of the variance in Set A and therefore represent more specific or subtle patterns in the data, such as variations in variables, or contrasting combinations, but their overall contribution to explaining Set A’s variance is limited compared to CV 1 and CV 2.
    - CV 1 and CV 2 indicate the main chemical patterns driving variation in Set A.

-   **SET B**:
    -   Based on the table, we can observe that the variate that captures the varaince of the set more is `CV 2` (0.37). `CV 2` refers to lower levels of `volatile_acidity` and `chlorides`.
    -   Other other variates capture more nuanced portions of the variance in Set B, however their overall contribution to explaining Set B’s variance is smaller compared to CV 2.
    - CV 2 highlights the dominant chemical profile in Set B that potentially responds to changes in Set A.

 ### Redundancy Analysis

Redundancy Analysis quantifies the amount of varaince that is captured by set A through set B.

| Canonical Variate | Set A → Set B (Variance in Set B explained by Set A CV) | Set B → Set A (Variance in Set A explained by Set B CV) |
|:-----------------|:---------------------------------------------|:---------------------------------------------|
| CV 1             | 0.276                                        | 0.125                                        |
| CV 2             | 0.162                                        | 0.177                                        |
| CV 3             | 0.056                                        | 0.057                                        |
| CV 4             | 0.008                                        | 0.006                                        |
| CV 5             | 0.001                                        | 0.002                                        |

-   **Set A → Set B**:
    - **Total Variance Explained by All CVs, Across Sets: 0.5025**
    - Using the identified variates of set A `CV 1` (0.276) captures the most varaince within set B with **27.6%** being explained.
    - The variables from set A collectively explain about 50% of the variance in Set B, particularly the first canonical variate of Set A alone accounts for 27.6% of the variance in Set B. This indicates that the dominant chemical patterns in Set A, such as higher alcohol and sulfur dioxide levels and lower residual sugar, are associated with the overall chemical profile of Set B. While this 50% shared variance suggests a moderate association between the sets, it also highlights that roughly half of the variation in Set B is not captured by Set A, meaning that many aspects of the wine’s chemical profile are independent and would require additional analyses to fully understand.

-   **Set B → Set A**:
    - **Total Variance Explained by All CVs, Across Sets: 0.3673**
    - Using the identified variates of set B `CV 2` (0.177) captures the most varaince within set A with **17.7%** being explained.
    - The variables from set B collectively explain about 36.73% of the variance in Set A, particularly the second canonical variate of Set B alone accounts for 17.1% of the variance in Set A. This indicates that the there exists a moderate association between the overall chemical profile of Set A and its lower levels of `volatile_acidity` and `chlorides`. This 36.73% shared variance suggests a little to moderate association between the sets. This low variance means that a majority of the variation in Set A is not captured by the canonical variates of Set B, indicating that many characteristics of Set A, such as alcohol content, sulfur dioxide, and residual sugar are largely independent of the patterns identified in Set B. Thus, while some associations exist, relying solely on Set B to predict or understand the full chemical profile of Set A would be limited, and additional analyses or variables may be needed to fully explain the variation in Set A.

# Factor Analysis (FA)

### Interpretation of FA Results

Based on the output from the `fa.parallel`, `summary(efa_vari4)`, `print(efa_vari4,cut = 0.4)`, and the warnings, here's an interpretation of the Factor Analysis:

1.  **Number of Factors**: The parallel analysis suggested 4 factors, and we proceeded with fitting a 4-factor model.

2.  **Model Fit Indices (`summary(efa_vari4)`)**:
    *   **Chi-Square Test**: The Chi-Square value of 7139.46 which is a non-significant p-value (e.g., > 0.05) indicating that the 4-factor model does not provide a good fit to the data.
    *   **Tucker Lewis Index (TLI)**: The TLI is 0.408  suggests a poor fit.
    *   **RMSEA Index**: The Root Mean Square Error of Approximation (RMSEA) is 0.265 (with a 90% confidence interval of 0.259 to 0.270) further indicating a poor model fit.
    *   **Root Mean Square of the Residuals (RMSR)**: The RMSR is 0.03. Lower values are better, with values close to 0 indicating a good fit. This metric looks acceptable, but it should be considered in conjunction with other fit indices.

3.  **Factor Loadings and Structure (`print(efa_vari4,cut = 0.4)`)**:
    The `print` output (with a cutoff of 0.4 for loadings) shows how each variable correlates with the latent factors:
    *   **PA1 (Factor 1)**:
        *   Strongly loads on `total_sulfur_dioxide` (-0.84), `free_sulfur_dioxide` (-0.72), `fixed_acidity` (0.64), `chlorides` (0.61), and `volatile_acidity` (0.54). This factor appears to represent a dimension related to `sulfur compounds` and some `acidity` components.
    *   **PA2 (Factor 2)**:
        *   Strongly loads on `density` (1.07), `alcohol` (-0.71), and `residual_sugar` (0.56). This factor seems to capture aspects related to `sweetness`, `alcohol content`, and `density`.
        *   **CRITICAL ISSUE**: The loading of `density` (1.07) is greater than 1, and its communality (`h2`) is 1.24, with a negative uniqueness (`u2`) of -0.24. This is an **"ultra-Heywood case"**, it indicates that the model is trying to explain more than 100% of the variance in `density`, suggesting a misspecification of the model, an insufficient number of factors, or issues with the data itself.
    *   **PA3 (Factor 3)**:
        *   Strongly loads on `citric_acid` (0.83) and negatively on `volatile_acidity` (-0.45). This factor could represent `citric acidity` opposing `volatile acidity`.
    *   **PA4 (Factor 4)**:
        *   Strongly loads on `pH` (0.84). This factor is primarily driven by `pH`.
    *   `sulphates` does not load significantly on any of the four factors (i.e., its loading is below 0.4 on all factors).

4.  **Variance Explained**: The 4 factors together explain 65% of the total variance in the observed variables (`Cumulative Var`).

The factor analysis results suggest that the 4-factor model, as currently specified, does not fit the data well due to poor model fit indices and the presence of an ultra-Heywood case. The Heywood case, in particular, indicates a fundamental problem with the model or the data. Further investigation or alternative modeling approaches might be necessary.

# Principal Component Analysis (PCA)

#### 1. Cumulative Variance

*   Identified 9 principal components (RC1 through RC9) that collectively explain **98.1%** of the total variance in the dataset. This is a very high percentage, indicating that we have successfully reduced the dimensionality of our data while retaining almost all the important information.

#### 2. Component Loadings

Loadings represent the correlation between the original variables and the principal components. They tell us which variables contribute most to each component and thus help us understand what each component represents. A loading value closer to 1 or -1 indicates a strong relationship.

Let's interpret each component based on the variables with absolute loadings greater than 0.3:

*   **RC1**: Strongly loaded by `free_sulfur_dioxide` (0.939) and `total_sulfur_dioxide` (0.823). This component appears to be primarily driven by **sulfur dioxide levels**, representing aspects of sulfur-related compounds in the wine.
*   **RC2**: Heavily loaded by `alcohol` (-0.972) and `density` (0.692). The negative loading for alcohol suggests an inverse relationship. This component seems to capture characteristics related to **alcohol content and overall density** of the wine.
*   **RC3**: Primarily loaded by `citric_acid` (0.943). This component is clearly associated with the **citric acid content**.
*   **RC4**: Strongly loaded by `sulphates` (0.963), indicating it represents **sulphate content**.
*   **RC5**: Dominated by `chlorides` (0.850), representing the **chloride content**.
*   **RC6**: Highly loaded by `residual_sugar` (0.908) and also by `density` (0.519). This component seems to capture aspects of **sugar content** and its relation to density.
*   **RC7**: Heavily loaded by `pH` (0.952), indicating it represents the **pH level** of the wine.
*   **RC8**: Predominantly loaded by `fixed_acidity` (0.912) and to a lesser extent by `density` (0.340). This component likely represents **fixed acidity**.
*   **RC9**: Strongly loaded by `volatile_acidity` (0.885), representing **volatile acidity**.

#### 3. Communalities

Communalities measure the proportion of each variable's variance that is explained by the retained principal components. Values closer to 1 mean that the variable is well-represented by the components.

*   The communality values are all very high, ranging from **0.902** (for `total_sulfur_dioxide`) to **0.999** (for `sulphates`).
*   This indicates that over **90%** of the variance in each of the original numeric variables is explained by the 9 principal components. This confirms that our PCA model effectively captures almost all the information from the original variables, and very little unique variance from the original variables is lost in the dimensionality reduction process.

### ANOVA Results

**Significant Principal Components (p < 0.05):**

*   **RC2**: p < 2e-16 (Highly Significant)
*   **RC6**: p = 0.0301 (Significant)
*   **RC4**: p = 1.88e-05 (Highly Significant)
*   **RC7**: p = 0.0467 (Significant)
*   **RC3**: p = 0.000166 (Highly Significant)
*   **RC9**: p < 2e-16 (Highly Significant)
*   **RC5**: p = 1.02e-11 (Highly Significant)

These seven components show a statistically significant relationship with wine quality, meaning their mean scores differ significantly across at least some of the quality groups.

**Non-Significant Principal Components (p > 0.05):**

*   **RC1**: p = 0.632 (Not Significant)
*   **RC8**: p = 0.671 (Not Significant)

For RC1 and RC8, there is no statistical evidence that their mean scores differ across the wine quality groups. This suggests these components are less useful for differentiating wine quality.

### Tukey HSD Post-Hoc Tests

*   **RC2**:
    *   `High` vs. `Low`: **Significant** (`p adj = 0.0008802`). The mean RC2 score for high-quality wines is significantly different from low-quality wines.
    *   `High` vs. `Medium`: **Highly Significant** (`p adj = 0.0000000`). There is a very strong difference between high and medium quality wines for RC2.

*   **RC6**:
    *   `High` vs. `Medium`: **Significant** (`p adj = 0.0240917`). High and medium quality wines differ significantly in RC6 scores.

*   **RC4**:
    *   `High` vs. `Medium`: **Highly Significant** (`p adj = 0.0000125`). High and medium quality wines differ significantly in RC4 scores.

*   **RC7**:
    *   None of the pairwise comparisons reached statistical significance.

*   **RC3**:
    *   `High` vs. `Medium`: **Highly Significant** (`p adj = 0.0001465`). High and medium quality wines differ significantly in RC3 scores.

*   **RC9**:
    *   `High` vs. `Low`: **Significant** (`p adj = 0.004200`). High and low quality wines differ significantly in RC9 scores.
    *   `High` vs. `Medium`: **Highly Significant** (`p adj = 0.0000000`). There is a very strong difference between high and medium quality wines for RC9.

*   **RC5**:
    *   `High` vs. `Medium`: **Highly Significant** (`p adj = 0.0000000`). High and medium quality wines differ significantly in RC5 scores.

#### **High vs. Medium Quality**

The most consistent differences are observed between `High` and `Medium` quality wines. Six components (RC2, RC3, RC4, RC5, RC6, and RC9) show statistically significant differences between these two groups. This indicates that these components are strong differentiators for high-quality wines compared to medium-quality ones.

#### **High vs. Low Quality**
Significant differences exist for RC2 and RC9. This suggests that these two components are particularly important in distinguishing high-quality wines from low-quality wines.

#### **Medium vs. Low Quality**
The Tukey HSD tests did not find a statistically significant difference between `Medium` and `Low` quality wines. This implies that while the components can differentiate 'High' quality wines from the other two categories, they do not clearly separate 'Medium'from 'Low' quality based on these factors.

# Quadratic Linear Discriminant (QLD) Clustering Results

Here's an interpretation of the QDA clustering results based on the confusion matrix:

### Confusion Matrix and Statistics

**Reference (Actual Classes):** Low, Medium, High
**Prediction (Predicted Classes):** Low, Medium, High

```
          Reference
Prediction  Low Medium High
    Low       6      5    1
    Medium    7   4124  504
    High      1    632  704
```

#### Overall Statistics:

*   **Accuracy: 0.8078 (80.78%)**
    *   This means that approximately 80.78% of the wines were correctly classified into their quality groups (Low, Medium, or High) by the QDA model. This is a decent overall performance.
*   **95% CI: (0.7976, 0.8177)**
    *   We can be 95% confident that the true accuracy of the model lies between 79.76% and 81.77%.
*   **No Information Rate (NIR): 0.7956**
    *   This is the accuracy that would be achieved by simply predicting the most frequent class (which is 'Medium' at 79.56%).
*   **P-Value [Acc > NIR]: 0.009680**
    *   Since this p-value is less than 0.05, it indicates that the model's accuracy (80.78%) is significantly better than simply guessing the most frequent class. This is a positive sign.
*   **Kappa: 0.4324**
    *   Kappa is a measure of agreement between the predicted and actual classifications, adjusting for chance agreement. A Kappa value of 0.4324 suggests a moderate level of agreement. Generally, values between 0.41-0.60 are considered moderate agreement.
*   **Mcnemar's Test P-Value: 0.002038**
    *   This low p-value suggests that there is a significant difference in the marginal probabilities of 'predicted equals actual' versus 'predicted does not equal actual'. This often indicates that the misclassifications are not symmetrical between classes.

#### Prediction Eval Metrics:

*   **Low Wine Quality**
    *   **Sensitivity (Recall): 0.428571** (Correctly identified 42.86% of actual 'Low' quality wines)
    *   **Specificity: 0.998995** (Correctly identified 99.90% of wines that were *not* 'Low' quality)
    *   **Pos Pred Value (Precision): 0.500000** (When the model predicted 'Low', it was correct 50% of the time)
    *   **Neg Pred Value: 0.998660** (When the model predicted not 'Low', it was correct 99.87% of the time)
    *   **Balanced Accuracy: 0.713783**

The model is very good at identifying wines that are NOT 'Low' quality but struggles to correctly identify actual 'Low' quality wines. When it does predict 'Low', it's right about half the time.

*   **Medium Wine Quality**
    *   **Sensitivity (Recall): 0.8662** (Correctly identified 86.62% of actual 'Medium' quality wines)
    *   **Specificity: 0.5822** (Correctly identified 58.22% of wines that were not 'Medium' quality)
    *   **Pos Pred Value (Precision): 0.8898** (When the model predicted 'Medium', it was correct 88.98% of the time)
    *   **Neg Pred Value: 0.5278** (When the model predicted not 'Medium', it was correct 52.78% of the time)
    *   **Balanced Accuracy: 0.7242**

 The model performs best for the 'Medium' class, which is also the most prevalent class. It has high recall and precision for 'Medium' wines, meaning it identifies most of them correctly and its 'Medium' predictions are largely reliable. However, its specificity is lower, indicating it sometimes incorrectly classifies 'Low' or 'High' wines as 'Medium'.

*   **High Wine Quality**
    *   **Sensitivity (Recall): 0.5823** (Correctly identified 58.23% of actual 'High' quality wines)
    *   **Specificity: 0.8674** (Correctly identified 86.74% of wines that were not 'High' quality)
    *   **Pos Pred Value (Precision): 0.5266** (When the model predicted 'High', it was correct 52.66% of the time)
    *   **Neg Pred Value: 0.8913** (When the model predicted not 'High', it was correct 89.13% of the time)
    *   **Balanced Accuracy: 0.7249**

 The model has moderate sensitivity and good specificity for the 'High' class. It identifies about 58% of actual 'High' quality wines and is generally reliable when it predicts 'High' (52.66% precision). It's also quite good at not misclassifying non-'High' wines as 'High'.

The QDA model shows a good overall accuracy, significantly better than chance. It performs strongest on the 'Medium' quality wines, likely due to their higher prevalence in the dataset. It struggles most with identifying 'Low' quality wines, often misclassifying them as 'Medium'. For 'High' quality wines, its performance is moderate, balancing between identifying actual 'High' wines and avoiding false positives. The Kappa value indicates moderate agreement beyond chance, suggesting the model has learned some meaningful patterns, but there's still room for improvement, especially in distinguishing between the 'Low' and 'Medium' classes.

# Executive Summary:

This analysis aimed to understand the complex relationships between chemical properties and wine quality using various statistical and machine learning techniques.

**Key Chemical Drivers of Wine Quality (ANOVA & PCA):**
*   Several chemical properties significantly differentiate wine quality. High-quality wines consistently exhibit **higher alcohol and citric acid levels** and **lower density and volatile acidity**. Residual sugar and free sulfur dioxide also play roles in differentiation.
*   Principal Component Analysis (PCA) successfully reduced the dimensionality, explaining 98.1% of variance across 9 components, with components representing factors like 'alcohol/density' (RC2), 'citric acid' (RC3), and 'volatile acidity' (RC9) being significant in distinguishing wine quality, especially between High and Medium quality. Conversely, components related to sulfur dioxide (RC1) and fixed acidity (RC8) did not show significant differentiation.

**Interdependencies Among Chemical Properties (CCA):**
*   Canonical Correlation Analysis (CCA) revealed strong interdependencies among chemical groups. For instance, higher `alcohol` and lower `residual_sugar` (Set A) were strongly linked to lower `density` (Set B). The model highlighted that about 50% of the variance in a wine's general chemical profile (Set B) can be explained by specific compositional traits (Set A), indicating a moderate yet significant cross-set relationship.

**Factor Structure & Model Limitations (FA):**
*   Factor Analysis (FA) attempted to uncover latent factors but faced significant challenges, including poor model fit and an "ultra-Heywood case" for `density`, rendering its results unreliable. This suggests the assumed linear factor structure may not adequately represent the data or that the chosen variables are too highly correlated for FA's assumptions.

**Predicting Wine Quality (QLD Clustering):**
*   A Quadratic Linear Discriminant (QLD) model achieved an overall accuracy of **80.78%** in classifying wine quality (Low, Medium, High), significantly outperforming random chance (Kappa = 0.4324).
*   The model performed best for **Medium quality wines**, accurately identifying 86.62% of them. However, it struggled with **Low quality wines** (42.86% sensitivity), frequently misclassifying them as Medium. Performance for **High quality wines** was moderate (58.23% sensitivity). This suggests the model is effective for the dominant 'Medium' class but needs improvement in distinguishing the less frequent 'Low' and 'High' categories.

**Conclusion:**
The analysis clearly identifies several chemical properties critical for wine quality differentiation, with alcohol, density, and various acidity measures being particularly influential. While advanced techniques like PCA effectively characterize these properties and their role in quality, and QLD provides a reasonably accurate predictive model, the underlying factor structure remains elusive due to model fit issues with FA. Further efforts might focus on improving classification for the 'Low' and 'High' quality tiers and exploring alternative dimensionality reduction or structural modeling techniques.






