# Common Statistical Methods for Clinical Research

A quick reference guide for selecting the right statistical test for your data and study design.

## 1. Descriptive Statistics

Used to summarize the characteristics of a dataset.

*   **Mean (Average):** Use for normally distributed data.
*   **Standard Deviation (SD):** Measure of spread around the mean.
*   **Median:** Use for skewed data (non-normal).
*   **Interquartile Range (IQR):** Measure of spread for the median (25th to 75th percentile).
*   **Frequency/Percentage:** For categorical data (e.g., Gender, Disease Status).

## 2. Assessing Agreement (Validation)

Used to compare a new method against a reference standard.

*   **Bland-Altman Plot:** The gold standard for method comparison. Plots the difference between two methods against their mean.
    *   *Output:* Bias (mean difference) and Limits of Agreement (±1.96 SD).
*   **Intraclass Correlation Coefficient (ICC):** Measures reliability/consistency.
    *   *Range:* 0 (no agreement) to 1 (perfect agreement). >0.75 is usually good.
*   **Cohen's Kappa:** Measures inter-rater agreement for categorical items (e.g., Diagnosis A vs B).

## 3. Comparing Groups (Hypothesis Testing)

Used to determine if differences between groups are statistically significant.

| Comparison | Normal Data (Parametric) | Non-Normal Data (Non-Parametric) |
| :--- | :--- | :--- |
| **2 Independent Groups** (e.g., Treatment vs Control) | **Independent T-test** | **Mann-Whitney U Test** (Wilcoxon Rank Sum) |
| **2 Paired Groups** (e.g., Before vs After) | **Paired T-test** | **Wilcoxon Signed-Rank Test** |
| **3+ Independent Groups** | **ANOVA** (Analysis of Variance) | **Kruskal-Wallis Test** |
| **Categorical Data** | **Chi-Square Test** | **Fisher's Exact Test** (small samples) |

## 4. Diagnostic Performance Metrics

Used to evaluate classification algorithms.

*   **Sensitivity (Recall):** Ability to correctly identify positives. (TP / (TP + FN))
*   **Specificity:** Ability to correctly identify negatives. (TN / (TN + FP))
*   **Positive Predictive Value (PPV):** Probability that a positive result is truly positive. Depends on prevalence.
*   **Negative Predictive Value (NPV):** Probability that a negative result is truly negative.
*   **ROC Curve & AUC:** Plot of Sensitivity vs (1-Specificity). AUC = 0.5 is random, 1.0 is perfect.

## 5. Regression Analysis

Used to model relationships between variables.

*   **Linear Regression:** Predict a continuous outcome (e.g., Blood Pressure) based on predictors.
*   **Logistic Regression:** Predict a binary outcome (e.g., Disease/No Disease). Output is Odds Ratio (OR).
*   **Cox Proportional Hazards:** Analyze time-to-event data (Survival Analysis). Output is Hazard Ratio (HR).

## 6. Meta-Analysis Statistics

Used when combining results from multiple studies.

*   **Forest Plot:** Visual display of estimated results from included studies.
*   **Fixed Effects Model:** Assumes all studies estimate the same underlying effect.
*   **Random Effects Model:** Assumes the underlying effect varies across studies (usually preferred).
*   **Heterogeneity ($I^2$):** Percentage of variation across studies due to heterogeneity rather than chance.
    *   *Low:* <25%
    *   *Moderate:* 25-50%
    *   *High:* >50%
