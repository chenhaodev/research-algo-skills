# Research Intake Questionnaire

This questionnaire is designed to assess the readiness and feasibility of a new digital measure project. Complete this assessment before initiating the project to identify gaps, risks, and resource needs.

**Date:** `[YYYY-MM-DD]`
**Project Name:** `[Project Name]`
**Lead Researcher:** `[Name]`

---

## Part 1: Research Strategy & Planning
*Focus: Clinical/Scientific Need & Context*

### 1. Concept of Interest
**Q1. What is the specific concept you want to measure?**
*Examples: Gait speed, sleep fragmentation, heart rate variability, tremor amplitude.*
- [ ] **Response:** `__________________________________________________`

**Q2. Why is this concept important to patients or stakeholders?**
*Does it reflect how a patient feels, functions, or survives?*
- [ ] **Response:** `__________________________________________________`

**Q3. What meaningful aspect of health does it relate to?**
- [ ] Activities of Daily Living (ADL)
- [ ] Quality of Life (QoL)
- [ ] Disease Burden / Symptom Severity
- [ ] Physiological Status / Biomarker
- [ ] Other: `____________________`

### 2. Context & Population
**Q4. What is your target population?**
*Specify disease, condition, age range, severity, and any exclusion criteria.*
- [ ] **Response:** `__________________________________________________`

**Q5. What is the intended context of use (COU)?**
- [ ] **Diagnostic:** Identifying a condition
- [ ] **Monitoring:** Tracking disease progression over time
- [ ] **Prognostic:** Predicting future outcomes
- [ ] **Response:** Measuring effect of a treatment (Endpoint)
- [ ] **Safety:** Monitoring adverse events

**Q6. Do you plan to seek regulatory acceptance (FDA, EMA, etc.)?**
- [ ] Yes (Requires strict adherence to V3/biomarker qualification frameworks)
- [ ] No (Exploratory/Internal use only)
- [ ] Undecided

### 3. Literature & Timeline
**Q7. Have you reviewed existing literature on this concept?**
- [ ] **Yes, extensive:** Validated measures exist.
- [ ] **Yes, partial:** Some evidence, but gaps exist.
- [ ] **No:** This is a novel concept.

**Q8. What is your timeline from concept to validation?**
- [ ] < 6 months
- [ ] 6-12 months
- [ ] 1-2 years
- [ ] > 2 years

---

## Part 2: Measurement Approach
*Focus: Technical Implementation*

### 4. Technology & Algorithms
**Q9. What sensor modalities are you considering?**
- [ ] **Wearable:** (e.g., Accelerometer, PPG, ECG)
- [ ] **Smartphone:** (e.g., GPS, screen interaction, microphone)
- [ ] **Clinical Device:** (e.g., Spirometer, pressure mat)
- [ ] **Ambient:** (e.g., Camera, radar, smart home)

**Q10. What is your proposed algorithm approach?**
- [ ] **Signal Processing:** (e.g., Filters, peaks, frequency analysis)
- [ ] **Rule-based:** (e.g., Thresholds, decision trees)
- [ ] **Machine Learning:** (e.g., Random Forest, SVM, Deep Learning)
- [ ] **Hybrid:** Combination of methods

### 5. Data Strategy
**Q11. What is your data collection plan?**
*Estimate sample size, duration per subject, and number of sites.*
- [ ] **Response:** `__________________________________________________`

**Q12. Do you have access to reference standards or "ground truth"?**
*Crucial for validation (e.g., Polysomnography for sleep, GaitRite for gait).*
- [ ] **Yes:** Gold standard available.
- [ ] **Partial:** Proxy measures or clinical rating scales available.
- [ ] **No:** Unsupervised or novel exploration.

---

## Part 3: Validation & Resources
*Focus: Feasibility & Risk*

### 6. Validation Plan
**Q13. What validation studies are planned?**
- [ ] **Analytical Validation:** Does the device measure the signal correctly? (Bench test)
- [ ] **Clinical Validation:** Does the measure reflect the clinical condition? (Patient study)
- [ ] **Usability Testing:** Can patients use the device correctly?

### 7. Resources & Risks
**Q14. What expertise is currently available on your team?**
- [ ] Clinical / Medical
- [ ] Data Science / Engineering
- [ ] Regulatory / Quality
- [ ] Clinical Operations

**Q15. What is your biggest uncertainty or risk?**
- [ ] **Technical:** Sensor reliability, battery life, data quality.
- [ ] **Clinical:** Patient adherence, variability of symptom.
- [ ] **Operational:** Recruitment, budget, timeline.
- [ ] **Regulatory:** Unclear pathway, evidence requirements.

---

## Part 4: Scoring & Interpretation

Review your responses to assess project readiness.

### Readiness Assessment

| Section | Green Flag (Ready) | Yellow Flag (Caution) | Red Flag (Stop & Review) |
| :--- | :--- | :--- | :--- |
| **Strategy** | Clear concept, defined COU, strong literature support. | Broad concept, undefined COU, limited literature. | Vague concept, no literature review, no clear patient benefit. |
| **Measurement** | Proven modality, access to ground truth, clear data plan. | Novel modality, proxy ground truth, complex ML required. | Unproven sensor, no ground truth, "black box" approach without plan. |
| **Validation** | Full validation plan (Analytical + Clinical), budget secured. | Partial validation plan, tight budget. | No validation plan, insufficient budget/team. |

### Action Plan

**If you have mostly Green Flags:**
*   **Action:** Proceed to **Phase 1: Definition** in the Research Strategy Skill.
*   **Next Step:** Draft your formal Concept of Interest (COI) and Context of Use (COU) statements.

**If you have Yellow Flags:**
*   **Action:** Pause to address gaps.
*   **Strategy Gaps:** Conduct a targeted literature review.
*   **Measurement Gaps:** Run a small proof-of-concept (POC) or pilot study.
*   **Validation Gaps:** Consult with a biostatistician or regulatory expert.

**If you have Red Flags:**
*   **Action:** **DO NOT START** data collection.
*   **Next Step:** Re-evaluate the core research question. Consider:
    *   Is there a simpler concept to measure?
    *   Can you use an existing validated measure instead of building a new one?
    *   Do you need to partner with an external vendor or academic group?

### Recommended Skills
*   **For Strategy Gaps:** See `research-strategy` (Phase 1 & 2)
*   **For Algorithm Decisions:** See `algorithm-selection-checklist` and `algo-development`
*   **For Validation Planning:** See `validation-framework`
