---
name: research-strategy
description: Strategic framework for developing digital measures from concept to regulatory endpoint. Guides the process of establishing concept relevance, defining measurement approaches, and navigating regulatory engagement (FDA CPIM) for Clinical Outcome Assessments (COAs) and Biomarkers.
version: 1.0.0
author: OpenCode
license: MIT
tags:
  - project strategy
  - digital measure
  - regulatory endpoint
  - concept of measure
  - COA design
  - CPIM
  - FDA endpoint
  - biomarker validation
  - meaningful aspect of health
---

# Research Strategy: Digital Measure Development

## Quick Reference

### The 3-Phase Framework
| Phase | Focus | Key Question | Primary Output |
|-------|-------|--------------|----------------|
| **1. Establish Concept Relevance** | Meaningfulness | *What is it?* | Validated Concept of Interest (COI) & Context of Use (COU) |
| **2. Define Measurement Approach** | Feasibility | *How to measure it?* | Sensor Selection, Algorithm Design, Verification Plan |
| **3. Regulatory Engagement** | Acceptance | *How to use it?* | Regulatory Feedback (CPIM), Validation Evidence, Endpoint Definition |

### Critical Path Summary
1.  **Identify Unmet Need**: What meaningful aspect of health is currently unmeasured?
2.  **Define Ontology**: Map the concept to a measurable phenomenon (e.g., "Itch" -> "Scratch" -> "Rhythmic Hand Movement").
3.  **Select Technology**: Choose sensors/devices capable of capturing the phenomenon.
4.  **Engage Stakeholders**: Validate relevance with patients, clinicians, and payers.
5.  **Seek Regulatory Advice**: Use FDA CPIM for early feedback on the measurement strategy.

### Key Terminology
*   **COI**: Concept of Interest - The thing we want to measure (e.g., sleep quality).
*   **COU**: Context of Use - The specific scenario where the measure is applied.
*   **MAH**: Meaningful Aspect of Health - A symptom or function that matters to the patient.
*   **COA**: Clinical Outcome Assessment - Measure of how a patient feels, functions, or survives.
*   **Biomarker**: Objective characteristic indicating a biological process.
*   **CPIM**: Critical Path Innovation Meeting - Non-binding FDA meeting for early guidance.

---

## When to Use This Skill

Activate this skill when the user asks to:
*   "Develop a strategy for a new digital biomarker."
*   "Plan the validation of a digital clinical outcome assessment (dCOA)."
*   "Prepare for an FDA Critical Path Innovation Meeting (CPIM)."
*   "Define the Context of Use (COU) for a wearable device."
*   "Map a clinical concept to a digital signal."
*   "Design a study to validate a novel digital endpoint."
*   "Understand the difference between a COA and a Biomarker in digital health."
*   "Create a roadmap for a digital endpoint qualification."

**Trigger Keywords**: `project strategy`, `digital measure`, `regulatory endpoint`, `concept of measure`, `COA design`, `CPIM`, `FDA endpoint`, `biomarker validation`, `meaningful aspect of health`.

---

## How to Use This Skill

1.  **Assess the Maturity**: Determine if the project is in the Concept (Phase 1), Measurement (Phase 2), or Regulatory (Phase 3) stage.
    *   *Is the concept defined?* -> Go to Phase 1.
    *   *Is the technology selected?* -> Go to Phase 2.
    *   *Is validation data available?* -> Go to Phase 3.
2.  **Apply the Framework**: Use the specific phase guidelines below to structure the work.
3.  **Draft Documentation**: Use the templates referenced in the `Shared Resources` section to create required artifacts (e.g., PICOS, Briefing Books).
4.  **Validate Alignment**: Ensure every technical decision traces back to the "Meaningful Aspect of Health" (MAH).
5.  **Prepare for Review**: Use the checklist in Phase 3 to prepare for regulatory interactions.

---

## Phase 1: Establish Concept Relevance (What is it?)

This phase focuses on defining the **Concept of Interest (COI)** and ensuring it represents a **Meaningful Aspect of Health (MAH)** for the patient population. The goal is to ensure we are measuring something that matters.

### 1.1 Define the Ontology
Mapping the abstract clinical concept to a concrete physical phenomenon is the foundation of digital measurement. This requires a clear line of sight from the patient's experience to the digital signal.

*   **Concept**: The patient's experience (e.g., "Itch", "Fatigue", "Tremor").
*   **Event**: The observable behavior or physiological change (e.g., "Scratch", "Gait Speed", "Hand shaking").
*   **Signal**: The digital representation of the event (e.g., "Rhythmic Accelerometer Data", "GPS Velocity", "Gyroscope Frequency").

