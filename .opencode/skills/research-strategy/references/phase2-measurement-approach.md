# Phase 2: Define Measurement Approach

This document details the methodology for **Phase 2** of the Research Strategy framework. Once the concept is defined (Phase 1), the focus shifts to the technical implementation: selecting sensors, designing algorithms, and planning validation.

## 1. Sensor Selection Methodology

Selecting the right hardware is a balance between data quality, patient burden, and operational feasibility.

### 1.1 Selection Criteria
Evaluate potential devices against these core requirements:

1.  **Modality**: Does the sensor capture the physical phenomenon defined in the ontology?
    *   *Example*: Accelerometer for movement, PPG for heart rate, GPS for mobility.
2.  **Form Factor & Wear Location**:
    *   *Wrist*: High compliance, good for sleep/activity. Noisy for gait.
    *   *Waist/Chest*: Better for gait/posture. Lower compliance.
    *   *Finger/Ring*: Good for PPG signal quality.
3.  **Sampling Rate & Dynamic Range**:
    *   *Requirement*: Nyquist theorem (sampling rate > 2x highest frequency of interest).
    *   *Example*: Tremor (4-6Hz) requires >12Hz (ideally >25Hz).
4.  **Battery Life & Data Storage**:
    *   Must support the intended wear protocol (e.g., 7 days continuous vs. nightly charging).
5.  **Data Access**:
    *   **Critical**: Access to raw sensor data (e.g., `.csv` of x,y,z acceleration) is preferred over proprietary processed metrics (e.g., "Activity Counts") for regulatory submission.

### 1.2 Detailed Sensor Comparison

| Sensor Type | Key Metrics | Pros | Cons | Ideal Use Case |
|-------------|-------------|------|------|----------------|
| **IMU (Accel/Gyro)** | Motion, Orientation, Vibration | Low power, robust, cheap. | No physiological data. | Activity, Sleep, Gait, Tremor. |
| **PPG (Optical)** | HR, HRV, SpO2, Resp Rate | Passive, familiar form factor. | Motion artifacts, skin tone bias. | Cardio, Stress, Sleep Stages. |
| **EDA (GSR)** | Skin Conductance (Sweat) | Direct measure of sympathetic arousal. | Very sensitive to environmental temp/humidity. | Stress, Pain, Seizures. |
| **GPS / Location** | Life Space, Mobility | High ecological validity. | Privacy concerns, battery drain, indoor signal loss. | Depression, Alzheimer's, QoL. |
| **Depth Camera / Lidar** | Gait, Posture, Fall Risk | Zero wear burden (ambient). | Privacy (cameras), limited to one room. | Frailty, Home monitoring. |

### 1.3 Sensor Evaluation Checklist

| Feature | Requirement | Pass/Fail | Notes |
|---------|-------------|-----------|-------|
| **Raw Data Access** | API or file export available? | | |
| **Battery Life** | > 24 hours (or study requirement)? | | |
| **Water Resistance** | IP67 or higher (shower/swim)? | | |
| **Biocompatibility** | ISO 10993 compliant materials? | | |
| **Data Security** | Encryption (AES-256)? HIPAA compliant? | | |
| **User Interface** | Simple for target population? | | |
| **Cost** | Fits within study budget? | | |
| **Regulatory Status** | 510(k) cleared (optional but helpful)? | | |

---

## 2. Algorithm Design Approaches

How to convert raw data into a clinical metric.

### 2.1 Approach Selection
*   **Rule-Based (Heuristic)**:
    *   *Description*: Explicit thresholds (e.g., "If acceleration > 1.5g, count as step").
    *   *Pros*: Transparent, explainable, easy to validate.
    *   *Cons*: Less robust to noise, may miss complex patterns.
*   **Machine Learning (ML)**:
    *   *Description*: Statistical models (Random Forest, SVM) trained on labeled data.
    *   *Pros*: High accuracy for complex signals.
    *   *Cons*: "Black box" risk, requires large training datasets.
*   **Deep Learning (DL)**:
    *   *Description*: Neural networks (CNN, LSTM) for raw signal processing.
    *   *Pros*: State-of-the-art performance, no manual feature engineering.
    *   *Cons*: Requires massive data, computationally expensive, hard to explain to regulators.

### 2.2 Development Pipeline
1.  **Preprocessing**:
    *   Filtering (Low-pass/High-pass) to remove noise/gravity.
    *   Normalization (z-score) to handle device variations.
2.  **Feature Extraction** (for Rule-based/ML):
    *   Time-domain: Mean, Variance, Zero-crossing rate.
    *   Frequency-domain: FFT, Power Spectral Density (PSD).
3.  **Model Training & Tuning**:
    *   Cross-validation (Leave-One-Subject-Out) to prevent overfitting.

### 2.3 Algorithm Logic Example (Pseudocode)
**Goal**: Detect "Scratch" events from Accelerometer data.

