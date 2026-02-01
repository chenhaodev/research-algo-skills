# Phase 1: Establish Concept Relevance

This document details the methodology for **Phase 1** of the Research Strategy framework. The primary objective is to define a **Concept of Interest (COI)** that represents a **Meaningful Aspect of Health (MAH)** for the target patient population.

## 1. Literature Review Methodology

A systematic literature review is the first step to understand the current landscape of measurement and identify unmet needs. This process should be rigorous and reproducible.

### 1.1 Search Strategy Protocol
Conduct a structured search using databases like PubMed, Embase, PsycINFO, and IEEE Xplore (for technical feasibility).

**Step 1: Define Search Strings**
Construct Boolean queries combining three domains:
1.  **Population**: "Atopic Dermatitis" OR "Eczema" OR "Pruritus"
2.  **Concept**: "Itch" OR "Scratch" OR "Sleep Quality" OR "Restlessness"
3.  **Technology**: "Wearable" OR "Sensor" OR "Actigraphy" OR "Digital Biomarker" OR "ePRO"

*Example Query*: `("Atopic Dermatitis" OR "Eczema") AND ("Scratch" OR "Itch") AND ("Wearable" OR "Accelerometer" OR "Mobile App")`

**Step 2: Screening Process**
*   **Level 1 (Title/Abstract)**: Screen for relevance. Discard clearly irrelevant papers (e.g., drug mechanism of action without measurement focus).
*   **Level 2 (Full Text)**: Assess against inclusion/exclusion criteria.

**Inclusion Criteria**:
*   Published in the last 10 years (unless seminal work).
*   Focus on clinical measurement, patient experience, or sensor validation.
*   English language.
*   Human subjects (or relevant animal models for sensor validation).

**Exclusion Criteria**:
*   Purely technical engineering papers without clinical context.
*   Reviews (use these for citation tracking, but extract data from primary sources).
*   Conference abstracts with insufficient detail.

### 1.2 Citation Tracking & Grey Literature
*   **Forward Chaining**: Use Google Scholar or Web of Science to see who cited the key papers. This finds the most recent developments.
*   **Backward Chaining**: Review the reference lists of key papers to find foundational studies.
*   **Grey Literature**: Search ClinicalTrials.gov for ongoing studies using similar endpoints. Search FDA/EMA qualification opinions.

### 1.3 Gap Analysis Framework
Systematically evaluate existing measures to identify the "Why":

| Limitation Type | Description | Example |
|-----------------|-------------|---------|
| **Subjectivity** | Reliance on patient memory or interpretation. | "Recall bias in weekly itch recall." |
| **Episodic** | Measurement occurs only during clinic visits. | "6-minute walk test only captures capacity, not performance at home." |
| **Burden** | High patient effort leading to missing data. | "Daily 30-minute diary has 40% drop-out rate." |
| **Sensitivity** | Inability to detect small but meaningful changes. | "Scale has floor/ceiling effects." |
| **Ecological Validity** | Clinic performance doesn't match real life. | "White coat effect improves adherence temporarily." |

---

## 2. Stakeholder Engagement

Engaging stakeholders early ensures the concept is relevant and the measurement approach is feasible. This is a requirement for Patient-Focused Drug Development (PFDD).

### 2.1 Patient Interviews (Concept Elicitation)
Qualitative research is essential to define the MAH.

**Methodology**:
*   **Format**: Semi-structured 1:1 interviews (30-60 minutes).
*   **Sample Size**: Saturation is typically reached with 15-20 patients per sub-group (e.g., mild vs. severe).
*   **Recruitment**: Diverse representation (age, gender, race, disease severity, socioeconomic status).
*   **Analysis**: Thematic analysis using coding software (e.g., NVivo, Dedoose).

**Detailed Interview Guide**:

**Part 1: Lived Experience**
*   "Tell me about a typical day living with [Condition]. Walk me through from when you wake up to when you go to sleep."
*   "What are the most difficult things you have to do? What can't you do anymore?"
*   "If you could wave a magic wand and fix one symptom, what would it be?"

**Part 2: Symptom Deep Dive**
*   "You mentioned [Symptom]. Describe what that feels like."
*   "How does [Symptom] change throughout the day?"
*   "What triggers it? What makes it better?"

