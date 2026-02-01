---
name: review-validation
description: Comprehensive guide for conducting literature reviews, systematic reviews (PRISMA), and clinical validation protocols for AI/ML models, with strict data leakage prevention standards.
triggers:
  - feasibility analysis
  - systematic review
  - validation protocol
  - literature review
  - citation graph
  - PRISMA
  - clinical validation
  - benchmarking
  - data leakage
version: 1.0.0
license: Apache-2.0
---

# Literature Review & Validation Skill

This skill provides a rigorous framework for assessing research feasibility, conducting systematic reviews according to PRISMA standards, and executing clinical validation protocols. It emphasizes the critical importance of preventing data leakage in medical AI datasets.

## Quick Reference

### Methodology Comparison

| Feature | Feasibility Analysis | Systematic Review | Validation Protocol |
| :--- | :--- | :--- | :--- |
| **Primary Goal** | Determine if a project is viable and novel. | Synthesize all available evidence on a topic. | Prove model performance against benchmarks. |
| **Input** | Seed papers, broad search terms. | Defined search query (PICOS), inclusion criteria. | Trained model, external test dataset. |
| **Output** | Go/No-Go decision, Landscape Table. | PRISMA Flow Diagram, Meta-analysis/Synthesis. | Statistical Report (Bland-Altman, Metrics). |
| **Key Standard** | Impact Factor > 4.0, Q1 Journals. | PRISMA 2020, GRADE, PROBAST. | FDA Guidelines, ANSI/AAMI standards. |
| **Timeframe** | Days to Weeks. | Months (3-6+). | Weeks to Months. |
| **Rigor Level** | High (Exploratory). | Very High (Exhaustive). | Critical (Regulatory). |
| **Team Size** | 1 Researcher. | 2+ Reviewers, 1 Adjudicator. | 1 ML Engineer, 1 Clinical Expert. |

### Common Tools & Metrics

| Category | Tools/Metrics | Description |
| :--- | :--- | :--- |
| **Discovery** | Connected Papers, Google Scholar, PubMed, IEEE Xplore. | Tools for finding and mapping relevant literature. |
| **Quality** | Impact Factor (IF), SCI Quartile (Q1/Q2), Citation Count. | Metrics to assess the prestige and reliability of a source. |
| **Validation** | Mean Absolute Error (MAE), Standard Deviation (STD), Bland-Altman. | Statistical methods for quantifying model performance. |
| **Statistics** | Paired T-test, Confidence Intervals (95% CI), ROC Curves. | Tests for statistical significance and reliability. |
| **Risk of Bias** | QUADAS-2, PROBAST, ROBINS-I. | Tools to assess bias in diagnostic and prognostic studies. |

---

## When to Use This Skill

### 1. Feasibility Analysis
Use this methodology when:
*   **Project Inception:** You are starting a new research project or product feature and need to validate the concept.
*   **SOTA Check:** You need to understand the "State of the Art" (SOTA) to ensure your approach is competitive.
*   **Algorithm Selection:** You are deciding between different algorithmic approaches (e.g., CNN vs Transformer vs Traditional ML).
*   **Dataset Scouting:** You need to identify available public datasets or determine if data collection is required.
*   **Trigger:** "Is this idea viable?", "What is the SOTA for X?", "Are there datasets for Y?"

### 2. Systematic Review
Use this methodology when:
*   **Publication:** You are preparing a review paper, meta-analysis, or white paper for publication.
*   **Evidence Synthesis:** You need an exhaustive, unbiased understanding of all evidence on a specific clinical question.
*   **Guideline Development:** You are establishing a clinical guideline or internal best practice.
*   **Performance Comparison:** You need to quantitatively compare performance across multiple studies (Meta-analysis).
*   **Trigger:** "Conduct a systematic review of...", "Summarize all evidence for...", "Compare performance of X vs Y across literature."

### 3. Validation Protocol
Use this methodology when:
*   **Model Testing:** A model has been trained and needs independent testing on a hold-out or external dataset.
*   **Regulatory Submission:** You are preparing for regulatory submission (FDA 510(k), CE Mark) and need formal validation.
*   **Benchmarking:** You need to benchmark your model against competitor devices or human expert performance.
*   **External Verification:** You are verifying performance on a specific standard dataset (e.g., Physionet, MIMIC).
*   **Trigger:** "Validate the model on...", "Run the validation protocol", "Generate the performance report."

