# QA Scenarios: Research Strategy Skill

This file contains test scenarios to verify the functionality of the `research-strategy` skill.
These scenarios cover the 3-phase framework for developing digital clinical measures.

## Test Scenarios

### Scenario 1: New Digital Measure Concept

**User Query:**
> "I want to develop a digital measure for tremor in Parkinson's disease. Where do I start?"

**Expected Skill Behavior:**
- Should trigger: `research-strategy`
- Should reference: `references/phase1-concept-relevance.md`

**Expected Response Elements:**
1.  **Phase 1 Guidance:** Emphasize starting with concept relevance, not technology.
2.  **Concept Mapping:** Explain the path from "tremor" (meaningful aspect of health) to "accelerometer signal" (concept of interest).
3.  **Stakeholder Identification:** Suggest interviewing patients, neurologists, and checking FDA guidance.
4.  **Literature Review:** Prompt to check existing measures to avoid reinventing the wheel.

**Critical Content to Include:**
- "Voice of the Patient" importance.
- Distinction between Meaningful Aspect of Health (MAH) and Concept of Interest (COI).

**References to Validate:**
- [ ] Links to `references/phase1-concept-relevance.md` work
- [ ] Links to `../shared/clinical-validation-framework.md` work
- [ ] Trigger keywords detected: "develop", "measure", "start"

**Pass Criteria:**
✅ Response focuses on Phase 1 (Concept) before moving to sensors.
✅ Mentions patient interviews or qualitative research.
✅ References the V3 framework (Verification, Analytical Validation, Clinical Validation) context.

---

### Scenario 2: Sensor Selection Decision

**User Query:**
> "What factors should I consider when selecting a wearable sensor for gait monitoring?"

**Expected Skill Behavior:**
- Should trigger: `research-strategy`
- Should reference: `references/phase2-measurement-approach.md`

**Expected Response Elements:**
1.  **Phase 2 Guidance:** Focus on selecting the right measurement approach.
2.  **Sensor Evaluation Checklist:**
    *   **Accuracy/Precision:** Sampling rate, dynamic range.
    *   **Form Factor:** Wearability, patient burden.
    *   **Battery Life:** Duration of monitoring required.
    *   **Data Access:** Raw data vs. processed metrics.
    *   **Cost:** Budget constraints.
3.  **Comparison of Options:** Briefly contrast IMUs (accelerometer/gyroscope), pressure insoles, and video-based systems.

**Critical Content to Include:**
- Importance of "Fit-for-Purpose" validation.
- Trade-off between clinical grade and consumer grade devices.

**References to Validate:**
- [ ] Links to `references/phase2-measurement-approach.md` work
- [ ] Links to `../shared/data-quality-checklist.md` work
- [ ] Trigger keywords detected: "selecting", "sensor", "wearable"

**Pass Criteria:**
✅ Response provides a structured checklist for evaluation.
✅ Mentions specific technical specs (e.g., sampling rate).
✅ References data access (raw data availability).

---

### Scenario 3: FDA Regulatory Pathway

**User Query:**
> "How do I prepare for an FDA CPIM meeting for a novel digital biomarker?"

**Expected Skill Behavior:**
- Should trigger: `research-strategy`
- Should reference: `references/phase3-regulatory-pathway.md`

**Expected Response Elements:**
1.  **Phase 3 Guidance:** Regulatory engagement strategies.
2.  **CPIM Overview:** Explain what a Critical Path Innovation Meeting is (non-binding scientific discussion).
3.  **Briefing Packet Outline:**
    *   Target population.
    *   Concept of Interest.
    *   Context of Use.
    *   Measurement approach.
    *   Validation plan.
4.  **Classification:** Discuss if it's a Clinical Outcome Assessment (COA) or a Biomarker.

**Critical Content to Include:**
- The importance of "Context of Use" (COU).
- Letter of Intent (LOI) submission process (brief mention).

**References to Validate:**
- [ ] Links to `references/phase3-regulatory-pathway.md` work
- [ ] Links to `../shared/fda-cds-criteria.md` work
- [ ] Trigger keywords detected: "FDA", "CPIM", "regulatory", "biomarker"

