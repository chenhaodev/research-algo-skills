# QA Scenarios: Review & Validation Skill

This file contains test scenarios to verify the functionality of the `review-validation` skill.
These scenarios cover the process of validating clinical evidence, designing protocols, and conducting systematic reviews.

## Test Scenarios

### Scenario 1: Feasibility Analysis

**User Query:**
> "How do I assess the feasibility of using ECG for respiratory rate estimation?"

**Expected Skill Behavior:**
- Should trigger: `review-validation`
- Should reference: `references/feasibility-analysis.md`

**Expected Response Elements:**
1.  **Citation Graph:** Suggest using tools like Connected Papers to find seminal works (e.g., Charlton et al.).
2.  **Quality Filters:**
    *   Impact Factor (IF) > 4.0.
    *   SCI Q1 journals.
    *   Recent reviews (last 3-5 years).
3.  **Landscape Analysis:** Create a table summarizing:
    *   Methods (EDR - ECG Derived Respiration).
    *   Performance (MAE, RMSE).
    *   Limitations (motion artifacts, arrhythmia).
4.  **Conclusion:** Determine if the technology is "Research Grade" or "Clinical Grade".

**Critical Content to Include:**
- Mention of "ECG Derived Respiration" (EDR) as the specific technique.
- Distinction between feasibility in controlled vs. free-living conditions.

**References to Validate:**
- [ ] Links to `references/feasibility-analysis.md` work
- [ ] Links to `../shared/reference-databases.md` work
- [ ] Trigger keywords detected: "feasibility", "assess", "viability"

**Pass Criteria:**
✅ Response suggests a structured literature review approach.
✅ Mentions specific quality metrics (IF, Q1).
✅ Identifies the core technical challenge (EDR).

---

### Scenario 2: Data Leakage Detection

**User Query:**
> "My model gets 98% accuracy on the test set, but fails in deployment. What went wrong?"

**Expected Skill Behavior:**
- Should trigger: `review-validation`
- Should reference: `references/data-leakage-prevention.md`

**Expected Response Elements:**
1.  **Diagnosis:** Strong suspicion of data leakage.
2.  **Common Causes:**
    *   **Subject Overlap:** Same patient in train and test sets (record-wise split vs. subject-wise split).
    *   **Temporal Leakage:** Future data predicting past events.
    *   **Feature Leakage:** Including a feature that is a proxy for the label (e.g., treatment duration).
3.  **Fixes:**
    *   Implement strict **Subject-wise Split**.
    *   Check feature importance (if one feature dominates, investigate it).
    *   Validate on an external, unseen dataset.

**Critical Content to Include:**
- "Subject-wise split" vs "Record-wise split".
- "Too good to be true" heuristic.

**References to Validate:**
- [ ] Links to `references/data-leakage-prevention.md` work
- [ ] Links to `../shared/data-quality-checklist.md` work
- [ ] Trigger keywords detected: "fails", "deployment", "accuracy", "wrong"

**Pass Criteria:**
✅ Response identifies "Subject Overlap" as the primary suspect.
✅ Explains the difference between splitting by record and by patient.
✅ Suggests external validation.

---

### Scenario 3: Systematic Review Process

**User Query:**
> "I need to conduct a systematic review of AI for diabetic retinopathy screening. What's the process?"

**Expected Skill Behavior:**
- Should trigger: `review-validation`
- Should reference: `references/systematic-review.md`

**Expected Response Elements:**
1.  **PRISMA Framework:** Reference the Preferred Reporting Items for Systematic Reviews and Meta-Analyses.
2.  **6-Step Process:**
    *   **Protocol:** Define PICOS (Population, Intervention, Comparator, Outcome, Study design).
    *   **Search:** Databases (PubMed, Embase), search strings.
    *   **Screening:** Title/Abstract -> Full Text.
    *   **Extraction:** Data extraction forms.
    *   **Quality Assessment:** QUADAS-2 or ROBINS-I tools.
    *   **Synthesis:** Meta-analysis or narrative synthesis.
3.  **Registration:** Suggest registering on PROSPERO.

**Critical Content to Include:**
- PICOS acronym definition.
- PRISMA checklist reference.

**References to Validate:**
- [ ] Links to `references/systematic-review.md` work
- [ ] Links to `../shared/prisma-checklist.md` work
- [ ] Links to `../shared/picos-templates.md` work

**Pass Criteria:**
✅ Response outlines the standard PRISMA flow.
✅ Mentions PICOS.
✅ Suggests quality assessment tools (QUADAS-2).

---

### Scenario 4: Validation Protocol Design

**User Query:**
> "How do I validate my blood pressure algorithm against gold standard measurements?"

