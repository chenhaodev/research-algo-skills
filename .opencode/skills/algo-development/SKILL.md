---
name: algo-development
description: Systematic approach to algorithm design, predictive biomarker selection, and model validation using academic literature and open-source toolboxes.
version: 1.0.0
license: Apache-2.0
---

# Algorithm Development & Predictive Biomarker Selection

## Quick Reference

| Phase | Action | Key Output | Tools |
| :--- | :--- | :--- | :--- |
| **1. Academic Research** | Search literature for proven methods | Candidate Algorithms List | PubMed, IEEE Xplore, Google Scholar |
| **2. Toolbox Research** | Find open-source implementations | Candidate Libraries List | GitHub, PyPI, Cargo, NPM |
| **3. Evaluation** | Score candidates against criteria | Scored Matrix (0-4) | Scoring Rubric, Evidence Checklist |
| **4. Selection** | Select best-fit algorithm | Final Algorithm Specification | Decision Matrix |
| **5. Validation** | Verify against evidence standards | Validation Report | 25-Item Evidence Checklist |

## When to Use This Skill

Use this skill when you need to:

*   **Design Predictive Algorithms:** Developing new models to predict clinical endpoints or physiological states.
*   **Select Biomarkers:** Identifying the most robust physiological signals (features) for a specific clinical application.
*   **Validate ML Models:** Ensuring a machine learning model meets rigorous clinical evidence standards before deployment.
*   **Evaluate Existing Solutions:** Assessing third-party algorithms or papers for reproducibility and clinical validity.
*   **Bridge Theory and Practice:** Translating academic findings into robust, deployable software implementations.

**Do NOT use this skill for:**
*   Simple data visualization (use `frontend-ui-ux`).
*   Basic statistical analysis without predictive modeling.
*   Infrastructure setup (use `dev-ops` or `cloud-arch`).

## How to Use This Skill

Follow this four-step workflow to ensure a rigorous, evidence-based approach to algorithm development.

### Phase 1: Academic Research Strategy

The goal is to identify algorithms with strong theoretical backing and clinical evidence.

#### 1. Search Resources
*   **Primary:** PubMed (Clinical focus), IEEE Xplore (Engineering focus).
*   **Secondary:** Google Scholar (Broad coverage), arXiv (Pre-prints).
*   **Venues:**
    *   *Journals:* Nature Medicine, JAMA, Lancet Digital Health, IEEE TBME.
    *   *Conferences:* NeurIPS, ICML, CVPR, EMBC.

#### 2. Search Query Construction
Combine **Methodological Keywords** with **Clinical Context**.

*   **Methodological Keywords:**
    *   `"Time-series analysis"`
    *   `"Spectral analysis"`
    *   `"Probability models"`
    *   `"Deep learning"`
    *   `"Feature extraction"`
*   **Clinical Keywords:**
    *   `"[Specific Disease/Condition]"` (e.g., "Atrial Fibrillation")
    *   `"[Clinical Guideline]"`
    *   `"[Clinical Endpoint]"` (e.g., "Readmission", "Mortality")
    *   `"Biomarker"`

**Example Query:**
> `("Time-series" OR "Deep learning") AND ("Atrial Fibrillation" OR "Arrhythmia detection") AND ("PPG" OR "ECG")`

#### 3. Filtering Criteria
Apply these filters to ensure quality and relevance:
*   **Citation Count:** > 100 citations in the last 3 years (indicates impact and community validation).
*   **Recency:** Published within the last 5 years (unless a seminal classic).
*   **Study Type:** Prioritize Prospective Studies and Randomized Controlled Trials (RCTs) over retrospective analysis.

### Phase 2: Toolbox Research Strategy

The goal is to find robust, maintained open-source implementations to accelerate development.

#### 1. Search Platforms
*   **Code Repositories:** GitHub, GitLab.
*   **Package Managers:**
    *   Python: `PyPI` (pip)
    *   JavaScript/TypeScript: `NPM`
    *   Rust: `Crates.io`

