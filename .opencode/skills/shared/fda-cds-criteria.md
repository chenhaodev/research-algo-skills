# FDA Clinical Decision Support (CDS) Criteria

This document outlines the criteria used by the FDA to determine if a software function is considered a "device" subject to regulation, specifically focusing on Clinical Decision Support (CDS) software.

**Reference:** FDA Guidance - Clinical Decision Support Software (September 2022)

## 1. The 4-Criteria Test (Non-Device CDS)

If a software function meets **ALL FOUR** of the following criteria, it is **NOT** considered a medical device and is therefore **exempt** from FDA regulation.

| Criterion | Description | Key Question |
| :--- | :--- | :--- |
| **1. Not for Processing Medical Images/Signals** | The function is NOT intended to acquire, process, or analyze a medical image or a signal from an in vitro diagnostic device or a pattern or signal from a signal acquisition system. | Does it analyze raw data (e.g., ECG waveforms, X-rays)? (If YES, it IS a device). |
| **2. Display/Analysis of Medical Information** | The function is intended for the purpose of displaying, analyzing, or printing medical information about a patient or other medical information (like peer-reviewed clinical studies and clinical practice guidelines). | Does it show standard medical data or guidelines? |
| **3. Support Recommendation (Not Direct Action)** | The function is intended for the purpose of supporting or providing recommendations to a health care professional about prevention, diagnosis, or treatment of a disease or condition. | Does it provide options/suggestions rather than a single, definitive output? |
| **4. Transparent Basis (Explanation)** | The function is intended for the purpose of enabling the health care professional to independently review the basis for such recommendations that such software presents so that it is not the intent that such health care professional rely primarily on any of such recommendations to make a clinical diagnosis or treatment decision. | Can the doctor see *why* the software made the suggestion (e.g., logic, citations)? |

### Summary
*   **Non-Device CDS:** Supports the doctor, explains its reasoning, uses standard data.
*   **Device CDS:** Analyzes complex signals/images, provides "black box" answers, or replaces the doctor's judgment.

---

## 2. Context of Use (COU)

Defining the Context of Use is critical for regulatory strategy and validation. It describes exactly how, where, and by whom the tool will be used.

### COU Components

1.  **Target Population:**
    *   Who is the patient? (Age, gender, disease stage, comorbidities).
    *   *Example:* Adults >18 with diagnosed Type 2 Diabetes on oral medication.
2.  **User:**
    *   Who uses the tool? (General practitioner, specialist, nurse, patient).
    *   *Example:* Cardiologists in an outpatient setting.
3.  **Clinical Setting:**
    *   Where is it used? (ICU, home, clinic, emergency room).
    *   *Example:* Home use for daily monitoring.
4.  **Clinical Input:**
    *   What data goes in? (Labs, vitals, patient-reported outcomes).
    *   *Example:* Heart rate, blood pressure, age, sex.
5.  **Output:**
    *   What does the tool produce? (Risk score, diagnosis, alert).
    *   *Example:* 5-year risk of cardiovascular event (Low/Medium/High).

---

## 3. Endpoint Acceptance Criteria (Digital Measures)

When developing digital biomarkers or endpoints, the FDA looks for specific evidence.

### 1. Analytical Validation (Does it measure correctly?)
*   **Accuracy:** Agreement with a gold standard.
*   **Precision:** Repeatability and reproducibility.
*   **Linearity:** Performance across the range of values.
*   **Interference:** Effect of noise or other factors.

### 2. Clinical Validation (Does it matter?)
*   **Association:** Is the measure linked to the clinical condition?
*   **Prediction:** Can it predict outcomes?
*   **Sensitivity to Change:** Does it change when the patient's status changes (e.g., after treatment)?

### 3. Patient Centricity
*   **Meaningfulness:** Does the measure reflect something important to the patient (e.g., ability to walk, sleep quality)?
*   **Usability:** Can patients use the device/app correctly?

---

## 4. Risk Categorization (IMDRF)

The level of regulation depends on the risk.

| State of Healthcare Situation | Treat or Diagnose (High Risk) | Drive Clinical Management (Med Risk) | Inform Clinical Management (Low Risk) |
| :--- | :--- | :--- | :--- |
| **Critical** | Class III | Class II | Class II |
| **Serious** | Class II | Class II | Class I |
| **Non-Serious** | Class II | Class I | Class I |

*   **Critical:** Life-threatening (e.g., stroke, sepsis).
*   **Serious:** Moderate progression (e.g., hypertension).
*   **Non-Serious:** Slow/manageable (e.g., headache).
