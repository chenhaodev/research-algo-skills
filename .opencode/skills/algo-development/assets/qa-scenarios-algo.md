# QA Scenarios: Algorithm Development Skill

This file contains test scenarios to verify the functionality of the `algo-development` skill.
These scenarios cover the process of researching, selecting, and evaluating algorithms for digital health.

## Test Scenarios

### Scenario 1: Literature Search Strategy

**User Query:**
> "How do I find the best machine learning papers for atrial fibrillation detection from PPG?"

**Expected Skill Behavior:**
- Should trigger: `algo-development`
- Should reference: `references/academic-research-strategy.md`

**Expected Response Elements:**
1.  **Search Strategy:** Guidance on using PubMed, IEEE Xplore, and Google Scholar.
2.  **Keywords:** Suggest specific search strings (e.g., `("atrial fibrillation" OR "AFib") AND ("PPG" OR "photoplethysmogram") AND ("deep learning" OR "machine learning")`).
3.  **Quality Filters:**
    *   Citation count (relative to publication year).
    *   Journal tier (e.g., IEEE TBME, Nature Digital Medicine).
    *   Sample size (>100 patients).
4.  **Snowballing:** Mention checking references of key papers.

**Critical Content to Include:**
- Distinction between clinical validation papers and technical feasibility papers.
- Importance of "open datasets" in search queries.

**References to Validate:**
- [ ] Links to `references/academic-research-strategy.md` work
- [ ] Links to `../shared/reference-databases.md` work
- [ ] Trigger keywords detected: "find", "papers", "search", "literature"

**Pass Criteria:**
✅ Response provides concrete search terms.
✅ Mentions specific databases.
✅ Includes quality filtering criteria.

---

### Scenario 2: Algorithm Evaluation Matrix

**User Query:**
> "I found 10 papers on fall detection algorithms. How do I compare them systematically?"

**Expected Skill Behavior:**
- Should trigger: `algo-development`
- Should reference: `references/evaluation-criteria.md`

**Expected Response Elements:**
1.  **Evaluation Criteria:**
    *   **Performance:** Sensitivity, Specificity, F1-score.
    *   **Data Quality:** Sample size, population diversity, real-world vs. lab data.
    *   **Reproducibility:** Code availability, open dataset usage.
    *   **Complexity:** Computational load (can it run on a wearable?).
2.  **Scoring Rubric:** Suggest a 0-4 point scale for each criterion.
3.  **Decision Matrix:** Recommend creating a table to visualize the comparison.

**Critical Content to Include:**
- Warning about "overfitting" in small datasets.
- Importance of "Leave-One-Subject-Out" (LOSO) cross-validation.

**References to Validate:**
- [ ] Links to `references/evaluation-criteria.md` work
- [ ] Links to `../shared/questionnaires/algorithm-selection-checklist.md` work
- [ ] Trigger keywords detected: "compare", "evaluate", "ranking"

**Pass Criteria:**
✅ Response proposes a structured evaluation method (matrix/rubric).
✅ Highlights key technical metrics (F1, computational cost).
✅ Mentions validation methodology (LOSO).

---

### Scenario 3: GitHub Code Search & Evaluation

**User Query:**
> "What should I look for when evaluating a GitHub repository for ECG QRS detection?"

**Expected Skill Behavior:**
- Should trigger: `algo-development`
- Should reference: `references/toolbox-research.md`

**Expected Response Elements:**
1.  **Search Strategy:** Use GitHub topics (e.g., `topic:ecg`, `topic:qrs-detection`).
2.  **Evaluation Criteria:**
    *   **Maintenance:** Last commit date, active issues/PRs.
    *   **Usage:** Stars, forks, "Used by" count.
    *   **Documentation:** Readme quality, installation guide, examples.
    *   **Code Quality:** Tests coverage, modularity, dependencies.
    *   **License:** Permissive (MIT/Apache) vs. restrictive (GPL).
3.  **Specific Checks:** Look for `requirements.txt`, `setup.py`, and Jupyter notebooks.

**Critical Content to Include:**
- "Works on my machine" check (ease of installation).
- License compatibility warning.

**References to Validate:**
- [ ] Links to `references/toolbox-research.md` work
- [ ] Trigger keywords detected: "GitHub", "repo", "code", "evaluate"

**Pass Criteria:**
✅ Response covers both code quality and community health metrics.
✅ Mentions licensing implications.
✅ Suggests checking for documentation/examples.

---

### Scenario 4: Evidence Checklist Application

**User Query:**
> "I'm designing a validation study for a sleep apnea detection algorithm. What must I include?"

**Expected Skill Behavior:**
- Should trigger: `algo-development`
- Should reference: `references/evidence-checklist.md`