```python
def detect_scratch(accel_data, window_size=3.0):
    events = []
    # 1. Preprocessing: Bandpass filter (2-10Hz) to isolate scratch frequency
    filtered_data = bandpass_filter(accel_data, low=2.0, high=10.0)
    
    # 2. Sliding Window
    for window in sliding_window(filtered_data, window_size):
        # 3. Feature Extraction
        power = calculate_power(window)
        periodicity = calculate_autocorrelation(window)
        
        # 4. Classification (Rule-Based Example)
        if power > POWER_THRESHOLD and periodicity > PERIODICITY_THRESHOLD:
            events.append(window.timestamp)
            
    return merge_adjacent_events(events)
```

---

## 3. Data Collection Planning

Designing the study to collect the necessary data for algorithm development and validation.

### 3.1 Sample Size Calculation
*   **Rule of Thumb**: For ML, aim for at least 10-20 events per feature, or 30-50 subjects for initial feasibility.
*   **Diversity**: Ensure the sample covers the full spectrum of disease severity (mild, moderate, severe) and demographics (age, BMI, skin tone).

### 3.2 Annotation Protocol (Ground Truth)
The algorithm is only as good as the reference standard.

*   **Gold Standard**: The absolute truth (rarely exists).
*   **Clinical Comparator**: The current best practice.
    *   *Video Annotation*: Frame-by-frame coding of behavior (e.g., scratch, gait).
    *   *Expert Observation*: Clinician rating in real-time.
    *   *Provocation Tests*: Inducing the symptom (e.g., exercise for fatigue) to ensure events occur.

### 3.3 Feasibility Study Protocol Outline
**Title**: Observational Study to Collect Sensor Data for [Concept] in [Disease].

**Visit 1: Enrollment & Training**
*   Informed Consent.
*   Clinical assessments (Gold Standard scales).
*   Device fitting and training ("Teach-back" method).
*   First sync test.

**Home Monitoring Period (e.g., 7-14 days)**
*   Patient wears device 24/7.
*   Completes daily eDiaries (concurrent validity).
*   Remote monitoring dashboard checks for compliance.

**Visit 2: Close-out**
*   Device return.
*   Skin inspection (adverse events).
*   Usability questionnaire (SUS - System Usability Scale).
*   Debrief interview.

---

## 4. Validation Framework

Based on the V3 framework (Verification, Analytical Validation, Clinical Validation).

### 4.1 Verification (Sensor Performance)
*   **Question**: Does the sensor measure the physical quantity accurately?
*   **Test**: Compare sensor output (e.g., acceleration) to a calibrated reference (e.g., shaker table).

### 4.2 Analytical Validation (Algorithm Performance)
*   **Question**: Does the algorithm accurately detect the event?
*   **Metrics**:
    *   Sensitivity (True Positive Rate)
    *   Specificity (True Negative Rate)
    *   Accuracy / F1-Score
    *   Bland-Altman Plot (Bias and Limits of Agreement)

### 4.3 Clinical Validation (Clinical Relevance)
*   **Question**: Does the measure reflect the patient's health status?
*   **Tests**:
    *   **Convergent Validity**: Correlation with established clinical scales (e.g., Pearson's r > 0.5).
    *   **Known-Groups Validity**: Significant difference between healthy and diseased groups (t-test, p < 0.05).
    *   **Test-Retest Reliability**: Intraclass Correlation Coefficient (ICC) > 0.7.

---

## 5. Usability & Human Factors
Even the best algorithm fails if patients won't wear the device.

### 5.1 Usability Testing
*   **System Usability Scale (SUS)**: Standardized 10-item questionnaire. Score > 68 is "Average".
*   **Task Success Rate**: Can the patient charge/sync the device without help?
*   **Comfort Rating**: "On a scale of 1-5, how comfortable was the device to sleep in?"

### 5.2 Compliance Monitoring
*   **Definition**: What counts as a "valid day"? (e.g., > 10 hours of wear time).
*   **Monitoring**: Real-time dashboards to flag non-compliant patients for intervention calls.

---

## 6. Templates & Tools

### 6.1 Sensor Comparison Table Template
| Device | Form Factor | Battery | Raw Data? | Cost | Pros | Cons |
|--------|-------------|---------|-----------|------|------|------|
| Device A | Wrist | 7 days | Yes | $200 | Validated | Bulky |
| Device B | Ring | 2 days | No | $300 | Comfortable | Black box |

### 6.2 Algorithm Decision Tree
1.  **Is the signal periodic?**
    *   Yes (e.g., walking, breathing) -> Frequency analysis (FFT).
    *   No (e.g., falls, scratch) -> Event detection.
2.  **Is the signal distinct from noise?**
    *   Yes -> Rule-based thresholds.
    *   No -> Machine Learning classifier.

### 6.3 Data Management Plan Checklist
*   [ ] Data Dictionary defined (variable names, units, types).
*   [ ] Data Transfer Agreement (DTA) with vendors.
*   [ ] Privacy Impact Assessment (PIA) completed.
*   [ ] Backup and Disaster Recovery plan in place.

---

## Cross-References
*   **Previous Step**: Ensure the concept is defined in `phase1-concept-relevance.md`.
*   **Next Step**: Prepare for regulatory engagement in `phase3-regulatory-pathway.md`.
*   **Standards**: Refer to `../shared/clinical-validation-framework.md` for detailed statistical methods.