---

## How to Use This Skill

1.  **Select Methodology:** Determine if you need a quick feasibility check, a deep systematic review, or a technical validation based on the triggers above.
2.  **Check for Data Leakage:** **CRITICAL STEP.** Before any analysis or model training, verify how data is split. Ensure subject independence.
3.  **Execute Protocol:** Follow the specific steps for the chosen methodology (detailed below).
4.  **Synthesize Findings:** Create the required artifacts (Landscape Table, PRISMA Diagram, or Validation Report).
5.  **Review & Refine:** Cross-reference with standard checklists (PRISMA, GRADE, FDA guidance).

---

## Feasibility Analysis

The Feasibility Analysis is a rapid yet rigorous assessment to determine if a research direction is worth pursuing. It relies on high-quality signals from the literature to avoid "garbage in, garbage out."

### 1. Citation Graph Approach
Instead of relying solely on keyword searches which can be overwhelmed by noise, use a graph-based approach to find relevant papers.

*   **Tool:** **Connected Papers** (or similar citation graph visualizers like ResearchRabbit, Inciteful).
*   **Process:**
    1.  **Identify Seed Papers:** Find 1-2 "Seed Papers" that are seminal works in the field. These are often highly cited papers from top journals.
    2.  **Generate Graph:** Input the seed paper into the tool to generate a graph.
    3.  **Analyze Clusters:** Look for clusters of nodes. These usually represent different methodological approaches (e.g., a cluster for "Wavelet Transform" and a cluster for "Deep Learning").
    4.  **Identify Hubs:** Look for "Hub" papers with high connectivity (large nodes). These are the most influential papers.
    5.  **Trace Lineage:** Use the graph to see "Prior Works" (Ancestors) and "Derivative Works" (Descendants) to understand the evolution of the idea.

### 2. Quality Filters
The volume of medical AI papers is massive, but the quality varies significantly. Apply strict filters to focus on high-signal research.

*   **Impact Factor (IF):** Prioritize journals with IF > 4.0.
    *   *High Tier:* Nature Medicine, Lancet Digital Health, JAMA Cardiology.
    *   *Mid Tier:* IEEE TBME, IEEE JBHI, Computers in Biology and Medicine.
*   **SCI Quartile:** Focus on Q1 (top 25%) journals in their category.
*   **Connectivity:** In citation graphs, look for nodes with high degree centrality. Isolated nodes often indicate niche or ignored research.
*   **Recency:**
    *   *AI Techniques:* Weight papers from the last 3-5 years higher.
    *   *Clinical Physiology:* Older seminal papers (10-20 years) often define the biological ground truth and remain valid.

### 3. Landscape Analysis Table
Construct a structured table to visualize the competitive landscape. This is the primary artifact of a feasibility analysis.

**Template:**

| Paper (Year) | Journal (IF) | Algorithm/Method | Dataset (Size/Type) | Performance (Metric) | Limitations | Relevance Score (1-5) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| *Author et al. (2023)* | *IEEE JBHI (7.4)* | ResNet-50 + LSTM | Private (n=5000 pts) | Acc: 92%, F1: 0.89 | No external validation. | 5 (High) |
| *Smith et al. (2021)* | *Comp. Bio. Med. (6.1)* | Hand-crafted features | Physionet (n=100 pts) | Acc: 85%, F1: 0.82 | Small sample size. | 3 (Med) |
| *Doe et al. (2024)* | *ArXiv (N/A)* | Transformer | Public + Private | Acc: 94%, F1: 0.91 | Pre-print, not peer-reviewed. | 2 (Low) |

### 4. Feasibility Scoring
Rate the feasibility of your proposed project based on the landscape:

*   **Data Availability (0-3):**
    *   0: No data available.
    *   1: Small public datasets, insufficient for deep learning.
    *   2: Large public datasets available but require cleaning.
    *   3: High-quality, large, pre-processed datasets available.
