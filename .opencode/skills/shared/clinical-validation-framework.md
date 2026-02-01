# Clinical Validation Framework

Validation is the process of demonstrating that a medical device or algorithm performs as intended. It is typically divided into two main phases: Analytical Validation and Clinical Validation.

## Phase 1: Analytical Validation (Technical Performance)

**Goal:** Prove that the algorithm processes the input data correctly and reliably. Does the tool measure what it claims to measure?

### Key Metrics
1.  **Accuracy:** How close is the measurement to the true value (Gold Standard)?
    *   *Metric:* Mean Absolute Error (MAE), Root Mean Square Error (RMSE), Bias.
2.  **Precision:** How consistent are the measurements?
    *   *Metric:* Standard Deviation (SD), Coefficient of Variation (CV).
3.  **Reliability:** Does it work under different conditions?
    *   *Test:* Repeatability (same user, same device) vs. Reproducibility (different users, different devices).
4.  **Linearity/Range:** Does it work across the entire expected physiological range?
    *   *Test:* Test at low, medium, and high values.
5.  **Robustness:** Can it handle noise, artifacts, or missing data?
    *   *Test:* Signal-to-noise ratio (SNR) tests.

### Study Design (Analytical)
*   **Subjects:** Can often use healthy volunteers or simulators.
*   **Sample Size:** Typically smaller than clinical trials (e.g., n=30-50).
*   **Environment:** Controlled laboratory setting.
*   **Comparator:** High-fidelity reference standard (e.g., Mass Spectrometry for glucose, Polysomnography for sleep).

---

## Phase 2: Clinical Validation (Clinical Utility)

**Goal:** Prove that the algorithm provides meaningful information for the target patient population in the intended use environment. Does it improve health outcomes?

### Key Concepts
1.  **Clinical Accuracy:** Does the output correlate with the clinical condition?
    *   *Metric:* Sensitivity, Specificity, Positive Predictive Value (PPV), Negative Predictive Value (NPV), Area Under the Curve (AUC).
2.  **Context of Use (COU):** Validation must occur in the actual setting (e.g., home, clinic).
3.  **Target Population:** Must include the intended diversity (age, gender, ethnicity, disease severity).

### Study Design (Clinical)
*   **Subjects:** Patients with the target condition.
*   **Sample Size:** Power calculation required (often n=100s or 1000s).
*   **Environment:** Real-world or simulated real-world.
*   **Comparator:** Clinical Gold Standard (e.g., Expert diagnosis, Biopsy).

### Types of Clinical Studies
1.  **Retrospective:** Using existing datasets. Good for initial training and testing.
    *   *Risk:* Selection bias, data quality issues.
2.  **Prospective Observational:** Collecting new data without intervening.
    *   *Benefit:* Better data quality, real-world evidence.
3.  **Randomized Controlled Trial (RCT):** Comparing intervention group to control group.
    *   *Benefit:* Highest level of evidence, proves causality.

---

## Validation Protocol Template

A good validation protocol should include:

1.  **Objective:** Clear statement of what is being tested.
2.  **Endpoints:** Primary and secondary performance metrics with acceptance criteria (e.g., "Sensitivity > 80%").
3.  **Study Population:** Inclusion/Exclusion criteria.
4.  **Sample Size Calculation:** Statistical justification for the number of subjects.
5.  **Data Collection:** Procedures, devices used, reference standards.
6.  **Statistical Analysis Plan (SAP):** How data will be cleaned, analyzed, and reported.
7.  **Blinding:** How bias will be minimized (e.g., annotators blinded to algorithm output).

---

## Common Pitfalls

*   **Data Leakage:** Training and testing on the same patients (see `data-quality-checklist.md`).
*   **Spectrum Bias:** Validating only on severe cases (easier to detect) and missing mild cases.
*   **Gold Standard Errors:** Assuming the reference standard is perfect (it rarely is).
*   **Overfitting:** Algorithm works perfectly on training data but fails in the real world.