**Expected Response Elements:**
1.  **EVIDENCE Checklist:** Refer to the 25-item checklist.
2.  **Key Sections:**
    *   **Study Population:** Inclusion/exclusion criteria.
    *   **Sensor Specs:** Sampling rate, placement.
    *   **Reference Standard:** PSG (Polysomnography) scoring rules (AASM).
    *   **Algorithm Details:** Pre-processing, feature extraction, model type.
    *   **Performance Reporting:** Confusion matrix, ROC curves.
3.  **Data Partitioning:** Explicit training/validation/test split.

**Critical Content to Include:**
- "Gold Standard" definition (PSG).
- Reporting of demographics (age, BMI, gender).

**References to Validate:**
- [ ] Links to `references/evidence-checklist.md` work
- [ ] Links to `../shared/clinical-validation-framework.md` work

**Pass Criteria:**
✅ Response references the EVIDENCE checklist or similar standard.
✅ Mentions specific requirements for sleep apnea (PSG, AASM).
✅ Emphasizes data partitioning.

---

### Scenario 5: Complete Workflow (Selection)

**User Query:**
> "Help me select an algorithm for detecting hyperglycemia from continuous glucose monitor data."

**Expected Skill Behavior:**
- Should trigger: `algo-development`
- Should reference: `references/example-biomarker-selection.md`

**Expected Response Elements:**
1.  **Research:** Search for "CGM hyperglycemia detection algorithms" (Academic + GitHub).
2.  **Filter:** Prioritize algorithms validated on open datasets (e.g., OhioT1DM).
3.  **Evaluate:** Compare based on:
    *   **Lag time:** How quickly is it detected?
    *   **False alarms:** Specificity is crucial for user trust.
    *   **Personalization:** Does it require individual calibration?
4.  **Select:** Choose top 2-3 candidates for internal benchmarking.

**Critical Content to Include:**
- Reference to the example file.
- Consideration of clinical utility (actionable alerts).

**References to Validate:**
- [ ] Links to `references/example-biomarker-selection.md` work
- [ ] Links to `references/academic-research-strategy.md` work
- [ ] Links to `references/toolbox-research.md` work

**Pass Criteria:**
✅ Response follows the full research -> filter -> evaluate -> select pipeline.
✅ Contextualizes criteria for CGM (lag time, false alarms).

---

### Scenario 6: Reproducibility Check

**User Query:**
> "I found a great paper claiming 99% accuracy, but there's no code. How do I verify it?"

**Expected Skill Behavior:**
- Should trigger: `algo-development`
- Should reference: `references/evaluation-criteria.md`

**Expected Response Elements:**
1.  **Skepticism:** High accuracy without code is a red flag (potential overfitting or data leakage).
2.  **Replication Steps:**
    *   Check if the dataset is public.
    *   Attempt to implement the method from the description (often difficult).
    *   Contact authors (low success rate but worth trying).
3.  **Alternative:** Look for other papers that cite it and attempt to reproduce it.
4.  **Decision:** If not reproducible, downgrade its score significantly in the evaluation matrix.

**Critical Content to Include:**
- "Reproducibility Crisis" awareness.
- Recommendation to prioritize lower-performing but open/reproducible methods.

**References to Validate:**
- [ ] Links to `references/evaluation-criteria.md` work
- [ ] Trigger keywords detected: "no code", "verify", "reproduce"

**Pass Criteria:**
✅ Response advises caution/skepticism.
✅ Suggests practical steps to attempt verification.
✅ Recommends prioritizing reproducibility over claimed accuracy.

---

### Scenario 7: Handling Imbalanced Data

**User Query:**
> "My fall detection dataset has 1000 hours of walking and only 5 minutes of falls. How do I handle this?"

**Expected Skill Behavior:**
- Should trigger: `algo-development`
- Should reference: `references/evaluation-criteria.md` (or general ML knowledge)

**Expected Response Elements:**
1.  **Problem Identification:** Severe class imbalance.
2.  **Techniques:**
    *   **Resampling:** Undersampling majority class, oversampling minority (SMOTE).
    *   **Metric Selection:** Do NOT use Accuracy. Use Precision-Recall AUC, F1-score, or Sensitivity/Specificity.
    *   **Loss Function:** Weighted loss functions to penalize missing falls more.
    *   **Data Augmentation:** Simulate falls or use GANs (advanced).

**Critical Content to Include:**
- Warning against using "Accuracy" as a metric.
- Mention of SMOTE or similar techniques.

**References to Validate:**
- [ ] Links to `references/evaluation-criteria.md` work
- [ ] Links to `../shared/statistical-methods.md` work

**Pass Criteria:**
✅ Response correctly identifies the imbalance problem.
✅ Suggests appropriate metrics (not accuracy).
✅ Proposes standard mitigation strategies (resampling, weighting).