*   **Methodological Clarity (0-3):**
    *   0: No clear SOTA, methods are obscure.
    *   1: SOTA exists but is complex/proprietary.
    *   2: SOTA is published but code is not available.
    *   3: SOTA is published with open-source code.
*   **Clinical Impact (0-3):**
    *   0: No clear clinical use case.
    *   1: Minor improvement over existing methods.
    *   2: Significant improvement or workflow efficiency.
    *   3: Breakthrough capability or new biomarker.

**Decision Matrix:**
*   **Score 0-3:** No-Go.
*   **Score 4-6:** Proceed with Caution (High Risk).
*   **Score 7-9:** Go (High Potential).

---

## Systematic Review (PRISMA)

A Systematic Review is a formal research study that collects and analyzes all evidence on a topic. We follow the **PRISMA 2020** (Preferred Reporting Items for Systematic Reviews and Meta-Analyses) guidelines.

### The 6-Step Process

#### Step 1: Define Topic & Scope
*   Clearly define the research question.
*   Determine if a meta-analysis (statistical combination of results) is possible.
*   Register the protocol (e.g., on PROSPERO) if intended for publication.

#### Step 2: Set Up Team
*   **Reviewers:** At least 2 independent reviewers are required to reduce bias during screening and extraction.
*   **Adjudicator:** A third senior reviewer to resolve disagreements between the primary reviewers.
*   **Statistician:** (Optional) For complex meta-analyses.

#### Step 3: Formulate Questions (PICOS)
Use the PICOS framework to structure your eligibility criteria:

*   **P (Population):** Who are the patients? (e.g., Adults >18 with Paroxysmal Atrial Fibrillation).
*   **I (Intervention):** What is the method? (e.g., Deep Learning algorithms using 12-lead ECG).
*   **C (Comparator):** What is it compared to? (e.g., Standard of Care, Cardiologist interpretation, Holter monitor).
*   **O (Outcome):** What are the metrics? (e.g., Sensitivity, Specificity, Stroke prediction accuracy).
*   **S (Study Design):** What types of studies? (e.g., RCTs, Cohort studies, Case-control).

*Technique Adaptation:* For pure engineering reviews, use the **Top-Med-AI-Labs-Checklist** to assess technical reproducibility (Code, Data, Hyperparameters).

#### Step 4: Search Literature
*   **Sources:**
    *   *Clinical:* PubMed/MEDLINE, Embase, Cochrane Library.
    *   *Technical:* IEEE Xplore, Scopus, Web of Science, ACM Digital Library.
*   **Query Construction:**
    *   Use MeSH terms (Medical Subject Headings) in PubMed.
    *   Use Boolean operators (AND, OR, NOT).
    *   *Example:* `("Deep Learning"[MeSH] OR "Neural Networks") AND ("Electrocardiography"[MeSH] OR "ECG") AND ("Atrial Fibrillation"[MeSH])`
*   **Deduplication:** Use tools like EndNote, Covidence, or Rayyan to remove duplicate records found across multiple databases.

#### Step 5: Synthesize Evidence
*   **Screening:**
    *   *Phase 1:* Title/Abstract screening. (Is it relevant?)
    *   *Phase 2:* Full-text screening. (Does it meet all criteria?)
*   **Extraction:** Extract data into a standardized form.
    *   *Fields:* Author, Year, Country, Study Design, Population Size, Dataset Name, Algorithm Type, Input Modality, Performance Metrics (Sens, Spec, AUC), Validation Method (CV vs External), Risk of Bias.
*   **Quality Assessment:**
    *   **GRADE:** For clinical evidence certainty.
    *   **QUADAS-2:** For diagnostic accuracy studies.
    *   **PROBAST:** For prediction model risk of bias.

#### Step 6: Form Conclusion
*   Summarize findings quantitatively and qualitatively.
*   Identify gaps in current research (e.g., "Lack of external validation", "Data leakage prevalent").
*   Propose future directions.

### PRISMA 2020 Checklist (Detailed)
Ensure your review covers these 27 items:

