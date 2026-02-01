# Algorithm Selection Checklist & Decision Matrix

This checklist provides a systematic way to evaluate and compare candidate algorithms for digital health measures. Use this tool to objectively score potential algorithms based on evidence, validation rigor, and feasibility.

**Date:** `[YYYY-MM-DD]`
**Project:** `[Project Name]`
**Algorithm Under Review:** `[Algorithm Name/Paper Title]`

---

## Part 1: Evaluation Criteria
*Score each category from 0 to 4 based on the rubric below.*

### 1. Evidence Quality (Weight: High)
*How strong is the scientific backing?*

**Citation Count (in last 3 years)**
- [ ] **0:** < 50 citations
- [ ] **1:** 50 - 100 citations
- [ ] **2:** 100 - 200 citations
- [ ] **3:** 200 - 500 citations
- [ ] **4:** > 500 citations

**Publication Venue**
- [ ] **0:** Unranked / Preprint only
- [ ] **1:** Q3-Q4 Journal / Workshop
- [ ] **2:** Q2 Journal / Standard Conference
- [ ] **3:** Q1 Journal / Top Conference
- [ ] **4:** Top-tier (JAMA, Nature, ICML, CVPR, NeurIPS)

**Level of Evidence**
- [ ] **0:** Case study / Anecdotal
- [ ] **1:** Retrospective analysis
- [ ] **2:** Prospective observational
- [ ] **3:** Randomized Controlled Trial (RCT)
- [ ] **4:** Meta-analysis / Systematic Review

### 2. Validation Rigor (Weight: Critical)
*How robust is the performance evaluation?*

**Overfitting Resistance**
- [ ] **0:** Training set only (No validation)
- [ ] **1:** Simple Train/Test split
- [ ] **2:** k-Fold Cross-Validation
- [ ] **3:** Hold-out by Subject (Leave-one-subject-out)
- [ ] **4:** External Validation (Independent dataset)

**Annotation / Ground Truth Quality**
- [ ] **0:** Single annotator / No clear standard
- [ ] **1:** Two annotators (no adjudication)
- [ ] **2:** Three+ annotators with adjudication
- [ ] **3:** Expert panel consensus
- [ ] **4:** Gold Standard Device (e.g., PSG, GaitRite, DEXA)

**Sample Size (N)**
- [ ] **0:** N < 100
- [ ] **1:** N = 100 - 500
- [ ] **2:** N = 500 - 1000
- [ ] **3:** N = 1000 - 5000
- [ ] **4:** N > 5000

### 3. Interpretability (Weight: Medium)
*Can we explain why it works?*

**Physiological Rationale**
- [ ] **0:** None / Black box
- [ ] **1:** Weak connection to physiology
- [ ] **2:** Moderate (plausible mechanism)
- [ ] **3:** Strong (aligned with known physiology)
- [ ] **4:** Mechanistic (directly models physiology)

**Mathematical Foundation**
- [ ] **0:** None
- [ ] **1:** Empirical only
- [ ] **2:** Heuristic proof
- [ ] **3:** Formal proof
- [ ] **4:** Theoretical guarantees

### 4. Reproducibility (Weight: High)
*Can we use it?*

**Code Availability**
- [ ] **0:** None
- [ ] **1:** Available on request
- [ ] **2:** Public GitHub / Archived
- [ ] **3:** Well-documented & organized
- [ ] **4:** Actively maintained package (pip/conda)

**Data Availability**
- [ ] **0:** None
- [ ] **1:** Available on request
- [ ] **2:** Public dataset used
- [ ] **3:** Multiple public datasets used
- [ ] **4:** Standard benchmark dataset

### 5. Implementation Feasibility (Weight: Medium)
*Can we deploy it?*

**Computational Cost**
- [ ] **0:** Requires HPC / Cluster
- [ ] **1:** High-end GPU required
- [ ] **2:** CPU intensive (Desktop)
- [ ] **3:** Moderate CPU (Mobile possible)
- [ ] **4:** Low resource (Edge/Embedded device)

**Ease of Integration**
- [ ] **0:** Custom / Obscure stack
- [ ] **1:** Rare dependencies
- [ ] **2:** Common libraries (numpy, scipy)
- [ ] **3:** Standard packages (scikit-learn, torch)
- [ ] **4:** Plug-and-play / No dependencies

---

## Part 2: Scoring & Decision Matrix

### Scoring Summary
Sum the scores from Part 1.
*   **Max Score:** 48 points
*   **Minimum Viable Score:** ~24 points (Average of 2 in all categories)

| Category | Score (Sum) | Max Possible |
| :--- | :--- | :--- |
| **Evidence Quality** | `___` | 12 |
| **Validation Rigor** | `___` | 12 |
| **Interpretability** | `___` | 8 |
| **Reproducibility** | `___` | 8 |
| **Implementation** | `___` | 8 |
| **TOTAL** | **`___`** | **48** |

### Recommendation Guide

*   **Score > 35 (Excellent):** Strong candidate. High likelihood of success. Prioritize for implementation.
*   **Score 25 - 35 (Good):** Viable candidate. May have some weaknesses (e.g., high computational cost or lower interpretability). Review trade-offs.
*   **Score 15 - 24 (Weak):** High risk. Only consider if no better alternatives exist. Requires significant internal validation and development.
*   **Score < 15 (Poor):** Do not use. Insufficient evidence or feasibility.

### Decision Matrix Template
Use this table to compare multiple algorithms side-by-side.

| Algorithm Name | Evidence (0-12) | Validation (0-12) | Interpret (0-8) | Reproduce (0-8) | Implement (0-8) | **Total** | **Rank** | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| *Example: Algo A* | *8* | *10* | *4* | *6* | *7* | *35* | *1* | *Solid choice* |
| **Candidate 1** | | | | | | | | |
| **Candidate 2** | | | | | | | | |
| **Candidate 3** | | | | | | | | |

### Trade-off Considerations
*   **Accuracy vs. Interpretability:** Deep learning models often score high on Validation but low on Interpretability. For clinical endpoints, Interpretability may be more critical.
*   **Performance vs. Cost:** A high-performing model (Score 4 on Validation) might be too computationally expensive (Score 0 on Implementation) for a wearable device.
*   **Reproducibility is Key:** Even a perfect algorithm is useless if you cannot reproduce the code or data (Score 0 on Reproducibility). **Disqualify any algorithm with Reproducibility score < 2.**
