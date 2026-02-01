# Case Study: Sleep Apnea Detection Algorithm Selection

**Project:** Selection of an AI Algorithm for Home Sleep Apnea Monitoring
**SOP Reference:** SOP-R-3 (Algorithm Selection)
**Duration:** 8 Weeks
**Status:** Implementation Complete

---

## 1. Project Overview

**Goal:** Enable sleep apnea detection (Apnea-Hypopnea Index estimation) using a single-lead ECG or PPG sensor suitable for home use.
**Constraint:** The algorithm must run on a mobile device or cloud backend with reasonable latency.
**Challenge:** Hundreds of papers claim "99% accuracy." We need to find one that actually works on *new* data.

---

## 2. Step 1: Academic Research (Weeks 1-2)

*Objective: Identify candidate methods from the literature.*

### 2.1 Search Strategy
We executed a structured search to filter high-quality work.

*   **Databases:** PubMed, IEEE Xplore.
*   **Query:**
    ```text
    ("sleep apnea"[MeSH] AND "electrocardiography"[MeSH] AND "machine learning"[Title/Abstract])
    OR ("sleep apnea detection" AND "ECG" AND "deep learning")
    ```
*   **Filters:** Year 2020-2024, Citations > 100 (for older papers) or Impact Factor > 4.0.

### 2.2 Results Screening
We identified 15 promising papers and extracted key data:

| Author (Year) | Algorithm | Dataset | Reported Accuracy | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Paper A (2023)** | ResNet-34 + Attention | Physionet Apnea-ECG | 98.5% | Used external validation set. |
| **Paper B (2022)** | LSTM | Private Hospital Data | 99.1% | Code not available. |
| **Paper C (2021)** | CNN-1D | Physionet Apnea-ECG | 96.0% | Lightweight, good for mobile. |

**Selection:** We chose **Paper A** and **Paper C** for detailed evaluation. Paper B was discarded due to lack of code/reproducibility.

---

## 3. Step 2: Toolbox Research (Weeks 2-3)

*Objective: Find existing code implementations.*

### 3.1 GitHub Search
*   **Query:** `sleep-apnea-detection ECG language:Python stars:>50`
*   **Results:** 8 repositories found.

### 3.2 Repository Evaluation
We applied our "Health Check" criteria:

1.  **Repo X (PyTorch):** Implements Paper A. Last commit 2 months ago. Has unit tests.
2.  **Repo Y (Keras):** Implements Paper C. Last commit 3 years ago. No `requirements.txt`.
3.  **Repo Z (Scikit-learn):** Feature engineering approach (HRV features). Very stable, but lower performance.

**Selection:** **Repo X** (for performance) and **Repo Z** (as a robust baseline).

---

## 4. Step 3: Evaluation & Scoring (Weeks 3-4)

*Objective: Objectively rank the candidates.*

We used the scoring rubric from `algo-development/references/evaluation-criteria.md`.

### 4.1 Scoring Matrix

| Criteria | Weight | Paper A / Repo X | Paper C / Repo Y | Baseline / Repo Z |
| :--- | :--- | :--- | :--- | :--- |
| **Overfitting Resistance** (External Val?) | 3 | **5** (Yes) | 2 (No) | 4 (Yes) |
| **Physiological Rationale** | 2 | **4** (Respiration derived) | 3 (Black box) | 5 (HRV features) |
| **Code Quality** | 2 | **5** (Modern PyTorch) | 1 (Broken) | 5 (Clean) |
| **Computational Cost** | 1 | 3 (Heavy GPU) | **5** (Light) | 5 (Light) |
| **Total Score** | -- | **4.2** | 2.5 | 4.1 |

### 4.2 Analysis
*   **Paper A / Repo X** is the winner for performance and reproducibility.
*   **Baseline / Repo Z** is a strong runner-up if we need to run on a microcontroller (very low compute).

---

## 5. Step 4: Selection Decision (Week 4)

**Decision:** Proceed with **Paper A (ResNet + Attention)** using **Repo X** as the base.

**Rationale:**
1.  **Performance:** F1=0.89 is significantly better than the baseline (F1=0.75).
2.  **Maintainability:** The codebase is active and uses modern standards.
3.  **Risk:** The computational cost is higher, but acceptable for a cloud-based deployment.

---

## 6. Step 5: Implementation (Weeks 5-8)

*Objective: Adapt the code to our environment and validate.*

### 6.1 Environment Setup
```bash
# Created isolated environment
conda create -n apnea-detect python=3.9
pip install torch==2.0.1 numpy pandas wfdb
```

### 6.2 Internal Testing
We tested the model on our internal dataset (N=100 patients, not seen by the model).

*   **Paper Reported F1:** 0.89
*   **Our Internal F1:** 0.85

**Analysis:** The slight drop is expected (domain shift). The model still outperforms our legacy algorithm (F1=0.70).

### 6.3 Integration
*   Wrapped the model in a FastAPI service.
*   Dockerized for deployment.
*   Added input validation (check for signal quality before prediction).

---

## 7. Lessons Learned

1.  **Papers vs. Toolboxes:** Academic papers provide the *theory*, but finding a good toolbox (Repo X) saved us ~3 months of implementation time.
2.  **The "SOTA" Trap:** Paper B claimed 99% accuracy but was useless without code. Always filter by reproducibility.
3.  **Domain Shift:** Expect a 5-10% performance drop when moving from public datasets (Physionet) to real-world clinical data.
4.  **Baselines Matter:** Having the simple feature-based baseline (Repo Z) gave us a sanity check. If the Deep Learning model didn't beat the simple one, we would have known something was wrong.

---

## 8. References Used

*   **Workflow:** `algo-development/SKILL.md`
*   **Search Syntax:** `algo-development/references/academic-research-strategy.md`
*   **Scoring Rubric:** `algo-development/references/evaluation-criteria.md`
*   **Similar Case:** `algo-development/references/example-biomarker-selection.md`
