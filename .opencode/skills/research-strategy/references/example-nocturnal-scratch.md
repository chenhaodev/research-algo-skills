# Case Study: Nocturnal Scratch in Atopic Dermatitis

This case study illustrates the end-to-end application of the Research Strategy framework, from identifying an unmet need to regulatory engagement.

## 1. Background & Unmet Need

**Condition**: Atopic Dermatitis (AD) is a chronic inflammatory skin disease characterized by intense itching (pruritus).

**The Problem**:
*   Itch is the most burdensome symptom reported by patients.
*   Current measurement relies on the Peak Pruritus Numerical Rating Scale (NRS), a daily recall question ("On a scale of 0-10, how itchy were you?").
*   **Limitations**:
    *   **Recall Bias**: Patients struggle to accurately remember itch intensity, especially during sleep.
    *   **Sleep Disruption**: Patients report that *nighttime* scratching is the most destructive aspect, causing sleep fragmentation and daytime fatigue.
    *   **Subjectivity**: "Itch" is a sensation; "Scratch" is the behavior. Treatments might reduce the *need* to scratch (sedation) without fixing the skin, or vice versa.

**Objective**: Develop an objective, passive measure of nocturnal scratching behavior to complement patient-reported itch scores.

---

## 2. Phase 1: Concept Relevance

### 2.1 Stakeholder Engagement
*   **Patient Interviews**: 20 adults and 15 pediatric caregivers.
    *   *Key Insight*: Patients described a "vicious cycle" of itch-scratch-wake. Many were unaware of how much they scratched while asleep, relying on blood on sheets or partner reports as evidence.
    *   *Analogy*: One patient compared it to "orthopnea" in heart failure—a physical sign (sleeping propped up) that reflects the severity of the condition.
*   **Clinician Input**: Dermatologists confirmed that reduction in excoriations (skin damage from scratching) is a key treatment goal.

### 2.2 Ontology Definition
We needed to map the subjective "Itch" to a measurable signal.

*   **Concept**: Itch (Pruritus).
*   **Meaningful Aspect of Health**: Restful Sleep / Skin Integrity.
*   **Event**: Scratching (repetitive movement of the hand against skin).
*   **Signal**: Rhythmic, oscillatory acceleration of the wrist.

**Refined Definition**:
"Rhythmic and repetitive skin contact movement of the dominant hand lasting > 3 seconds, occurring during the Total Sleep Opportunity (TSO)."

### 2.3 Context of Use (COU)
*   **Population**: Moderate-to-severe Atopic Dermatitis (Adults & Pediatrics > 6yo).
*   **Setting**: Home environment, unsupervised, during sleep.
*   **Placement**: Accelerometer on the dominant wrist (or both wrists if dominance is ambiguous).

---

## 3. Phase 2: Measurement Approach

### 3.1 Sensor Selection
*   **Requirement**: High sampling rate to capture the frequency of scratching (typically 3-8 Hz).
*   **Selection**: Research-grade actigraph (GeneActiv or similar) and consumer smartwatch (Apple Watch) for comparison.
*   **Settings**: 50 Hz sampling rate, +/- 8g dynamic range.

### 3.2 Algorithm Development
*   **Data Collection**: 30 patients slept in a lab with IR video cameras (Gold Standard) and wrist sensors.
*   **Annotation**: Trained raters marked start/stop times of scratch events in the video.
*   **Model**: Random Forest classifier using features like:
    *   Variance of acceleration.
    *   Dominant frequency (FFT).
    *   Autocorrelation (periodicity).
*   **Performance**:
    *   Sensitivity: 88%
    *   Specificity: 92%
    *   Correlation with video duration: r = 0.95.

### 3.3 Clinical Validation
*   **Study**: 100 patients monitored at home for 2 weeks.
*   **Results**:
    *   **Convergent Validity**: Moderate correlation (r = 0.6) with NRS Itch scores. (Note: This was expected; perception vs. behavior).
    *   **Known-Groups**: Differentiated mild vs. severe patients (p < 0.01).
    *   **Sensitivity to Change**: Detected reduction in scratching 2 days *before* patients reported reduction in itch (leading indicator).

**Data Table: Validation Results**
| Metric | Mild AD (n=30) | Severe AD (n=30) | p-value |
|--------|----------------|------------------|---------|
| **NRS Itch (0-10)** | 3.2 ± 1.1 | 7.8 ± 1.4 | <0.001 |
| **Scratch Duration (min/night)** | 12.5 ± 5.2 | 45.8 ± 15.3 | <0.001 |
| **Sleep Efficiency (%)** | 88% | 72% | <0.01 |

---

## 4. Phase 3: Regulatory Pathway

### 4.1 Strategy
*   **Classification**: Biomarker (Safety/Efficacy) or COA?
    *   *Decision*: **COA (Performance Outcome)** because it measures a voluntary (though often subconscious) motor behavior reflecting the patient's state.
*   **Engagement**: FDA CPIM requested.

### 4.2 CPIM Execution
*   **Briefing Packet**: Highlighted the "disconnect" between patient perception (NRS) and reality (Scratch). Argued that Scratch is a more objective measure of treatment effect.
*   **FDA Feedback**:
    *   **Positive**: Acknowledged the value of an objective nocturnal measure.
    *   **Concern**: "Is a reduction in scratch due to less itch, or due to sedation (side effect)?"
    *   **Guidance**: Must measure **Sleep Quality** concurrently to prove that scratch reduction leads to *better sleep*, not just *less movement*.

### 4.3 Outcome
*   **Endpoint Accepted**: "Percent Time Scratching during Total Sleep Opportunity" accepted as an **Exploratory Endpoint**.
*   **Path to Primary**: FDA requested a longitudinal study showing that changes in scratch predict long-term skin healing (EASI score) better than NRS.

---

## 5. Key Learnings

1.  **Terminology Matters**: We initially called it "Digital Itch." FDA rejected this, as "Itch" is a sensation. We renamed it "Nocturnal Scratch," which was accepted.
2.  **The Sedation Trap**: In dermatology, antihistamines reduce scratching by knocking the patient out. The digital measure must distinguish "calm sleep" from "sedated immobility."
3.  **Patient-Centricity**: The most powerful argument in the CPIM was the patient quotes about the trauma of waking up with bloody sheets. This grounded the technical discussion in human reality.

## 6. Results Summary

| Metric | Outcome |
|--------|---------|
| **Concept** | Validated as highly meaningful to patients. |
| **Measure** | High accuracy (r=0.95) against video gold standard. |
| **Regulatory** | Accepted as Exploratory Endpoint; clear path to Secondary. |
| **Impact** | Now standard in Phase 2/3 AD trials to demonstrate objective efficacy. |