1.  **Title:** Identify as a systematic review/meta-analysis.
2.  **Abstract:** Structured summary (Background, Methods, Results, Discussion).
3.  **Rationale:** Describe the current knowledge gap.
4.  **Objectives:** Explicit statement of questions (PICOS).
5.  **Eligibility Criteria:** Inclusion/Exclusion rules.
6.  **Information Sources:** Databases, registers, dates.
7.  **Search Strategy:** Full search string for at least one database.
8.  **Selection Process:** How were studies screened? (Independent reviewers?)
9.  **Data Collection:** Method of extraction (Forms? Automation?).
10. **Data Items:** List of all variables sought.
11. **Study Risk of Bias Assessment:** Tools used (QUADAS-2, etc.).
12. **Effect Measures:** Metrics used (OR, RR, AUC, Accuracy).
13. **Synthesis Methods:** How were studies combined? (Software, models).
14. **Reporting Bias Assessment:** Evaluation of publication bias.
15. **Certainty Assessment:** GRADE approach.
16. **Study Selection Results:** Flow diagram (Numbers screened, excluded, included).
17. **Study Characteristics:** Table of included studies.
18. **Risk of Bias Results:** Presentation of bias assessments.
19. **Results of Individual Studies:** Summary data for each study.
20. **Results of Syntheses:** Meta-analysis results (Forest plots).
21. **Reporting Biases Results:** Evidence of missing results.
22. **Certainty of Evidence Results:** GRADE summary of findings.
23. **Discussion:** Interpretation of results.
24. **Limitations:** Limitations of the evidence and the review process.
25. **Conclusions:** General interpretation.
26. **Registration:** Registry name and number (e.g., PROSPERO).
27. **Support:** Funding sources and conflicts of interest.

### AI Adaptations for Systematic Reviews
Traditional medical reviews use Odds Ratios (OR). AI reviews require different metrics:
*   **Forest Plots:** Adapt to show Accuracy, Sensitivity, Specificity, or AUC.
*   **ROC Curves:** Use Hierarchical Summary ROC (HSROC) models to combine performance across studies.
*   **Feature Importance:** Use linear regression meta-analysis to determine which features (e.g., "Use of LSTM", "Dataset Size > 10k") correlate with higher performance.

---

## Validation Protocol

Validation is the process of proving that a model works as intended on unseen data. This section focuses on the **Physionet QT Database** example, but the principles apply broadly to all medical AI validation.

### 1. Benchmarking Strategy
*   **Literature Benchmark:** Compare against SOTA papers.
    *   *QT Interval:* Charbit et al. (2006), Salvi et al. (2011), Hermans et al. (2017).
    *   *Arrhythmia:* Hannun et al. (2019), Ribeiro et al. (2020).
*   **Device Benchmark:** Compare against FDA-cleared devices.
    *   *Examples:* AliveCor Kardia, GE MUSE, Philips PageWriter, Welch Allyn.
*   **Gold Standard:** Human expert annotation.
    *   *Requirement:* Often requires consensus of 3 cardiologists for "Ground Truth".

### 2. Example Dataset: Physionet QT Database (QTDB)
*   **Description:** 105 records, 15 minutes each, 2-channel ECG.
*   **Source:** ITB, MIT-BIH, ESC, Sudden Death databases.
*   **Annotations:** Expert annotations of P-wave onset/offset, QRS onset/offset, and T-wave end.
*   **Relevance:** The standard benchmark for ECG delineation algorithms.

### 3. Key Metrics & Statistical Methods

#### A. Error Metrics
For regression/interval tasks (like QT measurement):
*   **Mean Absolute Error (MAE):** $\frac{1}{n}\sum |y_{pred} - y_{true}|$
    *   *Interpretation:* The average magnitude of the error.
*   **Standard Deviation (STD):** $\sqrt{\frac{\sum (x - \bar{x})^2}{n-1}}$
    *   *Interpretation:* The variability or precision of the error.
*   **Delta-QT Error:** Difference between Algorithm QT and Expert QT.

#### B. Bland-Altman Analysis
The gold standard for method comparison in medicine.
*   **Concept:** Plots the difference between two methods against their mean.
*   **X-axis:** Average of (Algorithm + Expert) / 2.
*   **Y-axis:** Difference (Algorithm - Expert).
*   **Bias:** The mean difference (distance from Y=0).
*   **Limits of Agreement (LoA):** Bias ± 1.96 * STD. 95% of differences should fall within this range.
*   **Proportional Bias:** Check if the difference changes as the value increases (e.g., larger errors at higher heart rates).

