# Data Quality & Validation Checklist

High-quality data is the foundation of any robust algorithm or research study. Use this checklist to ensure your data handling practices meet scientific standards.

## 1. Data Splitting (The Golden Rule)

**CRITICAL:** Never mix data from the same patient across Training, Validation, and Test sets. This causes "Data Leakage" and leads to over-optimistic results.

*   [ ] **Patient-Level Splitting:** Split by Subject ID, NOT by sample/segment.
    *   *Correct:* Patient A (Train), Patient B (Train), Patient C (Test).
    *   *Incorrect:* Patient A-Day1 (Train), Patient A-Day2 (Test).
*   [ ] **Stratification:** Ensure the distribution of key variables (age, gender, disease class) is similar across splits.
*   [ ] **Test Set Isolation:** The Test set (Hold-out set) should be locked away and only used ONCE for the final evaluation.

## 2. Cross-Validation Strategies

When data is limited, use cross-validation to estimate performance robustness.

*   [ ] **k-Fold Cross-Validation:** Split patients into *k* groups (folds). Train on *k-1*, test on 1. Repeat *k* times.
    *   *Standard:* 5-fold or 10-fold.
*   [ ] **Leave-One-Subject-Out (LOSO):** Train on all but one subject, test on that subject. Repeat for all subjects.
    *   *Best for:* Small datasets, personalized models.
*   [ ] **Nested Cross-Validation:** Use an inner loop for hyperparameter tuning and an outer loop for performance estimation.

## 3. Sample Size & Power

*   [ ] **Justification:** Is the sample size sufficient to detect the expected effect?
    *   *Tools:* G*Power, Python `statsmodels`.
*   [ ] **Events per Variable (EPV):** For regression/classification, aim for at least 10-20 events (positive cases) per predictor variable to avoid overfitting.
*   [ ] **Diversity:** Does the sample represent the target population demographics?

## 4. Annotation / Ground Truth Quality

Garbage In, Garbage Out. The algorithm cannot be better than the labels it learns from.

*   [ ] **Gold Standard:** What is the reference? (Biopsy, Expert Consensus, Device).
*   [ ] **Inter-Rater Reliability:** If using human annotators, measure agreement.
    *   *Metrics:* Cohen's Kappa, Fleiss' Kappa, Intraclass Correlation Coefficient (ICC).
*   [ ] **Adjudication:** How are disagreements resolved? (Third reviewer, consensus meeting).

## 5. Data Cleaning & Preprocessing

*   [ ] **Missing Data:**
    *   *Identify:* Is data missing at random (MAR) or not at random (MNAR)?
    *   *Handle:* Imputation (mean, median, KNN), deletion (if <5%), or use models that handle missingness (XGBoost).
*   [ ] **Outliers:**
    *   *Detect:* Z-score > 3, IQR method.
    *   *Action:* Verify if real physiological events or artifacts. Remove only if artifacts.
*   [ ] **Normalization/Scaling:**
    *   *Standard:* Zero-mean, unit variance (StandardScaler).
    *   *Range:* Min-Max scaling (0-1).
    *   *Note:* Apply scaling parameters from TRAINING set to Test set.

## 6. Reproducibility

*   [ ] **Code Versioning:** Use Git.
*   [ ] **Data Versioning:** Track which dataset version was used for which result (e.g., DVC).
*   [ ] **Seed:** Set random seeds for all stochastic processes (splitting, initialization) to ensure results can be reproduced.