**Part 3: Current Measurement**
*   "How do you explain this symptom to your doctor? Do they understand?"
*   "Do you track it? (Apps, notes, mental check)."
*   "What is frustrating about the current way your doctor measures this?"

**Part 4: Digital Concept Feedback**
*   "We are thinking of using a [Device Type] to measure [Concept]. What are your initial thoughts?"
*   "Would you wear a watch to bed every night? What would make that hard?"
*   "What would you want to see from the data?"

### 2.2 Cognitive Debriefing
Once a draft measure (e.g., a PRO question or a device instruction) exists, test it with patients.
*   "In your own words, what is this question asking?"
*   "Is this instruction clear? How would you rephrase it?"

### 2.3 Clinician Surveys & Advisory Boards
Validate the clinical significance of the patient-identified concepts.

**Key Questions for KOLs (Key Opinion Leaders)**:
*   "Does [Concept] correlate with disease progression or structural damage?"
*   "Would objective data on [Concept] influence your treatment decisions (e.g., switch meds, change dose)?"
*   "What is the minimum clinically important difference (MCID) you would expect to see?"
*   "Are there any safety concerns with this measurement approach?"

### 2.4 Payer & HTA Input
Assess the value proposition for reimbursement.
*   "Does improving [Concept] reduce healthcare utilization (e.g., hospitalizations, ER visits, surgeries)?"
*   "Is this measure accepted for reimbursement decisions in other diseases?"
*   "What evidence would you need to see to pay for a drug that improves this endpoint?"

---

## 3. Meaningful Aspects of Health (MAH) Framework

The MAH framework connects the patient's voice to the clinical endpoint. It ensures we don't just measure "what is easy" but "what matters."

### 3.1 The Hierarchy of Measurement
1.  **Concept of Interest (COI)**: The broad domain (e.g., Physical Function).
2.  **Meaningful Aspect of Health (MAH)**: The specific aspect that matters to the patient (e.g., Ability to walk independently to the grocery store).
3.  **Concept of Measurement**: What is actually measured (e.g., Walking speed, Maximum distance).
4.  **Endpoint**: The statistical variable used in the trial (e.g., Change in mean daily walking speed from baseline to Week 12).

### 3.2 Concept Mapping Examples

**Example 1: Parkinson's Disease**
*   **Observation**: Dopamine depletion in basal ganglia.
*   **Perception**: "I feel stiff and slow."
*   **Experience**: "It takes me forever to button my shirt or walk to the bathroom."
*   **Behavior (MAH)**: Fine motor control / Gait.
*   **Digital Signal**: Keypress latency (smartphone) / Stride length variability (accelerometer).

**Example 2: Heart Failure**
*   **Observation**: Reduced Ejection Fraction.
*   **Perception**: "I get out of breath easily."
*   **Experience**: "I can't walk up the stairs to my bedroom."
*   **Behavior (MAH)**: Physical Capacity.
*   **Digital Signal**: Steps per day / Vertical displacement (barometer).

**Example 3: Depression**
*   **Observation**: Neurotransmitter imbalance.
*   **Perception**: "I feel heavy and don't want to move."
*   **Experience**: "I stay in bed all day; I don't see my friends."
*   **Behavior (MAH)**: Social Isolation / Psychomotor Retardation.
*   **Digital Signal**: GPS homestay duration / Call & text frequency / Step count.

---

## 4. Ontology Definition

A precise ontology is required to translate the clinical concept into a technical specification. This prevents ambiguity between engineering and clinical teams.

### 4.1 Defining the Phenomenon
*   **What is it?**: Define the event in physical terms.
    *   *Vague*: "Tremor."
    *   *Precise*: "Rhythmic, oscillatory movement of the hand at 4-6 Hz (Rest) or 6-9 Hz (Postural)."
*   **Where is it?**: Anatomical location.
    *   *Example*: "Dominant wrist" vs. "Lumbar spine (L3)."
*   **When does it happen?**: Contextual timing.
    *   *Example*: "At rest, not during voluntary movement" vs. "During gait."
*   **How long?**: Duration constraints.
    *   *Example*: "Must persist for > 3 seconds to be counted."