#### 2. Evaluation Criteria for Tools
Assess potential libraries using the **"MUCD"** framework:

*   **M - Maintenance:**
    *   Last commit within 6 months?
    *   Regular release cadence?
*   **U - Usage:**
    *   GitHub Stars > 500?
    *   Significant number of Forks?
    *   Used by other reputable projects?
*   **C - Community:**
    *   Active Issues/PRs?
    *   Responsive maintainers?
    *   Good documentation/examples?
*   **D - Developer Reputation:**
    *   Is the author/org known in the domain?
    *   Do they have other successful projects?

### Phase 3: Evaluation Criteria (Scoring System)

Score each candidate algorithm or paper on a scale of 0-4 based on the following binary criteria. Higher scores indicate a higher probability of successful clinical translation.

| Criterion | Description | Score |
| :--- | :--- | :--- |
| **1. Overfitting Resistance** | Validated on **RCT** or **Prospective** data? (Not just retrospective/synthetic). Uses proper train/test/validation splits? | +1 |
| **2. Physiological Rationale** | Is the method grounded in known **pathophysiology**? (Not a "black box" correlation). Does it make biological sense? | +1 |
| **3. Mathematical Proof** | Is there a formal proof of convergence, stability, or error bounds? Is the training/adaptation mechanism theoretically sound? | +1 |
| **4. Code Accessibility** | Is the source code **open-source** and available? Can results be reproduced without reinventing the wheel? | +1 |

**Decision Thresholds:**
*   **Score 4:** Prime candidate. Adopt immediately.
*   **Score 3:** Strong candidate. Proceed with caution (verify missing attribute).
*   **Score < 3:** High risk. Avoid unless no other options exist.

### Phase 4: Evidence Checklist (The 25-Item Standard)

Use this checklist to validate the final design or evaluate a completed study. Based on the *Evidence Checklist for Digital Health Technologies*.

#### Section 1: Study Definition
1.  **Title:** Does it identify the study design, population, and technology?
2.  **Abstract:** Structured summary (Background, Methods, Results, Conclusions).
3.  **Rationale:** Scientific background and explanation of the gap this study fills.

#### Section 2: Methods
4.  **Ethics:** IRB/Ethics committee approval and informed consent confirmed.
5.  **Protocol:** Was the protocol published or registered (e.g., ClinicalTrials.gov)?
6.  **Participants:** Eligibility criteria, setting, and location described.
7.  **Sample Size:** How was the sample size determined? (Power analysis?).

#### Section 3: Technology Specifications
8.  **Sensor Make/Model:** Precise identification of hardware used.
9.  **Sensor Placement:** Where on the body? How was it attached?
10. **Algorithm Version:** Specific version number or commit hash.
11. **Algorithm Description:** Input data, processing steps, output definition.
12. **User Interface:** Description of what the user/clinician sees.

#### Section 4: Execution
13. **Outcomes:** Primary and secondary endpoints clearly defined.
14. **Data Collection:** How was data acquired, stored, and managed?
15. **Reference Standard:** What is the "Ground Truth"? (e.g., Holter monitor, expert annotation).
16. **Blinding:** Were assessors blinded to the algorithm results?
17. **Statistical Analysis:** Methods used to compare algorithm vs. reference.

#### Section 5: Reporting
18. **Flow Diagram:** Participant flow (enrolled, allocated, followed-up, analyzed).
19. **Demographics:** Baseline characteristics of the study population.
20. **Findings:** Estimates of diagnostic accuracy (Sensitivity, Specificity, AUC, PPV/NPV) with Confidence Intervals.
21. **Adverse Events:** Any side effects or issues reported?
22. **Usability:** User feedback or adherence data.

#### Section 6: Interpretation
23. **Summary:** Key findings in context of the hypothesis.
24. **Comparison:** How does this compare to existing literature?
25. **Limitations:** Honest assessment of bias, generalizability, and errors.

## Example: Predictive Biomarker Selection Workflow

**Scenario:** Developing an algorithm to detect Sleep Apnea from PPG signals.