**Pass Criteria:**
✅ Response outlines the specific sections of a briefing packet.
✅ Correctly identifies CPIM as an early-stage engagement.
✅ Mentions Context of Use.

---

### Scenario 4: Complete Workflow (End-to-End)

**User Query:**
> "Walk me through developing a digital measure for nocturnal scratching in atopic dermatitis."

**Expected Skill Behavior:**
- Should trigger: `research-strategy`
- Should reference: `references/example-nocturnal-scratch.md`

**Expected Response Elements:**
1.  **Phase 1 (Concept):** Interview patients to confirm scratching impacts sleep quality. Define "scratching duration" as the concept.
2.  **Phase 2 (Measurement):** Select a wrist-worn accelerometer. Define algorithm to detect rhythmic hand movement.
3.  **Phase 3 (Regulatory/Validation):** Validate against video (gold standard). Plan for FDA qualification if intended for drug labeling.
4.  **Key Learnings:** Mention potential pitfalls like distinguishing scratching from other movements.

**Critical Content to Include:**
- A cohesive narrative connecting all 3 phases.
- Reference to the specific example file for deep dive.

**References to Validate:**
- [ ] Links to `references/example-nocturnal-scratch.md` work
- [ ] Links to `references/phase1-concept-relevance.md` work
- [ ] Links to `references/phase2-measurement-approach.md` work
- [ ] Links to `references/phase3-regulatory-pathway.md` work

**Pass Criteria:**
✅ Response covers the entire lifecycle.
✅ Uses the specific example of nocturnal scratch effectively.
✅ Logical flow from patient need to regulatory acceptance.

---

### Scenario 5: Clinical Outcome Assessment (COA) Type Selection

**User Query:**
> "Is my digital measure a PerfO, ClinRO, ObsRO, or PRO? It measures reaction time using a smartphone app."

**Expected Skill Behavior:**
- Should trigger: `research-strategy`
- Should reference: `references/phase3-regulatory-pathway.md`

**Expected Response Elements:**
1.  **Definitions:** Briefly define the 4 types of COAs.
    *   **PerfO (Performance Outcome):** Task performance by patient.
    *   **ClinRO (Clinician-reported):** Professional judgment.
    *   **ObsRO (Observer-reported):** Caregiver observation.
    *   **PRO (Patient-reported):** Patient's direct voice.
2.  **Classification:** Identify "reaction time task" as a **PerfO** (Performance Outcome).
3.  **Nuance:** If the patient *reports* they feel slow, that's a PRO. If they *perform* a task, it's a PerfO.

**Critical Content to Include:**
- Clear distinction between active tasks (PerfO) and passive monitoring (often DHT/Biomarker, but can be mapped to COA types).
- FDA definitions.

**References to Validate:**
- [ ] Links to `references/phase3-regulatory-pathway.md` work
- [ ] Trigger keywords detected: "PerfO", "ClinRO", "ObsRO", "PRO", "type"

**Pass Criteria:**
✅ Correctly classifies the example as PerfO.
✅ Provides clear definitions for all types.

---

### Scenario 6: Patient Engagement in Phase 1

**User Query:**
> "Why do I need to talk to patients before building my fall detection algorithm? I know falls are bad."

**Expected Skill Behavior:**
- Should trigger: `research-strategy`
- Should reference: `references/phase1-concept-relevance.md`

**Expected Response Elements:**
1.  **Justification:** Explain that "falls" is broad. Patients can define *what kind* of falls matter (e.g., injurious vs. stumbles) or the *impact* (fear of falling).
2.  **Usability:** Patients provide input on device wearability (will they wear a chest strap 24/7?).
3.  **Meaningfulness:** Establishing the "Meaningful Aspect of Health" is a regulatory requirement for clinical endpoints.
4.  **Risk Mitigation:** Avoids building a technically perfect solution that no one uses.

**Critical Content to Include:**
- "Meaningful Aspect of Health" (MAH).
- Patient burden considerations.

**References to Validate:**
- [ ] Links to `references/phase1-concept-relevance.md` work
- [ ] Links to `../shared/questionnaires/research-intake-questionnaire.md` work

**Pass Criteria:**
✅ Persuasively argues for patient involvement.
✅ Connects patient input to regulatory success (MAH).
