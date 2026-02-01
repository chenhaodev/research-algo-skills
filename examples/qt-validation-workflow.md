# Case Study: Validation of AI-ECG QTc Algorithm

**Project:** Validation of Automated QT Interval Measurement for Drug Safety
**SOP Reference:** SOP-R-4 (Validation Protocol)
**Duration:** 4 Weeks
**Status:** Validation Passed

---

## 1. Project Overview

**Objective:** Validate our proprietary AI algorithm (`AI-ECG-QTc`) for measuring the QT interval on single-lead ECGs.
**Use Case:** Remote monitoring of patients taking QT-prolonging medications (e.g., certain antibiotics, anti-arrhythmics).
**Regulatory Requirement:** Accuracy must be comparable to standard manual measurement (Mean Absolute Error < 15 ms).

---

## 2. Step 1: Protocol Design (Week 1)

*Objective: Define the rules of the game before playing.*

*   **Reference Standard:** The **Physionet QT Database (QTDB)**. It contains 105 records with "Gold Standard" annotations by two cardiologists.
*   **Sample Size:** 105 subjects $\times$ 30 beats/subject = **3,150 QT intervals**.
*   **Metrics:**
    1.  **Mean Absolute Error (MAE):** Target < 15 ms.
    2.  **Bland-Altman Plot:** Assess bias across heart rates.
    3.  **Correlation (Pearson's r):** Target > 0.90.
*   **Benchmarks:**
    *   *Charbit et al. (2006):* MAE ~15 ms (Human inter-observer variability).
    *   *AliveCor (FDA Cleared):* Comparable device performance.

---

## 3. Step 2: Data Preparation (Weeks 1-2)

*Objective: Get the data ready for the algorithm.*

We used the `wfdb` library to access the Physionet data.

```python
import wfdb
import numpy as np

def load_qt_data(record_name):
    # Load signal
    record = wfdb.rdrecord(f'qtdb/{record_name}')
    signal = record.p_signal[:, 0]  # Lead I
    
    # Load annotations (Gold Standard)
    annotation = wfdb.rdann(f'qtdb/{record_name}', 'pu1')
    
    return signal, annotation
```

**Process:**
1.  Downloaded all 105 records.
2.  Extracted random 10-30s strips to avoid selection bias.
3.  Aligned the "Gold Standard" timestamps (P-onset, T-offset) with our signal.

---

## 4. Step 3: Algorithm Execution (Week 2)

*Objective: Run the test.*

We ran the `AI-ECG-QTc` model on the prepared dataset.

```python
# Pseudocode for batch processing
results = []

for subject in all_subjects:
    signal, true_qt = load_qt_data(subject)
    
    # Run our algorithm
    pred_qt_start, pred_qt_end = ai_ecg_qtc.predict(signal)
    pred_qt_duration = (pred_qt_end - pred_qt_start) / fs * 1000  # in ms
    
    results.append({
        'subject': subject,
        'true_qt': true_qt,
        'pred_qt': pred_qt_duration
    })
```

---

## 5. Step 4: Statistical Analysis (Week 3)

*Objective: Crunch the numbers.*

We calculated the key metrics using the `results` list.

### 5.1 Quantitative Results
*   **Mean Absolute Error (MAE):** 12.3 ms
    *   *Result:* **PASS** (Target < 15 ms).
*   **Standard Deviation (STD):** 8.7 ms.
*   **Correlation:** $r = 0.94$ ($p < 0.001$).
*   **Paired T-test:** $p = 0.082$.
    *   *Interpretation:* No statistically significant difference between Algorithm and Human.

### 5.2 Bland-Altman Analysis
*   **Bias:** -2.1 ms (Algorithm slightly underestimates).
*   **Limits of Agreement (95%):** [-25.3, 21.1] ms.
*   **Plot Observation:** The bias is consistent across the range of QT intervals (no "proportional bias").

```python
import matplotlib.pyplot as plt

diff = qt_predicted - qt_actual
mean_diff = np.mean(diff)
std_diff = np.std(diff)

plt.scatter((qt_predicted + qt_actual)/2, diff)
plt.axhline(mean_diff, color='red', label='Bias')
plt.axhline(mean_diff + 1.96*std_diff, color='red', linestyle='--', label='95% LoA')
plt.title('Bland-Altman Plot: AI vs. Cardiologist')
```

---

## 6. Step 5: Benchmarking (Week 3)

*Objective: Compare against the field.*

| Method | MAE (ms) | Notes |
| :--- | :--- | :--- |
| **Our Algorithm** | **12.3** | Validated on QTDB |
| Charbit (2006) | 15.0 | Human vs. Human variability |
| Salvi (2011) | 13.2 | Standard automated method |
| FDA Threshold | ~15-20 | General acceptance criteria |

**Conclusion:** Our algorithm performs better than the average human variability and is equivalent to state-of-the-art automated methods.

---

## 7. Step 6: Reporting (Week 4)

*Objective: Document for stakeholders.*

We compiled the **Validation Report (VR-QT-001)** containing:
1.  **Methods:** Detailed description of the Physionet QT Database and sampling strategy.
2.  **Results:** Summary tables and the Bland-Altman plot.
3.  **Discussion:**
    *   Acknowledged the -2.1 ms bias (negligible clinical impact).
    *   Highlighted robustness against noise (tested on noisy segments).
4.  **Conclusion:** "The AI-ECG-QTc algorithm is suitable for drug safety monitoring purposes."

---

## 8. Lessons Learned

1.  **Gold Standards aren't Gold:** Even cardiologists disagree. The "15 ms" benchmark exists because humans vary by that much. Don't try to beat the ground truth perfectly—you might just be overfitting to one annotator's style.
2.  **Bland-Altman is King:** A simple correlation coefficient ($r=0.94$) hides bias. The Bland-Altman plot showed us exactly *how* we differed (a constant offset), which is easier to fix than a proportional error.
3.  **Real-World Drop:** In the lab, we got 12.3 ms. In our subsequent beta test with real patients (more motion artifacts), MAE rose to ~18 ms. This is normal; always buffer your expectations.

---

## 9. References Used

*   **Methodology:** `review-validation/SKILL.md`
*   **Metrics:** `review-validation/references/validation-protocol.md`
*   **Case Study:** `review-validation/references/example-qt-validation.md`
*   **Stats:** `shared/statistical-methods.md`
