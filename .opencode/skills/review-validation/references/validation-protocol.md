# Clinical Validation Protocol

This document details the methodology for validating AI/ML models against clinical standards. It focuses on benchmarking against established datasets and FDA-cleared devices.

## 1. Reference Database Selection

Validation must be performed on "Gold Standard" datasets that are independent of the training data.

### 1.1. Physionet Databases
Physionet is the standard repository for medical physiologic signals.
*   **QT Database (QTDB):**
    *   *Use Case:* ECG delineation (P-wave, QRS, T-wave limits).
    *   *Stats:* 105 records, 15 mins, 2-channel.
    *   *Annotations:* Expert manual annotation (Gold Standard).
*   **Apnea-ECG Database:**
    *   *Use Case:* Sleep apnea detection from single-lead ECG.
    *   *Stats:* 70 records (approx 8 hours each).
*   **MIMIC-III / MIMIC-IV:**
    *   *Use Case:* ICU mortality prediction, sepsis, hemodynamics.
    *   *Stats:* >40,000 patients, multi-modal (vitals, labs, notes).

### 1.2. Selection Criteria
1.  **Public Availability:** Allows reproducibility.
2.  **Expert Annotation:** Labels must be clinically verified (not just automated output).
3.  **Diversity:** Includes various pathologies and morphologies.

## 2. Validation Protocol Steps

### Step 1: Data Extraction & Splitting
*   **Subject Independence:** Ensure NO patient overlap between Train and Test sets.
*   **Sampling:**
    *   Extract random segments (e.g., 10s strips) from the Test Set.
    *   Ensure balanced representation of classes (Normal vs. Abnormal).

### Step 2: Model Inference
*   Run the trained model on the extracted test samples.
*   Store raw predictions (probabilities/values) and final labels.

### Step 3: Comparison to Gold Standard
*   **Alignment:** For time-series (ECG), align model output with ground truth annotations using a tolerance window (e.g., ±150ms for T-wave end).
*   **Matching:** Only compare "Matched" beats. Count "Missed" beats separately.

### Step 4: Statistical Analysis
Calculate the following metrics:

| Metric | Formula | Interpretation |
| :--- | :--- | :--- |
| **Mean Absolute Error (MAE)** | $\frac{1}{n}\sum |y_{pred} - y_{true}|$ | Average error magnitude. Lower is better. |
| **Standard Deviation (STD)** | $\sigma$ of error | Precision/Variability. Lower is better. |
| **Delta Error** | $y_{pred} - y_{true}$ | Signed error. Used to detect systematic bias. |
| **Correlation (r)** | Pearson / Spearman | Linear relationship. Target > 0.9. |

## 3. Advanced Statistical Methods

### 3.1. Bland-Altman Analysis
The standard for method comparison.
*   **Plot:** X-axis = Mean of (Pred, True); Y-axis = Difference (Pred - True).
*   **Bias:** Mean difference. Ideally 0.
*   **Limits of Agreement (LoA):** Bias ± 1.96 * STD.
*   **Interpretation:** 95% of errors fall within the LoA. If LoA is too wide (clinically unsafe), the method fails.

### 3.2. Paired T-Test
*   Tests if the systematic bias is statistically significant.
*   *Null Hypothesis:* Bias = 0.
*   *Result:* If p < 0.05, there is a significant bias (model consistently over/under-estimates).

## 4. Benchmarking Strategy

### 4.1. Against Literature
Compare your results to top-tier papers.
*   **Example (QT Interval):**
    *   *Charbit et al. (2006):* MAE ~15ms.
    *   *Salvi et al. (2011):* MAE ~13ms.
    *   *Target:* Your model should achieve MAE < 13ms.

### 4.2. Against FDA Devices
Compare against cleared devices (510(k) summaries are public).
*   **AliveCor KardiaMobile:**
    *   *Claim:* Atrial Fibrillation detection.
    *   *Performance:* Sensitivity 98%, Specificity 97%.
*   **Apple Watch ECG:**
    *   *Claim:* AF detection (Class II).
    *   *Performance:* Sensitivity 98.3%, Specificity 99.6%.
*   **Target:** Non-inferiority (within margin of error) or Superiority.

## 5. Reporting Template

### Section 1: Methods
*   "We validated the algorithm on the Physionet QT Database (n=105 records)."
*   "Beats were matched with a 150ms tolerance window."

### Section 2: Results Table
| Metric | Our Model | Benchmark (Salvi 2011) | Status |
| :--- | :--- | :--- | :--- |
| **MAE (ms)** | 12.3 | 13.2 | **Pass** |
| **STD (ms)** | 8.7 | 10.5 | **Pass** |
| **Sensitivity** | 99.1% | 98.5% | **Pass** |

### Section 3: Visualizations
*   [Insert Bland-Altman Plot]
*   [Insert Regression Plot]

### Section 4: Interpretation
*   "The model demonstrates high agreement with expert annotations."
*   "Bias is negligible (-2.1ms) and not clinically significant."
*   "Performance exceeds the current literature benchmark."

---
**Related References:**
*   `../shared/statistical-methods.md`
*   `references/example-qt-validation.md`