#### C. Hypothesis Testing
*   **Paired T-test:** Tests if the mean difference is significantly different from zero.
    *   *Null Hypothesis:* Mean difference = 0.
    *   *P-value < 0.05:* Significant bias exists.
*   **Confidence Intervals (CI):** Calculate 95% CI for all metrics using bootstrapping (resampling with replacement).

### 4. Execution Procedure
1.  **Data Extraction:**
    *   Download records using `wfdb` library.
    *   Extract specific leads (usually Lead II) and annotation files (`.atr`, `.qt1`, `.qt2`).
2.  **Preprocessing:**
    *   Apply standard filters (e.g., bandpass 0.5-40Hz) *only if* the model expects it.
    *   **Warning:** Do not over-filter; aggressive filtering can shift wave boundaries.
3.  **Measurement:**
    *   Run the algorithm on the extracted strips.
    *   Detect fiducial points: Q-onset, T-offset.
    *   Calculate QT interval (T_offset - Q_onset).
4.  **Alignment & Matching:**
    *   Align algorithm beats with ground truth beats.
    *   Use a tolerance window (e.g., 150ms) to match beats.
    *   Discard unmatched beats (but report the "Detection Rate").
5.  **Analysis:**
    *   Compute metrics (MAE, STD) for the matched pairs.
    *   Generate Bland-Altman plots.
    *   Calculate Heart Rate Corrected QT (QTc) using Bazett's ($QT / \sqrt{RR}$) or Fridericia's ($QT / \sqrt[3]{RR}$) formula.

---

## Data Leakage Prevention

**This is the single most critical quality control step in Medical AI.**
Data leakage occurs when information from the test set "leaks" into the training set, leading to overly optimistic performance estimates that fail in the real world.

### The Concept: Subject Independence
*   **Subject:** The biological entity (patient) generating the data.
*   **Record/Sample:** A specific instance of data (e.g., one minute of ECG, one MRI slice).
*   **Leakage:** When data from Subject A appears in both the Training Set and the Test Set.

### Types of Leakage
1.  **Patient Leakage:** Same patient in Train and Test. Model learns patient identity (biometrics) instead of pathology.
2.  **Temporal Leakage:** Future data predicts past data (in time-series).
3.  **Spatial Leakage:** Neighboring patches/slices in imaging.

### Case Study: Physionet Apnea Dataset
*   **Dataset Stats:** 70 records, but only 32 unique subjects.
*   **The Trap:** Some subjects have multiple records (e.g., Subject X has Record 1, Record 2, Record 3).
*   **Wrong Approach (Leakage):**
    *   Shuffle all 70 records.
    *   Split 80/20 randomly.
    *   *Result:* Subject X's Record 1 is in Train, Record 2 is in Test.
    *   *Inflated Performance:* ~95% Accuracy.
*   **Correct Approach (No Leakage):**
    *   Group records by Subject ID.
    *   Split Subjects 80/20 (e.g., 25 subjects Train, 7 subjects Test).
    *   *Result:* Model must generalize to completely new people.
    *   *Realistic Performance:* 79-87% Accuracy.

### Prevention Checklist
1.  [ ] **Identify Subject ID:** Find the unique Subject Identifier in the metadata. Do not assume Filename = Subject ID.
2.  [ ] **Map Samples to Subjects:** Create a mapping of `Sample_ID -> Subject_ID`.
3.  [ ] **Use GroupKFold:** Use `sklearn.model_selection.GroupKFold` or `StratifiedGroupKFold`.
4.  [ ] **Verify Split:** Explicitly check `intersect(train_subject_ids, test_subject_ids) == empty`.

