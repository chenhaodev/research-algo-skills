# Evaluation Criteria (Scoring Rubric)

This document defines the scoring rubric used to evaluate candidate algorithms and academic papers. The goal is to objectively assess the "translation potential" of a method—how likely it is to work in a real-world clinical product.

## Scoring System Overview

Each candidate is scored on a scale of **0 to 4**. Points are awarded for the presence of four specific positive attributes.

**Formula:**
`Score = (Overfitting Resistance) + (Physiological Rationale) + (Mathematical Proof) + (Source Code Accessibility)`

## Criterion 1: Overfitting Resistance (+1 Point)

Does the study demonstrate that the model generalizes to new data?

### Requirements for +1 Point:
*   **Data Split:** Proper separation of Training, Validation, and Test sets.
*   **Validation Type:**
    *   **Gold Standard:** External Validation (Testing on a completely different dataset/hospital).
    *   **Acceptable:** Prospective data collection (Testing on data collected *after* the model was frozen).
    *   **Minimum:** Strict Hold-out set (Random split, but never touched during training).
*   **Data Balance:** The test set reflects realistic class prevalence (or is balanced and metrics are adjusted).

### Examples:
*   **Good (+1):** "We trained on MIMIC-III and validated on an internal dataset of 500 patients collected prospectively."
*   **Bad (0):** "We used 10-fold cross-validation on 50 patients." (High risk of data leakage/overfitting).
*   **Bad (0):** "We achieved 99% accuracy." (Suspiciously high, likely overfitted).

## Criterion 2: Physiological / Pathological Rationale (+1 Point)

Is the method grounded in biological reality, or is it a "black box" finding random correlations?

### Requirements for +1 Point:
*   **Mechanism:** The paper explains *why* the features should predict the outcome based on known physiology.
*   **Alignment:** The method aligns with the clinical pathway (Symptom -> Diagnosis -> Treatment).
*   **Feature Interpretability:** The input features map to physical quantities (e.g., "Heart Rate Variability reflects autonomic tone") rather than abstract embeddings.

### Examples:
*   **Good (+1):** "We use the QT interval because it reflects ventricular repolarization, which is prolonged in drug-induced arrhythmia."
*   **Bad (0):** "We fed raw data into a 50-layer CNN and it predicted the disease." (No explanation of *what* it learned).
*   **Bad (0):** "We combined age, shoe size, and zip code to predict diabetes." (Spurious correlation).

## Criterion 3: Mathematical Proof / Soundness (+1 Point)

Is the algorithm mathematically robust?

### Requirements for +1 Point:
*   **Formal Proofs:** Existence of convergence bounds, generalization error bounds, or stability proofs.
*   **Heuristic Justification:** Strong theoretical argument for why the architecture fits the data structure (e.g., "Using CNNs because ECG data has translation invariance").
*   **Empirical Demonstration:** Extensive ablation studies showing the contribution of each component.

### Examples:
*   **Good (+1):** "We prove that our convex optimization objective guarantees a global minimum."
*   **Good (+1):** "We use a Kalman Filter because the underlying system dynamics are linear and Gaussian."
*   **Bad (0):** "We tweaked the hyperparameters until it worked."
*   **Bad (0):** "We proposed a novel 'Quantum-Neuro-Fuzzy' layer." (Buzzword soup without mathematical substance).

## Criterion 4: Source Code Accessibility (+1 Point)

Can we reproduce the results without reinventing the wheel?

### Requirements for +1 Point:
*   **Availability:** Code is hosted on a public repository (GitHub, GitLab, Bitbucket).
*   **Completeness:** Includes training scripts, inference scripts, and (ideally) a sample dataset.
*   **Documentation:** Instructions on how to run the code are provided.

### Examples:
*   **Good (+1):** "Code and pre-trained models are available at github.com/lab/project."
*   **Bad (0):** "Code is available upon reasonable request." (Usually means never).
*   **Bad (0):** No mention of code availability.

## Scoring Interpretation

| Total Score | Classification | Action |
| :--- | :--- | :--- |
| **4 / 4** | **Ideal Candidate** | **Adopt immediately.** This is a high-quality, validated, explainable, and reproducible method. |
| **3 / 4** | **Strong Candidate** | **Proceed with caution.** Identify the missing point (e.g., no code) and estimate the effort to fix it (e.g., re-implement from paper). |
| **2 / 4** | **Acceptable Risk** | **Fallback option.** Only use if no better options exist. Requires significant internal validation effort. |
| **1 / 4** | **Weak** | **Avoid.** Likely to fail in production. |
| **0 / 4** | **Unacceptable** | **Reject.** Do not waste time reading further. |
