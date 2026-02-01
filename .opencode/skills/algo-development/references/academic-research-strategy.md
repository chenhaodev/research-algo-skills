# Academic Research Strategy

This document details the methodology for conducting a systematic literature search to identify high-quality algorithms and predictive biomarkers. The goal is to filter the vast volume of academic publications down to a manageable set of "prime candidates" for implementation.

## 1. Database-Specific Search Strategies

Different databases serve different purposes. A comprehensive search should cover at least one clinical database and one engineering database.

### PubMed (Clinical Focus)
*   **Best for:** Validated clinical studies, disease-specific biomarkers, medical guidelines.
*   **Strategy:**
    *   Use **MeSH (Medical Subject Headings)** terms for precise indexing (e.g., `("Atrial Fibrillation"[Mesh])`).
    *   Use **Boolean Operators** (AND, OR, NOT) to combine concepts.
    *   **Filters:**
        *   *Article Type:* "Clinical Trial", "Randomized Controlled Trial", "Meta-Analysis".
        *   *Publication Date:* Last 5 years (unless searching for foundational physiology).
        *   *Species:* Humans.

### IEEE Xplore (Engineering Focus)
*   **Best for:** Signal processing techniques, novel sensor hardware, mathematical algorithm details.
*   **Strategy:**
    *   Use **Command Search** for complex nested logic.
    *   Filter by **"Index Terms"** to find papers categorized by specific technologies (e.g., "Electrocardiography", "Machine Learning").
    *   **Filters:**
        *   *Content Type:* "Journals" (generally higher rigor than conferences) or "Conferences" (for cutting-edge, less mature work).
        *   *Sort by:* "Most Cited" to find influential papers.

### Google Scholar (Broad Coverage)
*   **Best for:** Finding full text, grey literature, and cross-disciplinary work.
*   **Strategy:**
    *   Use **"Advanced Search"** to search for exact phrases.
    *   **Citation Tracking:** Use the "Cited by" link on key papers to find newer improvements.
    *   **Author Alerts:** Follow key researchers in the specific niche.
    *   *Note:* Google Scholar has no quality filters, so manual screening is essential.

## 2. Keyword Development

Construct search queries by combining keywords from three categories: **Methodology**, **Clinical Context**, and **Data Modality**.

### A. Machine Learning / Methodology
*   **Time-Series:** `Time-series analysis`, `Recurrent Neural Networks`, `LSTM`, `GRU`, `Dynamic Time Warping`.
*   **Spectral:** `Power Spectral Density`, `Wavelet transform`, `Coherence`, `Time-frequency analysis`.
*   **Probability:** `Bayesian network`, `Hidden Markov Model`, `Gaussian Process`, `Logistic Regression`.
*   **General:** `Deep learning`, `Machine learning`, `Artificial Intelligence`, `Feature extraction`.

### B. Clinical Context
*   **Disease/Condition:** `Atrial Fibrillation`, `Sleep Apnea`, `Sepsis`, `Hypertension`.
*   **Endpoint:** `Mortality`, `Readmission`, `Diagnosis`, `Prognosis`, `Risk stratification`.
*   **Guidelines:** `Clinical guidelines`, `Gold standard`, `Consensus statement`.

### C. Data Modality
*   **Signals:** `ECG`, `PPG`, `EEG`, `Accelerometry`, `Vital signs`.
*   **Sensors:** `Wearable`, `Patch`, `Smartwatch`, `Pulse oximeter`.

**Example Combined Query:**
> `("Deep learning" OR "LSTM") AND ("Atrial Fibrillation" detection) AND ("Single-lead ECG" OR "PPG")`

## 3. Quality Filters

Apply these filters to prioritize high-quality evidence.

| Filter Type | Threshold / Criteria | Rationale |
| :--- | :--- | :--- |
| **Citation Count** | > 100 citations (if > 3 years old) | Indicates community acceptance and reproducibility. |
| **Impact Factor** | Journal IF > 3.0 (approx.) | Higher peer-review standards (heuristic only). |
| **Study Design** | Prospective / RCT | Higher level of evidence than retrospective studies. |
| **Data Size** | N > 100 subjects | Avoids small-sample overfitting. |
| **Validation** | External Validation | Proves generalizability beyond the training set. |

## 4. Top-Tier Venues

Prioritize papers from these sources.

### Medical / Clinical
*   **General:** *JAMA*, *NEJM*, *The Lancet*.
*   **Digital Health:** *The Lancet Digital Health*, *Nature Medicine*, *npj Digital Medicine*.
*   **Specialized:** *Circulation* (Cardio), *Chest* (Resp), *Sleep* (Sleep Med).

### Machine Learning / AI
*   **Conferences:** *NeurIPS* (Neural Information Processing Systems), *ICML* (International Conference on Machine Learning), *CVPR* (Computer Vision), *ICLR*.
*   **Journals:** *Journal of Machine Learning Research (JMLR)*, *IEEE Transactions on Pattern Analysis and Machine Intelligence (TPAMI)*.

### Biomedical Engineering
*   **Journals:** *IEEE Transactions on Biomedical Engineering (TBME)*, *Nature Biomedical Engineering*, *IEEE Journal of Biomedical and Health Informatics (JBHI)*.
*   **Conferences:** *EMBC* (IEEE Engineering in Medicine and Biology Society).

## 5. Literature Management

Organize your findings systematically to avoid losing track of key papers.

*   **Reference Managers:** Use tools like **Mendeley**, **Zotero**, or **EndNote**.
    *   *Tip:* Use browser plugins to save papers directly from search results.
*   **Citation Tracking:** Link papers to see who cites whom (building a "citation graph").
*   **Version Control:** Store your literature review notes in a Git repository (e.g., as markdown files).

## 6. Summary Table Template

Use this template to summarize candidate papers during your review.

| Keyword | Author (Year) | Title | Key Method | Validation | Why Promising? | Rank (0-4) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `AFib` | Smith et al. (2023) | *Deep learning for AF detection* | 1D-CNN on raw ECG | External dataset (N=5000) | Open code, large dataset | 4 |
| `Sleep` | Jones et al. (2021) | *Sleep staging with PPG* | Feature Eng. + XGBoost | Cross-validation (N=50) | Simple features, interpretable | 3 |
| `Sepsis` | Lee et al. (2020) | *Early sepsis prediction* | LSTM | Retrospective MIMIC-III | High accuracy reported | 2 |

**Rank Key:**
*   **4:** Ideal (Prospective, Open Code, High Impact).
*   **3:** Strong (Retrospective but large N, Good Methods).
*   **2:** Acceptable (Needs validation).
*   **1:** Weak (Small N, unclear methods).
*   **0:** Reject.
