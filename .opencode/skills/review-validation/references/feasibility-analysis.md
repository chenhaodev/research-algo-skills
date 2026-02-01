# Feasibility Analysis Methodology

This document details the methodology for conducting a rigorous feasibility analysis for AI/ML research projects. The goal is to determine project viability, identify the State of the Art (SOTA), and assess data availability before significant resources are invested.

## 1. Citation Graph Methodology

Traditional keyword searches often miss relevant papers due to terminology differences or overwhelming volume. A citation graph approach traces the flow of ideas through the literature.

### 1.1. Tooling
*   **Primary Tool:** [Connected Papers](https://www.connectedpapers.com/)
*   **Alternatives:** ResearchRabbit, Inciteful, Litmaps.

### 1.2. Process
1.  **Identify Seed Papers:**
    *   Start with 1-2 seminal papers that define the problem or method you are interested in.
    *   *Example:* For "ECG Arrhythmia Detection", a seed might be *Hannun et al. (2019) "Cardiologist-level arrhythmia detection..."*
2.  **Generate Graph:**
    *   Input the seed paper into the tool.
    *   The tool generates a visual graph where nodes are papers and edges represent citation similarity (not just direct citations).
3.  **Interpret Visualization:**
    *   **Clusters:** Groupings of nodes usually represent specific sub-topics or methodologies (e.g., a cluster for "Wavelet Transform" vs. a cluster for "Deep Learning").
    *   **Prior Works (Ancestors):** Papers that most other papers in the graph cite. These are the foundational theories.
    *   **Derivative Works (Descendants):** Recent papers that cite the graph's core papers. These represent the current SOTA.
    *   **Similar Works:** Papers that share a high degree of citation overlap with the seed paper, even if they don't cite each other directly.
4.  **Apply Filters:**
    *   **Year:** Filter for the last 3-5 years to see recent advancements.
    *   **Citations:** High citation counts indicate influence, but be wary of "review" papers vs. "original research."
    *   **Connectivity:** Focus on nodes with multiple connections. Isolated nodes are often outliers or low-quality.

## 2. Quality Filters Implementation

The volume of published research is massive. Use these filters to separate high-signal research from noise.

### 2.1. Journal Ranking
*   **Impact Factor (IF):**
    *   **Threshold:** > 4.0 is a good baseline for reputable medical/engineering journals.
    *   **Sources:** Journal Citation Reports (JCR), Scimago Journal Rank.
    *   *High Tier:* Nature Medicine, Lancet Digital Health, IEEE TPAMI.
    *   *Mid Tier:* IEEE JBHI, Computers in Biology and Medicine, Scientific Reports.
*   **SCI Quartile (Q1/Q2):**
    *   Focus on **Q1** (Top 25%) journals in their specific category (e.g., "Biomedical Engineering" or "Computer Science, AI").
    *   Q2 is acceptable for niche topics. Avoid Q3/Q4 for SOTA benchmarking.

### 2.2. Connectivity Check
*   In the citation graph, a paper should have a **Connectivity Degree > 3** (connected to at least 3 other relevant papers).
*   Papers that sit outside the main clusters often lack reproducibility or community validation.

## 3. Landscape Analysis Table

The core output of this phase is a structured comparison of the top 5-10 relevant papers.

### 3.1. Table Structure

| Author (Year) | Journal (IF) | Input Signals | Algorithm/Model | Evaluation Method | Testing Dataset | Key Results |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| *Smith (2023)* | *IEEE JBHI (7.4)* | 12-lead ECG | ResNet-50 | 5-fold CV (Patient-split) | PTB-XL (Public) | AUC: 0.92 |
| *Jones (2022)* | *Nature Comms (16.6)* | Single-lead ECG | Transformer | External Validation | Private (n=10k) | F1: 0.88 |
| *Lee (2024)* | *ArXiv (N/A)* | PPG | CNN-LSTM | Random Split (Leakage?) | MIMIC-III | Acc: 99% |

### 3.2. Row Analysis
For each entry, analyze:
*   **Patterns:** Are most recent papers using Transformers? Is there a shift from 12-lead to single-lead?
*   **Gaps:** Is external validation consistently missing? Are datasets small (<100 patients)?
*   **Best Practices:** What preprocessing steps are standard (e.g., bandpass 0.5-40Hz)?

## 4. Validation Check (CRITICAL)

Before trusting a paper's results, perform a "Sanity Check" on their validation methodology. **Inflated results are often due to data leakage.**

### 4.1. Example: Apnea-ECG Dataset
*   **Dataset:** 70 records from 32 subjects.
*   **The Flaw:** Many papers treat the 70 records as independent samples.
*   **Leakage Scenario:**
    *   Subject A has Record 1 and Record 2.
    *   Record 1 goes to Training Set.
    *   Record 2 goes to Test Set.
    *   Model learns Subject A's specific heart rate variability, not sleep apnea patterns.
*   **Performance Impact:**
    *   *With Leakage:* Accuracy ~95-99%.
    *   *Proper Subject Split:* Accuracy ~79-87%.
*   **Action:** If a paper reports >95% on this dataset without explicit mention of "subject-independent splitting," **discard it** or mark it as "Low Reliability."

See `references/data-leakage-prevention.md` for detailed detection methods.

## 5. Feasibility Report Template

Combine findings into a concise report.

### Section 1: Landscape Summary
*   **SOTA Performance:** "Current top models achieve AUC 0.92 (Smith 2023)."
*   **Dominant Method:** "ResNet-based architectures are standard."
*   **Data Availability:** "PTB-XL is the primary public dataset."

### Section 2: Validation Assessment
*   **Reliability:** "3 out of 5 top papers use proper subject-level splitting. One paper (Lee 2024) likely has data leakage."
*   **Gaps:** "No study has validated on wearable (noisy) data."

### Section 3: Real-World Performance Estimate
*   *Estimate:* "Expect 5-10% drop from published academic results due to domain shift."
*   *Target:* "To be clinically useful, we need Sensitivity > 90%."

### Section 4: Recommendation
*   **Decision:** [GO / NO-GO / CAUTION]
*   **Rationale:** "GO. High-quality data is available, and current SOTA leaves room for improvement in noise robustness."

---
**Related References:**
*   `../shared/data-quality-checklist.md`
*   `references/data-leakage-prevention.md`
