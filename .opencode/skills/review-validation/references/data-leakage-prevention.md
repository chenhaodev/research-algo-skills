# Data Leakage Prevention

**CRITICAL WARNING:** Data leakage is the most common cause of failure in Medical AI. A model with data leakage will perform perfectly in the lab and fail disastrously in the clinic.

## 1. What is Data Leakage?

Data leakage occurs when information from the **Test Set** is inadvertently included in the **Training Set**. This allows the model to "memorize" the answer instead of learning the underlying pathology.

### Common Causes
1.  **Signal-Segment Splitting (The "Sin"):** Splitting a single patient's recording into segments and distributing them randomly.
2.  **Improper Cross-Validation:** Normal `KFold` instead of `GroupKFold`.
3.  **Data Contamination:** Preprocessing (e.g., normalization) applied to the whole dataset *before* splitting.

## 2. The Golden Rule: Patient ID Splitting

**ALWAYS split by Subject/Patient ID.**

### Incorrect: Signal-Segment Splitting
*   *Scenario:* Patient A has a 1-hour ECG. You cut it into 60 one-minute segments.
*   *Split:* Randomly put 48 segments in Train, 12 segments in Test.
*   *Result:* The model sees Patient A's heart rate, noise profile, and specific morphology in Training. It recognizes "Patient A" in the Test set.
*   *Outcome:* Inflated Accuracy (e.g., 99%). Real-world generalization is near zero.

### Correct: Subject-Level Splitting
*   *Scenario:* You have 100 Patients.
*   *Split:* Put Patients 1-80 in Train. Put Patients 81-100 in Test.
*   *Result:* The model has NEVER seen the biological signals of Patients 81-100.
*   *Outcome:* Realistic Accuracy (e.g., 85%). This reflects clinical performance.

## 3. Implementation Guide

### 3.1. Python (sklearn)
Use `GroupKFold` or `LeaveOneGroupOut`.

```python
from sklearn.model_selection import GroupKFold

# X = Features, y = Labels
# groups = Array of Patient IDs corresponding to each sample
groups = [1, 1, 1, 2, 2, 3, 3, 4, 4, 4] 

gkf = GroupKFold(n_splits=5)

for train_idx, test_idx in gkf.split(X, y, groups=groups):
    # Verify independence
    train_patients = set(groups[train_idx])
    test_patients = set(groups[test_idx])
    
    assert len(train_patients.intersection(test_patients)) == 0
    print("Split verified: No patient overlap.")
```

### 3.2. Best Practices Checklist
*   [ ] **Identify Patient ID:** Do not assume filename is unique. Look for metadata like `subject_id`.
*   [ ] **Check for Duplicates:** Some public datasets contain the same patient under different record names.
*   [ ] **Report Split Method:** Explicitly state "Subject-independent split" in your report.
*   [ ] **Report Counts:** State "N=1000 samples from M=50 patients."

## 4. Case Studies

### 4.1. Apnea-ECG Database
*   **Stats:** 70 records, 32 subjects.
*   **The Trap:** Many papers treat this as 70 independent samples.
*   **Impact:**
    *   *Leakage Split:* ~95-100% Accuracy.
    *   *Correct Split:* ~79-87% Accuracy.
*   **Lesson:** If you see >95% on Apnea-ECG, check the methodology. It's likely flawed.

### 4.2. PTB Diagnostic ECG Database
*   **Stats:** 549 records, 290 subjects.
*   **The Trap:** Multiple records per patient (e.g., different dates).
*   **Impact:** High correlation between records of the same patient.
*   **Lesson:** Must group by `patient_id` from the header file, not just record name.

## 5. Detection Methods

How to spot leakage in your own work or others':

1.  **Performance is "Too Good":** AUC > 0.99 is rarely real in complex medical tasks.
2.  **Training vs. Validation Gap:** If Train Acc is 99% and Val Acc is 99%, but External Test Acc is 60%, you have leakage in the Validation set.
3.  **Visual Inspection:** Plot the features. If Test points cluster tightly around specific Training points, you might be memorizing patients.

---
**Related References:**
*   `references/validation-protocol.md`
*   `../shared/data-quality-checklist.md`