### 4.2 The Concept-Event-Signal Chain
Ensure a clear line of sight.

1.  **Concept**: The clinical symptom (e.g., Sleep Disturbance).
2.  **Event**: The observable physical manifestation (e.g., Awakening / Movement).
3.  **Signal**: The raw sensor data (e.g., Accelerometer magnitude > threshold).
4.  **Feature**: The extracted mathematical property (e.g., Zero-crossing rate).
5.  **Metric**: The aggregated value (e.g., Total Sleep Time).

---

## 5. Context of Use (COU) Definition

The COU defines the boundaries of your measure. A measure is not "validated" in the abstract; it is validated for a specific COU.

### 5.1 COU Template

| Component | Description | Example |
|-----------|-------------|---------|
| **Disease** | Specific condition and subtype. | Parkinson's Disease (Idiopathic). |
| **Population** | Demographics, severity, comorbidities. | Hoehn & Yahr Stage 1-3, Ambulatory, Age > 45. |
| **Setting** | Where the measure is used. | Unsupervised home environment (free-living). |
| **Tool** | The specific device/app. | Apple Watch Series 6+ with "TremorApp" v1.0. |
| **Endpoint Positioning** | How the data is used. | Exploratory efficacy endpoint. |

### 5.2 Defining the "Target Population"
*   **Inclusion Criteria**: Who is in? (e.g., Smartphone users, English speakers).
*   **Exclusion Criteria**: Who is out? (e.g., Patients with other movement disorders, skin allergies to silicone).
*   **Variability**: Consider how disease heterogeneity affects the signal (e.g., does tremor vary by time of day?).

---

## 6. Concept Selection Matrix

Use this matrix to prioritize which concepts to develop into digital measures. Score each criterion (1-5) to rank opportunities.

| Criterion | Weight | Description | Score (1-5) |
|-----------|--------|-------------|-------------|
| **Patient Relevance** | High (x3) | Is this a top 3 symptom for patients? | |
| **Clinical Significance** | High (x3) | Does it predict outcomes or track progression? | |
| **Measurability** | Med (x2) | Can it be captured by existing sensors? | |
| **Usability/Burden** | Med (x2) | Can it be measured passively or with low burden? | |
| **Regulatory Precedent** | Low (x1) | Has FDA/EMA accepted similar endpoints? | |
| **Commercial Value** | Low (x1) | Does it support differentiation or reimbursement? | |
| **Technical Risk** | Med (x2) | Is the algorithm novel (high risk) or established? | |

**Scoring Guide**:
*   **5 (Excellent)**: Top priority for patients, proven technology, clear regulatory path.
*   **1 (Poor)**: Low patient interest, requires unproven hardware, high regulatory risk.

**Decision Thresholds**:
*   **Score > 45**: Green Light. Proceed to Phase 2.
*   **Score 30-45**: Yellow Light. Requires mitigation (e.g., feasibility study).
*   **Score < 30**: Red Light. Stop or pivot.

---

## 7. Templates & Tools

### 7.1 Concept Definition Template
*   **Name of Concept**:
*   **Target Population**:
*   **Meaningful Aspect of Health**:
*   **Proposed Measurement Approach**:
*   **Hypothesis**: "We hypothesize that [Measure] will correlate with [Clinical Scale] and reflect changes in [MAH]."
*   **Risk Assessment**:
    *   *Clinical Risk*:
    *   *Technical Risk*:
    *   *Regulatory Risk*:

### 7.2 Stakeholder Interview Summary Form
*   **Stakeholder Type**: (Patient/Clinician/Payer)
*   **Key Themes Identified**:
    1.
    2.
    3.
*   **Quotes**:
*   **Implications for Measurement**:
*   **Action Items**: (e.g., "Need to adjust sensor placement based on patient feedback.")

---

## Cross-References
*   **Next Step**: Proceed to `phase2-measurement-approach.md` to select sensors and define algorithms.
*   **Regulatory Context**: See `phase3-regulatory-pathway.md` for how these concepts feed into the CPIM briefing book.
*   **Example**: See `example-nocturnal-scratch.md` for a real-world application of this ontology.