**Ontology Mapping Example:**
| Level | Description | Example: Parkinson's | Example: Dermatitis |
|-------|-------------|----------------------|---------------------|
| **Concept** | Patient Experience | "I can't walk well." | "I itch all night." |
| **MAH** | Meaningful Aspect | Mobility / Independence | Sleep Quality / Comfort |
| **Event** | Observable Phenomenon | Gait Asymmetry | Scratching Behavior |
| **Metric** | Calculated Value | Step Time Variability (ms) | Scratch Duration (min/hour) |

### 1.2 Determine Context of Use (COU)
The COU defines the specific circumstances under which the measure is valid. A measure valid in one context may be invalid in another.

*   **Population**: Disease condition, severity, age, demographics.
    *   *Example*: "Adults with mild-to-moderate Alzheimer's disease."
*   **Setting**: Clinic, home, free-living, supervised.
    *   *Example*: "Unsupervised home environment during waking hours."
*   **Purpose**: Diagnostic, prognostic, response to treatment, safety.
    *   *Example*: "Secondary endpoint to evaluate improvement in physical function."

### 1.3 Stakeholder Engagement
Early engagement prevents "measuring the wrong thing."

**Patient Engagement Strategy:**
*   **Qualitative Interviews**: Conduct 1:1 interviews to understand the lived experience of the disease.
*   **Focus Groups**: Facilitate discussions to identify common themes and priorities.
*   **Survey Research**: Quantify the prevalence and burden of specific symptoms.

**Clinician & Payer Engagement:**
*   **Clinicians**: Verify clinical relevance and interpretation of the measure.
*   **Payers**: Assess the economic value and impact on healthcare utilization.

### 1.4 Literature Review Strategy
Conduct a systematic review to support the concept.
*   **Search Strategy**: Identify existing measures, validated scales, and known pathophysiology.
*   **Gap Analysis**: Determine why existing measures are insufficient (e.g., recall bias in surveys, "white coat" effect in clinic).
*   **Evidence Synthesis**: Compile evidence linking the digital signal to the clinical concept.

### 1.5 Concept Selection Matrix
Use this matrix to prioritize potential concepts.

| Criteria | High Priority | Low Priority |
|----------|---------------|--------------|
| **Clinical Impact** | Directly affects quality of life or survival. | Minor annoyance or cosmetic issue. |
| **Feasibility** | Proven sensor technology exists. | Requires novel/unproven hardware. |
| **Patient Burden** | Passive measurement (zero effort). | Active tasks requiring daily effort. |
| **Regulatory Precedent** | Similar endpoints accepted in other diseases. | Completely novel, no precedent. |

> **Reference**: See `references/phase1-concept-relevance.md` for interview guides and ontology templates.

---

## Phase 2: Define Measurement Approach (How to measure it?)

This phase translates the concept into a technical specification, selecting the right tools and algorithms. It bridges the gap between clinical need and engineering reality.

### 2.1 Sensor & Device Selection
Select hardware that can capture the signal with sufficient fidelity and patient compliance.

**Selection Criteria:**
1.  **Form Factor**: Wrist, chest patch, ring, ambient sensor, phone.
    *   *Constraint*: Must be wearable for the required duration (e.g., 24/7 vs. nightly).
2.  **Sensor Modality**: Accelerometer, gyroscope, PPG, ECG, GPS.
    *   *Requirement*: Must capture the physical phenomenon defined in the ontology.
3.  **Battery Life**: Must support the required duration of data collection without frequent charging.
4.  **Data Access**: Raw data access is often required for novel algorithm development.
    *   *Warning*: "Black box" algorithms from consumer devices are often unsuitable for regulatory submission.
5.  **Usability**: Burden on the patient must be minimized (comfort, aesthetics, ease of use).

**Sensor Evaluation Checklist:**
*   [ ] **Sampling Rate**: Is it high enough to capture the event? (e.g., >50Hz for tremor).
*   [ ] **Dynamic Range**: Can it capture the full range of motion/intensity?
*   [ ] **Storage Capacity**: Can it store data for the full study duration or sync reliably?
*   [ ] **Water Resistance**: Can patients shower/swim with it? (Critical for compliance).
*   [ ] **Biocompatibility**: Is the material safe for long-term skin contact?

### 2.2 Algorithm Design & Development
Develop the logic to convert raw sensor data into the clinical measure.

**Development Pipeline:**
1.  **Data Collection**: Gather a "Gold Standard" dataset.
    *   *Method*: Video annotation, expert observation, or concurrent established device.