**1. Academic Research:**
*   *Query:* `("Sleep Apnea" OR "OSA") AND ("Photoplethysmography" OR "PPG") AND "Deep Learning"`
*   *Result:* Found "Paper A" (CNN based, 200 citations) and "Paper B" (Feature engineering, 50 citations).
*   *Filter:* Paper A is recent (2022) and high impact.

**2. Toolbox Research:**
*   *Search:* GitHub for "PPG sleep apnea".
*   *Result:* Found `py-ppg-sleep` (Stars: 120, Last update: 2 weeks ago) and `sleep-net` (Stars: 10, Last update: 3 years ago).
*   *Selection:* `py-ppg-sleep` selected for evaluation.

**3. Evaluation (Scoring "Paper A"):**
*   *Overfitting:* Used retrospective MIMIC-III data (0 points - prefer prospective).
*   *Physiological:* Explains correlation between SpO2 drops and PPG amplitude (1 point).
*   *Math:* Standard CNN, no specific proof for this domain (0 points).
*   *Code:* GitHub link provided and working (1 point).
*   *Total Score:* 2/4 (Risky. Need to validate on own prospective data).

**4. Evidence Check (Gap Analysis):**
*   *Missing:* "Sensor Placement" not specified in Paper A.
*   *Action:* Define strict sensor placement protocol for our implementation.

## Detailed Reference: Algorithm Categories

### 1. Time-Series Analysis
*   **Use Case:** Continuous monitoring (ECG, PPG, EEG).
*   **Key Techniques:**
    *   Fourier Transform (FFT) / Wavelets.
    *   Autoregression (AR/ARIMA).
    *   Dynamic Time Warping (DTW).
    *   Recurrent Neural Networks (RNN/LSTM/GRU).

### 2. Spectral Analysis
*   **Use Case:** Frequency-domain features (HRV, Tremor analysis).
*   **Key Techniques:**
    *   Power Spectral Density (PSD).
    *   Coherence analysis.
    *   Time-frequency distributions.

### 3. Probability Models
*   **Use Case:** Risk stratification, diagnosis.
*   **Key Techniques:**
    *   Bayesian Networks.
    *   Hidden Markov Models (HMM).
    *   Gaussian Processes.
    *   Logistic Regression (Baseline).

## Best Practices for Implementation

### Data Management
*   **Raw Data:** Always preserve raw sensor data immutable.
*   **Versioning:** Version control both Code AND Data (e.g., DVC).
*   **Annotation:** Use standardized tools for ground-truth labeling.

### Validation Strategy
*   **Cross-Validation:** Use k-fold cross-validation for small datasets.
*   **Hold-out Set:** STRICT separation of Test set (never seen during training).
*   **External Validation:** Test on a completely different dataset (different hospital, different device) to prove generalizability.

### Documentation
*   **Algorithm Description Document (ADD):** Detailed technical spec.
*   **User Manual:** Instructions for data collection.
*   **Validation Report:** Statistical performance summary.

## Common Pitfalls

*   **Data Leakage:** Features in training data that contain information about the target (e.g., future data, patient ID).
*   **Overfitting:** Model learns noise instead of signal. (Fix: Regularization, more data, simpler model).
*   **Selection Bias:** Training data does not represent the target population.
*   **"Black Box" Trust:** Deploying deep learning models without explainability (SHAP/LIME) in clinical settings.

## Related Skills
*   `data-science`: For general data manipulation and exploration.
*   `python-dev`: For implementation details.
*   `clinical-validation`: For deeper dive into trial design.

## References & Further Reading
*   [academic-research-strategy.md](./references/academic-research-strategy.md)
*   [toolbox-research.md](./references/toolbox-research.md)
*   [evaluation-criteria.md](./references/evaluation-criteria.md)
*   [evidence-checklist.md](./references/evidence-checklist.md)

---
*Trigger Keywords: algorithm development, predictive biomarker, machine learning, evidence checklist, model selection, algorithm design, biomarker validation, clinical AI, digital health validation.*
