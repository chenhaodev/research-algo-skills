# Case Study: Nocturnal Scratching as a Digital Endpoint

**Project:** Development of a Novel Digital Endpoint for Atopic Dermatitis
**SOP Reference:** SOP-R-1 (Concept Development)
**Duration:** 12 Months
**Status:** Completed (Positive FDA Feedback)

---

## 1. Project Overview

**Clinical Context:** Atopic Dermatitis (AD) is characterized by intense itching (pruritus).
**Problem:** Current measurements rely on patient recall (e.g., "How itchy were you yesterday?"), which is subjective and prone to recall bias. Patients often scratch during sleep without realizing it.
**Goal:** Develop an objective, device-based measure of **Nocturnal Scratching** to serve as a Clinical Outcome Assessment (COA) in Phase 3 trials.

---

## 2. Phase 1: Concept Development (Months 1-3)

*Objective: Define what we are measuring and why it matters to patients.*

### 2.1 Patient Interviews (Qualitative Research)
We conducted semi-structured interviews with **N=25** patients (15 adults, 10 pediatric/parents).

*   **Key Finding 1:** "The itching is worst at night. I wake up with blood on the sheets but don't remember scratching."
*   **Key Finding 2:** "Poor sleep due to scratching ruins my next day—I can't focus at work/school."
*   **Conclusion:** Nocturnal scratching is a **Meaningful Aspect of Health (MAH)** because it directly impacts sleep quality and daily functioning.

### 2.2 Literature Review
*   **Search:** PubMed query `("atopic dermatitis"[MeSH] AND "pruritus"[MeSH] AND "actigraphy")`.
*   **Results:** 47 relevant papers.
*   **Gap Analysis:** Most studies used generic "activity counts" which correlate poorly with specific scratching movements. Need a specific "scratch detection" algorithm.

### 2.3 Concept Definition & Ontology
We formalized the concept to ensure consistent measurement:

| Term | Definition |
| :--- | :--- |
| **Scratch Bout** | A distinct event of rhythmic skin contact movement lasting $\ge 1.0$ seconds. |
| **Rhythmicity** | Frequency range of 0.5 – 3.0 Hz (distinct from restless tossing). |
| **Sleep Opportunity** | The period between "lights out" (intent to sleep) and "lights on" (intent to wake). |

**Proposed Endpoint:** "Total Scratch Duration (minutes) during the Total Sleep Opportunity."

---

## 3. Phase 2: Measurement Approach (Months 4-9)

*Objective: Build and validate the tool.*

### 3.1 Sensor Selection
*   **Device:** Wrist-worn accelerometer (GeneActiv).
*   **Specs:** 3-axis, +/- 8g range, 32 Hz sampling rate (sufficient to capture 3 Hz scratch motion).
*   **Placement:** Dominant hand (captures ~80% of scratching) or both hands (ideal but higher burden). *Decision: Both hands for validation, Dominant only for feasibility.*

### 3.2 Algorithm Development
*   **Method:** Supervised Machine Learning (Random Forest).
*   **Features:**
    *   Variance of acceleration (Energy).
    *   Dominant frequency (FFT peak).
    *   Autocorrelation (Rhythmicity).
*   **Training Data:** 10 subjects wearing devices + video recording in sleep lab.

### 3.3 Validation Study (The "Gold Standard")
*   **Protocol:** N=50 nights of concurrent video + accelerometer data.
*   **Annotation:** Trained human raters marked start/stop of scratching on video.
*   **Performance:**
    *   **Epoch-by-epoch Sensitivity:** 85%
    *   **Epoch-by-epoch Specificity:** 92%
    *   **Cohen's $\kappa$:** 0.82 (Strong agreement).

### 3.4 Feasibility Study
*   **Protocol:** N=30 patients used the device at home for 7 nights.
*   **Compliance:** 94% of nights had valid data.
*   **User Feedback:** "Wristbands were comfortable, but I forgot to push the 'bedtime' button sometimes."
*   **Adjustment:** Implemented an automated "sleep period detection" algorithm as a backup.

---

## 4. Phase 3: Regulatory Engagement (Months 10-12)

*Objective: Get FDA buy-in for use in drug trials.*

### 4.1 CPIM Preparation
We prepared a **Critical Path Innovation Meeting (CPIM)** briefing packet.
*   **Content:** Concept model, literature summary, validation results (video vs. device), and proposed context of use.
*   **Ask:** "Does the Agency agree that Nocturnal Scratching is a valid COA for Atopic Dermatitis?"

### 4.2 FDA Feedback
*   **Classification:** FDA agreed it is a **COA** (specifically, a Performance Outcome or ObsRO depending on interpretation, but definitely *not* a biomarker).
*   **Critical Feedback:** "You must demonstrate that a reduction in scratching is not just due to **sedation**."
    *   *Implication:* If a drug knocks the patient out, they scratch less, but that's not treating the itch.
    *   *Requirement:* We must measure "Sleep Architecture" or "Daytime Sleepiness" concurrently to rule out sedation.

### 4.3 Endpoint Refinement
Based on feedback, we finalized the endpoints:
*   **Primary:** Total Scratch Duration (minutes).
*   **Secondary:** Percent of Sleep Time spent Scratching.
*   **Safety Control:** Daytime sleepiness score (ESS).

---

## 5. Lessons Learned

1.  **Patient-Centricity is Key:** We originally thought about "scratch intensity" (g-force), but patients told us "duration" (how long it keeps me awake) was what mattered. This simplified the engineering significantly.
2.  **"Night" is Ambiguous:** Defining "Total Sleep Opportunity" was critical. Without it, a patient sleeping 4 hours vs. 8 hours would have non-comparable scratch totals.
3.  **The Sedation Trap:** We missed the regulatory concern about sedation. Always ask: "Could my digital measure improve for the wrong reason?"
4.  **Early Engagement:** The CPIM meeting saved us from running a Phase 3 trial with a rejected endpoint.

---

## 6. Timeline & Resources

| Phase | Duration | Team | Budget (Est.) |
| :--- | :--- | :--- | :--- |
| **Concept** | 3 Months | 1 Clinical Lead, 1 UX Researcher | $50k (Recruitment) |
| **Measurement** | 6 Months | 2 Data Scientists, 1 Engineer | $300k (Devices, Lab) |
| **Regulatory** | 3 Months | 1 Regulatory Affairs, 1 Tech Writer | $150k (Consultants) |
| **Total** | **12 Months** | **~5 FTEs** | **~$500k** |

---

## 7. References Used

*   **Framework:** `research-strategy/SKILL.md`
*   **Interview Guides:** `research-strategy/references/phase1-concept-relevance.md`
*   **Regulatory Process:** `research-strategy/references/phase3-regulatory-pathway.md`
*   **Criteria:** `shared/fda-cds-criteria.md`