2.  **Preprocessing**: Filtering, artifact removal, normalization.
3.  **Feature Extraction**: Identify signal characteristics (frequency, amplitude, periodicity).
4.  **Model Training**: Train machine learning or heuristic models.
    *   *Split*: Training set (70%), Validation set (15%), Test set (15%).
5.  **Verification**: Confirm the algorithm accurately detects the physical event (analytical validation).

### 2.3 Clinical Validation Strategy
Plan the study to prove the measure reflects the clinical concept.

**Validation Types:**
*   **Analytical Validation**: Does the device measure the physical parameter accurately? (e.g., steps = steps).
*   **Clinical Validation**: Does the measure reflect the patient's health status? (e.g., steps = mobility).

**Key Validity Metrics:**
*   **Convergent Validity**: Correlation with established scales (e.g., NRS for itch, UPDRS for Parkinson's).
*   **Known-Groups Validity**: Ability to distinguish between disease severities or healthy vs. diseased.
*   **Test-Retest Reliability**: Stability of the measure over time in stable patients.
*   **Sensitivity to Change**: Ability to detect treatment effects or disease progression.

### 2.4 Data Management & Privacy
*   **Data Flow**: Device -> App -> Cloud -> Analysis Platform.
*   **Security**: Encryption at rest and in transit.
*   **Compliance**: GDPR, HIPAA, 21 CFR Part 11 (electronic records).

> **Reference**: See `references/phase2-measurement-approach.md` for sensor evaluation matrices and validation study protocols.

---

## Phase 3: Regulatory Engagement & Validation (How to use it?)

This phase focuses on gaining regulatory acceptance for the measure as a drug development tool (DDT).

### 3.1 Regulatory Pathway Selection
Determine if the measure is a **Clinical Outcome Assessment (COA)** or a **Biomarker**.

**Classification Guide:**
*   **COA**: Measures how a patient feels, functions, or survives.
    *   *Patient-Reported Outcome (PRO)*: Patient answers questions.
    *   *Performance Outcome (PerfO)*: Patient performs a task (e.g., cognitive test).
    *   *Observer-Reported Outcome (ObsRO)*: Caregiver reports observations.
    *   *Clinician-Reported Outcome (ClinRO)*: Doctor reports observations.
*   **Biomarker**: Indicator of normal biological processes, pathogenic processes, or responses to an exposure.
    *   *Types*: Diagnostic, Monitoring, Pharmacodynamic/Response, Predictive, Prognostic, Safety, Susceptibility/Risk.

### 3.2 FDA Critical Path Innovation Meeting (CPIM)
The CPIM is a non-binding meeting to discuss novel methodologies with the FDA. It is often the first step in the regulatory journey.

**Purpose:**
*   Discuss the potential use of a novel biomarker or COA.
*   Get feedback on the validation plan.
*   Identify potential regulatory hurdles early.

**Preparation Steps:**
1.  **Draft Briefing Packet**: Summarize the unmet need, the proposed measure, and the validation plan.
    *   *Content*: Disease background, COU, Ontology, Technology, Validation Data (if available).
2.  **Submit Request**: Formal request to the FDA CDER/CBER.
3.  **The Meeting**: Present the strategy and receive feedback on the path to qualification.

### 3.3 Endpoint Definition
Formalize the measure into a specific study endpoint.

**Endpoint Components:**
1.  **Variable**: The specific metric (e.g., "Scratch Duration").
2.  **Timeframe**: The observation period (e.g., "Nightly from 10 PM to 6 AM").
3.  **Aggregation**: How data is combined (e.g., "Weekly Mean").
4.  **Population**: Who is being measured (e.g., "Intent-to-Treat Population").

**Example Endpoint Statement:**
"The primary endpoint is the change from baseline in the mean weekly nocturnal scratch duration (minutes) at Week 12."

### 3.4 Qualification Process (DDT)
For measures intended for widespread use, the Drug Development Tool (DDT) qualification process is appropriate.
1.  **Letter of Intent (LOI)**: Propose the concept and COU.
2.  **Qualification Plan (QP)**: Detailed validation protocol.
3.  **Full Qualification Package (FQP)**: Complete evidence dossier.

### 3.5 Regulatory Risk Assessment
Evaluate the risk profile of the proposed measure.

| Risk Factor | Low Risk | High Risk |
|-------------|----------|-----------|
| **Endpoint Hierarchy** | Exploratory Endpoint | Primary Endpoint |
| **Technology** | Established (e.g., Actigraphy) | Novel (e.g., Radar, Ingestible) |
| **Algorithm** | Transparent / Rule-based | Black Box / Deep Learning |
| **Context of Use** | Broad / General Population | Niche / Specific Sub-population |

> **Reference**: See `references/phase3-regulatory-engagement.md` for CPIM briefing book templates and FDA guidance summaries.

---

## Troubleshooting & Common Pitfalls

### Common Failure Modes
1.  **"Solution Looking for a Problem"**: Starting with a cool sensor instead of a patient need.
    *   *Fix*: Return to Phase 1 and validate the "Meaningful Aspect of Health."
2.  **"The Black Box Problem"**: Using proprietary algorithms that regulators cannot validate.
    *   *Fix*: Negotiate raw data access or develop open-source algorithms.
3.  **"Data Dump"**: Collecting terabytes of data without a plan to analyze it.
    *   *Fix*: Define the specific metrics and analysis plan *before* starting the study.
4.  **"Validation Mismatch"**: Validating in healthy volunteers but applying to sick patients.
    *   *Fix*: Ensure the validation study population matches the Context of Use (COU).

### Decision Support
*   **Q: Should we go for full DDT qualification or just use it in a single trial?**
    *   *A*: DDT qualification is resource-intensive (years) but adds value to the field. Single-trial use (Letter of Support) is faster but less transferable.
*   **Q: Can we use a consumer device (e.g., Apple Watch, Fitbit)?**
    *   *A*: Only if you can access the raw data or if the processed metric is already validated for your specific COU. Data ownership and long-term availability are key risks.

---

## Example: Nocturnal Scratch Case Study

This example illustrates the full lifecycle of a digital measure for Atopic Dermatitis.

### Phase 1: Concept
*   **Unmet Need**: Patients reported "nighttime itching" as the most burdensome symptom, disrupting sleep and quality of life. Existing surveys (NRS) suffered from recall bias.
*   **Ontology**: Itch (Symptom) -> Scratch (Behavior) -> Rhythmic Hand Movement (Signal).
*   **COU**: Pediatric and adult patients with moderate-to-severe Atopic Dermatitis in a home setting.
*   **Stakeholder Input**: Patients confirmed that reducing nighttime scratching would significantly improve their lives.

### Phase 2: Measurement
*   **Sensor**: Accelerometer on the dominant wrist (smartwatch).
*   **Algorithm**: Machine learning model (Random Forest) trained on video-annotated sleep data (IR cameras) to detect rhythmic movements characteristic of scratching.
*   **Validation**:
    *   *Analytical*: 90% sensitivity and specificity against video gold standard.
    *   *Clinical*: Strong correlation (r > 0.7) with patient-reported itch severity and sleep disturbance.

### Phase 3: Regulatory
*   **Engagement**: CPIM held to discuss the "scratch" measure as a surrogate for "itch."
*   **Feedback**: FDA acknowledged the potential but requested more data on the relationship between scratch duration and sleep fragmentation.
*   **Outcome**: FDA accepted "Nocturnal Scratch" as an exploratory endpoint, providing a roadmap for use as a primary endpoint in future trials upon further validation.

---

## Shared Resources

### Internal References
*   `../shared/fda-endpoint-criteria.md`: Checklist for FDA endpoint acceptance.
*   `../shared/picos-template.md`: Template for defining Population, Intervention, Comparator, Outcome, Study design.
*   `references/phase1-concept-relevance.md`: Detailed guide for Phase 1 (Ontology, Interviews).
*   `references/phase2-measurement-approach.md`: Detailed guide for Phase 2 (Sensors, Validation).
*   `references/phase3-regulatory-engagement.md`: Detailed guide for Phase 3 (CPIM, Qualification).

### External Standards
*   **FDA Guidance**: Patient-Focused Drug Development (PFDD) Guidance Series.
*   **V3 Framework**: Verification, Analytical Validation, Clinical Validation (DiMe Society).
*   **BEST Resource**: Biomarkers, EndpointS, and other Tools (FDA/NIH).

### Tools & Templates
*   **Ontology Mapper**: Tool for visualizing the Concept-Event-Signal chain.
*   **Sensor Selector**: Database of validated research-grade wearables.
*   **CPIM Briefing Book Template**: Standard structure for FDA meeting requests.

---

## Disclaimer

**Professional Judgment Required**: This skill provides a strategic framework based on general regulatory guidance and best practices. It does not constitute legal or regulatory advice. Every development program is unique; specific strategies must be tailored to the therapeutic area, patient population, and current regulatory landscape. Always consult with regulatory affairs professionals and subject matter experts.
