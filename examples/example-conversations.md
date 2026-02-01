# Example Conversations

This document provides a collection of example conversations demonstrating how to effectively use the R&D Planning Skills. These examples cover various scenarios, from quick definitions to complex multi-stage workflows.

## Table of Contents

1. [Example 1: Quick Question (Research Strategy)](#example-1-quick-question-research-strategy)
2. [Example 2: Workflow Question (Algorithm Development)](#example-2-workflow-question-algorithm-development)
3. [Example 3: Troubleshooting (Review & Validation)](#example-3-troubleshooting-review--validation)
4. [Example 4: Multi-Skill Workflow (End-to-End)](#example-4-multi-skill-workflow-end-to-end)
5. [Example 5: Advanced Usage (Regulatory Strategy)](#example-5-advanced-usage-regulatory-strategy)

---

## Example 1: Quick Question (Research Strategy)

**Scenario:** A user needs to clarify regulatory terminology for a new project proposal.

**User:** What's the difference between a COA and a biomarker for FDA purposes?

**Assistant:** [Triggers `research-strategy` skill]

A **Clinical Outcome Assessment (COA)** measures how a patient feels, functions, or survives. It is a direct measure of the patient's health status.
-   **Patient-Reported Outcome (PRO):** Patient's own perspective (e.g., pain scale).
-   **Clinician-Reported Outcome (ClinRO):** Clinician observation (e.g., tumor size on scan interpreted by radiologist).
-   **Observer-Reported Outcome (ObsRO):** Non-clinician observer (e.g., parent reporting on infant's sleep).
-   **Performance Outcome (PerfO):** Standardized task (e.g., 6-minute walk test).

A **Biomarker** is an indicator of biological or pathogenic processes, or response to an exposure or intervention.
-   **Diagnostic:** Detects or confirms presence of disease.
-   **Prognostic:** Identifies likelihood of a clinical event or disease progression.
-   **Predictive:** Identifies individuals more likely to respond to an intervention.

For digital measures, the classification often depends on **what you are measuring**:
-   If it measures *patient function or feeling* (e.g., sleep quality, physical activity capability) → **COA**
-   If it measures a *biological process* (e.g., heart rate, skin conductance) → **Biomarker**

**Example: Nocturnal scratching in atopic dermatitis**
-   **Scratching** = behavior affecting sleep quality and daily function → **COA**
-   **Skin conductance** = physiological marker of inflammation or stress → **Biomarker**

**Reference:** See `references/phase3-regulatory-pathway.md` for detailed classification criteria and the FDA's "BEST (Biomarkers, EndpointS, and other Tools) Resource".

---

## Example 2: Workflow Question (Algorithm Development)

**Scenario:** A data scientist needs to start a new project on heart rate variability (HRV) and wants a structured approach.

**User:** I need to find and evaluate algorithms for heart rate variability analysis. Walk me through the process.

**Assistant:** [Triggers `algo-development` skill]

I'll guide you through the complete workflow for selecting and evaluating HRV algorithms. This follows our standard Algorithm Development SOP.

**Step 1: Academic Research** (see `references/academic-research-strategy.md`)

First, we need to identify the state-of-the-art methods. I recommend the following search strategy on PubMed and IEEE Xplore:

```text
("heart rate variability"[MeSH] OR HRV[Title/Abstract]) 
AND ("machine learning"[MeSH] OR "deep learning"[Title/Abstract] OR "signal processing")
AND ("validation"[Title/Abstract] OR "clinical"[MeSH])
Filters: Publication date 2020-2024, Impact Factor > 4.0
```

**Key things to look for:**
-   **Preprocessing:** How do they handle artifacts/noise? (e.g., ectopic beat correction).
-   **Features:** Time-domain (SDNN, RMSSD) vs. Frequency-domain (LF/HF ratio) vs. Non-linear (Poincaré plot).
-   **Validation:** Did they use a public dataset (e.g., MIT-BIH)?

**Step 2: Toolbox Research**

Don't reinvent the wheel. Look for existing, well-maintained libraries.
*   **Search:** GitHub for "HRV analysis python", "ECG processing".
*   **Evaluation Criteria:**
    *   **Maintenance:** Last commit < 6 months?
    *   **Documentation:** Are there tutorials and API docs?
    *   **Testing:** Is there high test coverage?
    *   **Citations:** Is the library used in peer-reviewed papers?

*Potential Candidates:* `NeuroKit2`, `pyHRV`, `HeartPy`.

**Step 3: Evaluation & Scoring**

Create a scoring matrix (rows = algorithms/libraries, columns = criteria).
*   **Accuracy:** Performance on benchmark datasets.
*   **Computational Cost:** Can it run on your target device?
*   **Interpretability:** Can you explain *why* a metric changed?
*   **License:** Is it compatible with our commercial goals (e.g., MIT/Apache vs. GPL)?

**Step 4: Implementation & Testing**

1.  **Baseline:** Implement the top candidate library.
2.  **Data:** Use the Physionet MIT-BIH Normal Sinus Rhythm Database for initial testing.
3.  **Metric:** Calculate RMSSD and compare against the library's example outputs to ensure correctness.

**User:** That's helpful. Which library do you usually recommend for Python?

**Assistant:**
For general research and robust processing, **NeuroKit2** is currently the top recommendation.
*   **Pros:** Excellent documentation, comprehensive pipeline (cleaning -> peak detection -> HRV calculation), active maintenance.
*   **Cons:** Can be slower than optimized C++ implementations for real-time use.

If you need real-time processing on edge devices, **HeartPy** is often better optimized for noisy, real-world sensor data (PPG/ECG).

---

## Example 3: Troubleshooting (Review & Validation)

**Scenario:** A validation study for a step-counting algorithm failed to meet the target accuracy.

**User:** Our latest validation run for the step counter showed a MAPE of 15%, but our target is <10%. The error seems high during sedentary periods. How should we investigate?

**Assistant:** [Triggers `review-validation` skill]

A Mean Absolute Percentage Error (MAPE) of 15% with issues during sedentary periods suggests a **False Positive** problem—the algorithm is counting non-walking movements (like hand gestures) as steps.

Here is a troubleshooting protocol based on `review-validation/SKILL.md`:

**1. Error Analysis (Stratification)**
Break down the error by activity type.
*   **Action:** Generate a confusion matrix or error plot specifically for "Sedentary/Hand Movements" vs. "Walking".
*   **Hypothesis:** You will likely see a high step count during activities like typing, gesticulating, or eating.

**2. Visual Inspection**
*   **Action:** Pull 5-10 examples of "high error" files. Plot the raw accelerometer data (X, Y, Z) alongside the algorithm's "step detected" markers.
*   **Look for:** Low-amplitude, high-frequency noise (typical of typing) triggering the threshold.

**3. Threshold Tuning**
*   If the issue is indeed false positives during low-intensity movement:
    *   **Check:** Is your minimum amplitude threshold too low?
    *   **Check:** Are you using a frequency filter? (Walking is typically 1-3 Hz; typing might be higher).
    *   **Recommendation:** Try increasing the minimum peak prominence or adding a "minimum duration of rhythmic movement" constraint (e.g., must detect 3 steps in 2 seconds to start counting).

**4. Re-Validation**
*   Do **not** just optimize on the test set.
*   Split your "Sedentary" data into Dev/Test.
*   Adjust parameters on Dev.
*   Verify on Test to ensure you haven't introduced False Negatives (missing real slow walking).

**User:** We looked at the plots. It's definitely typing. The Z-axis variance is low, but X/Y are active.

**Assistant:**
Great catch. Since typing is planar (horizontal surface), the vertical axis (usually aligned with gravity/Z when wrist is flat) should be relatively stable.

**Suggested Fix:**
Modify the algorithm to weight the **vertical axis (gravity)** more heavily or require a significant **magnitude vector** change ($$\sqrt{x^2+y^2+z^2}$$) that exceeds a "typing threshold". Most step counters use the magnitude to be orientation-invariant, but for wrist-worn devices, leveraging the orientation (if known) can help filter desk work.

---

## Example 4: Multi-Skill Workflow (End-to-End)

**Scenario:** A user wants to develop a new digital biomarker for "Fatigue" using voice analysis.

**User:** I want to build a voice-based biomarker for fatigue. Where do I start?

**Assistant:** [Triggers `research-strategy` -> `algo-development` -> `review-validation`]

This is a complex, end-to-end R&D project. We will move through three distinct phases.

**Phase 1: Concept & Research (Skill: `research-strategy`)**
*   **Goal:** Define "Fatigue" and link it to voice acoustics.
*   **Action:** Literature review on "vocal biomarkers fatigue".
*   **Key Concepts:**
    *   *Jitter/Shimmer:* Micro-fluctuations in pitch/loudness.
    *   *Speaking Rate:* Slows down with cognitive fatigue.
    *   *Pauses:* Increase in frequency and duration.
*   **Outcome:** A "Concept of Interest" document defining the physiological link between neuromuscular fatigue and vocal cord control.

**Phase 2: Algorithm Development (Skill: `algo-development`)**
*   **Goal:** Build a pipeline to extract these features.
*   **Data:** Do we have labeled data? (e.g., subjects performing tasks before/after sleep deprivation).
*   **Toolbox:** `OpenSMILE` or `Librosa` (Python).
*   **Pipeline:**
    1.  **VAD (Voice Activity Detection):** Remove silence.
    2.  **Feature Extraction:** MFCCs, prosodic features.
    3.  **Modeling:** Train a classifier (Random Forest or SVM) to distinguish "Alert" vs. "Fatigued".
*   **Outcome:** A prototype algorithm with initial cross-validation performance (e.g., AUC = 0.75).

**Phase 3: Validation (Skill: `review-validation`)**
*   **Goal:** Prove it works on new people.
*   **Protocol:**
    *   **Population:** N=50 healthy volunteers.
    *   **Intervention:** 24-hour sleep deprivation protocol.
    *   **Ground Truth:** Psychomotor Vigilance Task (PVT) scores (Gold Standard for fatigue).
*   **Analysis:** Correlate "Voice Fatigue Score" with "PVT Reaction Time".
*   **Success Criteria:** Correlation $r > 0.6$ or Classification Accuracy > 80%.

**User:** That makes sense. For Phase 1, are there standard voice tasks?

**Assistant:**
Yes. Don't just record free speech. Standard tasks reduce variability:
1.  **Sustained Phonation:** Say "aaaaah" for as long as possible (measures breath control/stability).
2.  **Diadochokinetic Rate:** Say "pa-ta-ka" rapidly (measures motor coordination).
3.  **Reading Passage:** "The Rainbow Passage" (standardizes phoneme distribution).

Start with **Sustained Phonation**—it's the easiest to process and highly sensitive to neuromuscular fatigue.

---

## Example 5: Advanced Usage (Regulatory Strategy)

**Scenario:** A team is preparing a pre-submission package for the FDA and needs to justify their endpoint selection.

**User:** We're writing the briefing book for our pre-sub meeting. We chose "Sleep Efficiency" as our primary endpoint for an insomnia treatment, measured by our device. How do we justify this?

**Assistant:** [Triggers `research-strategy` with regulatory focus]

To justify "Sleep Efficiency" (SE) as a primary endpoint, you must build an argument based on the **"Fit-for-Purpose" (FFP)** framework.

**1. Clinical Relevance (The "So What?")**
*   **Argument:** SE reflects both the *quantity* (Total Sleep Time) and *quality* (Time in Bed) of sleep.
*   **Evidence:** Cite literature linking low SE to daytime impairment, mood disturbance, and long-term health risks.
*   **Patient Voice:** "Patients report that lying awake in bed is their most distressing symptom." (Do you have interview data to support this?)

**2. Measurement Validity (The "How Well?")**
*   **Accuracy:** Show your device's agreement with Polysomnography (PSG) - the Gold Standard.
    *   *Metric:* Bland-Altman bias < 5%, Sensitivity/Specificity for Wake/Sleep > 90%.
*   **Reliability:** Test-retest reliability (does it give the same score if nothing changed?).

**3. Endpoint Definition (The "Specifics")**
*   **Formula:** $$SE = \frac{\text{Total Sleep Time}}{\text{Time in Bed}} \times 100$$
*   **Window:** Is it measured over one night? A weekly average? (Weekly average is usually more robust and clinically meaningful).

**4. Context of Use (The "Who and When")**
*   **Population:** Adults with primary insomnia.
*   **Setting:** Home use, unsupervised.

**Critical Gap Check:**
FDA often prefers **Sleep Onset Latency (SOL)** or **Wake After Sleep Onset (WASO)** as specific components, rather than the composite SE, because SE can be "gamed" (e.g., staying in bed longer).
*   **Strategy:** Propose SE as Primary, but include SOL and WASO as key Secondary endpoints.
*   **Question for FDA:** "Does the Agency agree that Sleep Efficiency, defined as [X], represents a meaningful aspect of health for this population, provided we demonstrate [Y] correlation with daily function?"

**User:** That's a good point about SOL/WASO. We'll add those. What about "Time in Bed"? How does the device know?

**Assistant:**
This is a classic "Context of Use" risk.
*   **Risk:** Device assumes "lights off" = "trying to sleep". If user reads in bed, SE drops artificially.
*   **Mitigation:**
    1.  **Event Marker:** User presses a button on the device/app when they try to sleep.
    2.  **Algorithm:** "Sleep Opportunity" detection algorithm (e.g., light sensor + lack of motion).
    3.  **Patient Diary:** Backup log of bedtimes.
*   **Recommendation:** For the pre-sub, explicitly state *how* "Time in Bed" is determined. If it's purely algorithmic, provide validation data specifically for "Bedtime Detection Accuracy," not just "Sleep/Wake Accuracy."