### Code Example: Correct Splitting
```python
import numpy as np
from sklearn.model_selection import GroupKFold

# X = Data, y = Labels, groups = Patient IDs
X = np.array([...]) 
y = np.array([...])
groups = np.array([1, 1, 1, 2, 2, 3, 3, 3]) # Patient IDs

gkf = GroupKFold(n_splits=5)

for train_index, test_index in gkf.split(X, y, groups=groups):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]
    
    # VERIFICATION
    train_subjects = set(groups[train_index])
    test_subjects = set(groups[test_index])
    assert train_subjects.isdisjoint(test_subjects), "LEAKAGE DETECTED!"
    
    print(f"Train Subjects: {train_subjects}")
    print(f"Test Subjects: {test_subjects}")
```

---

## Examples

### Example 1: QT Interval Validation Workflow

**Objective:** Validate a new Deep Learning QT delineation model against the Physionet QT Database.

**Step 1: Preparation**
*   **Dataset:** Physionet QT Database (qtdb).
*   **Exclusion:** Exclude records with extreme noise or missing leads (document these exclusions).
*   **Standard:** ANSI/AAMI EC57:2012 (Testing and reporting performance results of cardiac rhythm and ST segment measurement algorithms).

**Step 2: Execution**
```python
# Pseudo-code for validation loop
results = []
for record in qtdb.records:
    # 1. Load Signal and Annotations
    signal, truth = load_record(record)
    
    # 2. Model Inference
    predictions = model.predict(signal)
    
    # 3. Match Beats
    # Use a tolerance window of 150ms as per standard
    matched_pairs = match_beats(truth.qrs, predictions.qrs, tolerance=0.15s)
    
    # 4. Calculate Errors
    for truth_beat, pred_beat in matched_pairs:
        qt_error = pred_beat.qt - truth_beat.qt # Signed error
        results.append(qt_error)

# 5. Compute Statistics
mean_error = np.mean(results)
std_error = np.std(results)
print(f"MAE: {mean_error} ms, STD: {std_error} ms")
```

**Step 3: Reporting**
*   **Table:**
    | Method | Mean Error (ms) | STD (ms) |
    | :--- | :--- | :--- |
    | **Our Model** | **4.2** | **8.5** |
    | Martinez et al. | 6.5 | 12.1 |
    | Laguna et al. | 8.0 | 14.3 |
    | *Acceptance Criteria* | *< 10.0* | *< 15.0* |
*   **Plot:** Bland-Altman plot showing error distribution across different heart rates.
*   **Conclusion:** "The model achieves state-of-the-art performance with a mean error of 4.2ms, significantly lower than the accepted tolerance of 10ms."

### Example 2: Systematic Review of AF Detection

**Objective:** Review performance of PPG-based Atrial Fibrillation detection.

**Step 1: Search Strategy**
*   Query: `("Photoplethysmography" OR "PPG" OR "Smartwatch") AND ("Atrial Fibrillation" OR "AF") AND ("Deep Learning" OR "AI")`
*   Databases: PubMed, IEEE Xplore.

**Step 2: Screening**
*   Total Hits: 450.
*   After Deduplication: 380.
*   Title Screen Exclusions: 300 (irrelevant).
*   Full Text Exclusions: 50 (no performance metrics, review papers).
*   Included: 30 studies.

**Step 3: Synthesis**
*   **Metric:** Sensitivity and Specificity.
*   **Meta-Analysis:** Pooled Sensitivity = 0.96 (95% CI: 0.94-0.98), Pooled Specificity = 0.95 (95% CI: 0.93-0.97).
*   **Bias:** High risk of bias in 20/30 studies due to patient selection (case-control design).
*   **Conclusion:** "High accuracy reported, but real-world prospective validation is lacking."

---

## Related Skills & References

### Internal References
*   `references/feasibility-analysis.md`: Detailed breakdown of feasibility scoring and landscape analysis templates.
*   `references/systematic-review.md`: Extended PRISMA guidelines and search strategy construction.
*   `references/validation-protocol.md`: Specifics on FDA validation requirements and statistical methods.
*   `references/data-leakage-prevention.md`: Advanced splitting techniques (e.g., Stratified Group K-Fold, Time-series splitting).

### Shared Resources
*   `shared/prisma-checklist.md`: Full 27-item PRISMA 2020 checklist.
*   `shared/grade-framework.md`: Guide to GRADE evidence quality assessment.
*   `shared/statistical-methods.md`: Code snippets for Bland-Altman, T-tests, and Bootstrap CI.
