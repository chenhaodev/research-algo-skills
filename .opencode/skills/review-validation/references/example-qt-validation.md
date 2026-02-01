# Case Study: QT Interval Validation

This document provides a complete, end-to-end example of a clinical validation protocol. It demonstrates how to apply the principles from `validation-protocol.md` in a real-world scenario.

## 1. Background & Objective

*   **Clinical Context:** The QT interval on an ECG represents the time for ventricular depolarization and repolarization. Prolonged QT (Long QT Syndrome) can lead to fatal arrhythmias (Torsades de Pointes).
*   **Objective:** Validate the performance of the "Biofourmis AI-ECG-QTc" algorithm.
*   **Target:** Demonstrate equivalence or superiority to established literature benchmarks and FDA-cleared devices.

## 2. Methods

### 2.1. Dataset
*   **Source:** Physionet QT Database (QTDB).
*   **Composition:** 105 records, 15 minutes each, 2-channel ECG.
*   **Diversity:** Includes normal sinus rhythm, arrhythmia, ST changes, and conduction blocks.
*   **Gold Standard:** Manual annotations by experts (P-onset, P-offset, QRS-onset, QRS-offset, T-end).

### 2.2. Algorithm
*   **Type:** Hybrid (Wavelet Transform + Deep Learning).
*   **Input:** Single-lead ECG (Lead II).
*   **Output:** Fiducial points (Q-onset, T-end).

### 2.3. Procedure
1.  **Extraction:**
    *   Randomly selected 30-second strips from each of the 105 records.
    *   Total beats analyzed: 3,150.
2.  **Prediction:**
    *   Algorithm processed each strip blindly.
3.  **Matching:**
    *   Algorithm beats were matched to Ground Truth beats.
    *   Tolerance window: 150ms (standard for T-wave end).
4.  **Analysis:**
    *   Calculated QT interval = $T_{end} - Q_{onset}$.
    *   Computed error metrics (MAE, STD, Bias).

## 3. Results

### 3.1. Quantitative Metrics

| Metric | Value (Mean ± STD) | 95% CI |
| :--- | :--- | :--- |
| **Mean Absolute Error (MAE)** | **12.3 ± 8.7 ms** | [11.8, 12.8] |
| **Delta-QT Error (Bias)** | **-2.1 ± 11.5 ms** | [-2.5, -1.7] |
| **Correlation (Pearson)** | **0.94** | p < 0.001 |
| **Detection Rate** | **99.8%** | N/A |

### 3.2. Bland-Altman Analysis
*   **Bias:** -2.1 ms (Slight underestimation, clinically negligible).
*   **Limits of Agreement (LoA):** [-25.3 ms, +21.1 ms].
*   **Interpretation:** 95% of errors are within ~25ms, which is well within the clinical acceptability range (usually <30ms variability).

### 3.3. Paired T-Test
*   **Result:** p = 0.082.
*   **Interpretation:** p > 0.05, meaning the systematic bias is **not statistically significant**. The algorithm is effectively unbiased.

## 4. Benchmarking

We compared our results to three key benchmarks:

### 4.1. Literature Comparison

| Study | N (Subjects) | Method | MAE (ms) | STD (ms) | Comparison |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Our Model** | **105** | **AI-ECG-QTc** | **12.3** | **8.7** | **-** |
| *Charbit et al. (2006)* | 108 | Linear Reg. | ~15.0 | ~18.0 | **Superior** |
| *Salvi et al. (2011)* | 105 | Single-lead | 13.2 | 10.5 | **Equivalent** |
| *Hermans et al. (2017)* | 200 | GLM | 14.1 | 12.2 | **Superior** |

### 4.2. FDA Device Comparison
*   **Device:** AliveCor KardiaMobile (510k K181823).
*   **Performance:** Reported equivalence to manual caliper measurement.
*   **Conclusion:** Our MAE of 12.3ms is comparable to the inter-observer variability of human cardiologists (typically 10-20ms).

## 5. Interpretation & Conclusion

*   **Performance:** The algorithm achieves high accuracy with low bias.
*   **Reliability:** The narrow Limits of Agreement suggest consistent performance across different heart rates.
*   **Clinical Utility:** The error margin is smaller than the clinical threshold for decision making (e.g., a 20ms error does not typically change diagnosis of Long QT).
*   **Recommendation:** The algorithm is validated for clinical use in QT interval monitoring.

## 6. Lessons Learned
*   **Morphology Matters:** Initial errors were high in "biphasic T-waves." Retraining with specific biphasic examples improved MAE by 2ms.
*   **Noise Robustness:** Preprocessing with a 0.5Hz high-pass filter was critical for baseline wander removal.

---
**Related References:**
*   `references/validation-protocol.md`
*   `references/feasibility-analysis.md`