**Expected Skill Behavior:**
- Should trigger: `review-validation`
- Should reference: `references/validation-protocol.md`

**Expected Response Elements:**
1.  **Reference Standard:** Manual auscultation (double observer) or invasive arterial line (ICU).
2.  **Standards:** Reference ISO 81060-2 (universal standard for non-invasive sphygmomanometers).
3.  **Metrics:**
    *   Mean Absolute Error (MAE).
    *   Standard Deviation of Error (STD).
    *   Bland-Altman Plot (Bias + Limits of Agreement).
    *   Correlation (Pearson/Spearman) - *secondary*.
4.  **Procedure:** Simultaneous or sequential measurements, range of BP values (hypo to hyper).

**Critical Content to Include:**
- ISO 81060-2 mention.
- Bland-Altman analysis importance.

**References to Validate:**
- [ ] Links to `references/validation-protocol.md` work
- [ ] Links to `../shared/statistical-methods.md` work

**Pass Criteria:**
✅ Response references the specific ISO standard.
✅ Identifies Bland-Altman as the key visualization.
✅ Specifies the reference standard (auscultation/catheter).

---

### Scenario 5: Complete Workflow (Validation)

**User Query:**
> "Validate my AI-ECG-QTc algorithm using the Physionet QT Database."

**Expected Skill Behavior:**
- Should trigger: `review-validation`
- Should reference: `references/example-qt-validation.md`

**Expected Response Elements:**
1.  **Dataset:** Confirm Physionet QT Database (QTDB) details (105 records).
2.  **Protocol:**
    *   Run algorithm on all records.
    *   Compare detected QT start/end points to expert annotations.
3.  **Analysis:**
    *   Calculate mean error and SD for Q-onset and T-offset.
    *   Compare against literature benchmarks (e.g., Martinez et al., Laguna et al.).
4.  **Reporting:** Create a table comparing your results to the "Gold Standard" algorithms.

**Critical Content to Include:**
- Reference to the specific example file.
- Specific metrics for ECG segmentation (ms error).

**References to Validate:**
- [ ] Links to `references/example-qt-validation.md` work
- [ ] Links to `references/validation-protocol.md` work

**Pass Criteria:**
✅ Response provides a specific validation plan for QTDB.
✅ Mentions comparison to literature benchmarks.

---

### Scenario 6: Statistical Analysis Plan (SAP)

**User Query:**
> "What statistical tests should I use to show my new device is equivalent to the old one?"

**Expected Skill Behavior:**
- Should trigger: `review-validation`
- Should reference: `../shared/statistical-methods.md`

**Expected Response Elements:**
1.  **Equivalence vs. Superiority:** Clarify the goal (Equivalence or Non-inferiority).
2.  **Bland-Altman:** The primary tool for method comparison. Check if 95% limits of agreement fall within clinically acceptable ranges.
3.  **Correlation is Insufficient:** Explain why high correlation ($r > 0.9$) doesn't prove agreement (could have bias).
4.  **Paired t-test:** To check for systematic bias (mean difference).
5.  **ICC:** Intraclass Correlation Coefficient for reliability.

**Critical Content to Include:**
- "Correlation does not imply agreement."
- Definition of "Clinically Acceptable Difference".

**References to Validate:**
- [ ] Links to `../shared/statistical-methods.md` work
- [ ] Links to `references/validation-protocol.md` work

**Pass Criteria:**
✅ Response warns against relying solely on correlation.
✅ Recommends Bland-Altman.
✅ Mentions ICC.

---

### Scenario 7: Benchmarking against State-of-the-Art (SOTA)

**User Query:**
> "Is my sleep staging algorithm good enough? It has 80% accuracy."

**Expected Skill Behavior:**
- Should trigger: `review-validation`
- Should reference: `references/feasibility-analysis.md` (or general benchmarking)

**Expected Response Elements:**
1.  **Contextualize:** 80% on what? (4-class vs 5-class staging? Healthy vs. Apnea patients?).
2.  **Literature Benchmark:** Compare to SOTA (e.g., deep learning models often achieve 83-87% on public datasets like Sleep-EDF).
3.  **Inter-rater Reliability:** Compare to human expert agreement (often ~83%). If you match human agreement, you are "good enough".
4.  **Cohen's Kappa:** Suggest reporting Kappa alongside accuracy to account for class imbalance (N2 sleep dominance).

**Critical Content to Include:**
- Comparison to "Human Level Performance".
- Cohen's Kappa.

**References to Validate:**
- [ ] Links to `references/feasibility-analysis.md` work
- [ ] Links to `../shared/grade-framework.md` work

**Pass Criteria:**
✅ Response asks for context (classes, dataset).
✅ Compares performance to human inter-rater reliability.
✅ Suggests Kappa metric.
