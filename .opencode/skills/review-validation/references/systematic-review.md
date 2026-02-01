# Systematic Review Methodology (PRISMA 2020)

This document outlines the standard operating procedure for conducting a Systematic Review and Meta-Analysis following the **PRISMA 2020** (Preferred Reporting Items for Systematic Reviews and Meta-Analyses) guidelines.

## 1. The 6-Step Process

### Step 1: Define Topic & Scope
*   **Objective:** Clearly state the clinical or technical question.
*   **Frameworks:**
    *   *Clinical:* **PICOS** (Population, Intervention, Comparator, Outcome, Study Design).
    *   *Technical:* **Top-Med-AI-Labs Checklist** (Code availability, Data privacy, Reproducibility).
*   **Registration:** Register protocol on PROSPERO (for clinical) or OSF (Open Science Framework) to prevent duplication.

### Step 2: Set Up Review Team
*   **Primary Reviewers (2+):** Two independent researchers to screen titles/abstracts and full texts. This reduces selection bias.
*   **Adjudicator (1):** A senior researcher to resolve disagreements (e.g., Reviewer A includes, Reviewer B excludes).
*   **Librarian (Optional):** To assist with complex search string construction.

### Step 3: Formulate Questions (PICOS)
Structure your inclusion/exclusion criteria:

| Component | Description | Example |
| :--- | :--- | :--- |
| **Population** | Target subjects | Adults >18 with Heart Failure |
| **Intervention** | The AI model/method | Deep Learning on Chest X-Ray |
| **Comparator** | Baseline for comparison | Radiologist interpretation |
| **Outcome** | Metrics of interest | Sensitivity, Specificity, AUC |
| **Study Design** | Allowed types | RCTs, Cohort Studies (Exclude Case Reports) |

### Step 4: Literature Search
*   **Strategy:** Comprehensive search across multiple databases.
*   **Databases:** PubMed, Embase, Cochrane (Clinical); IEEE Xplore, Scopus, ACM (Technical).
*   **Search String Construction:**
    *   **MeSH Terms:** Use Medical Subject Headings for precision (e.g., `"Artificial Intelligence"[MeSH]`).
    *   **Keywords:** Use free-text synonyms (e.g., "Deep Learning", "Neural Network").
    *   **Boolean Logic:**
        *   `AND`: Narrows results (Intersection).
        *   `OR`: Broadens results (Union).
        *   `NOT`: Excludes terms (Use with caution).
    *   *Example:* `(Population OR Synonyms) AND (Intervention OR Synonyms) AND (Outcome OR Synonyms)`

### Step 5: Synthesize Evidence
*   **Data Extraction:** Use a standardized form (Excel/Covidence) to extract:
    *   Study Metadata (Author, Year, Country).
    *   Dataset Details (Size, Public/Private, Split Method).
    *   Model Details (Architecture, Inputs).
    *   Performance Metrics (TP, FP, TN, FN, AUC).
*   **Quality Assessment:**
    *   **GRADE:** For overall certainty of evidence.
    *   **QUADAS-2:** For diagnostic accuracy studies.
    *   **PROBAST:** Specifically for prediction model bias.

### Step 6: Form Conclusion
*   **Summary:** Synthesize findings (e.g., "AI performs equivalent to clinicians").
*   **Certainty:** Rate confidence (High, Moderate, Low, Very Low).
*   **Recommendations:** Actionable advice for clinical practice or future research.

## 2. PRISMA 2020 Checklist

Ensure compliance with all 27 items. Refer to `../shared/prisma-checklist.md` for the full text.

**Key Compliance Tips:**
*   **Item 5 (Eligibility):** Be specific. "Machine Learning" is too broad; specify "Supervised Learning for Classification."
*   **Item 7 (Search Strategy):** You MUST publish the exact search string for at least one database so it is reproducible.
*   **Item 16 (Flow Diagram):** Track the exact number of papers at each stage (Identification -> Screening -> Eligibility -> Included).

## 3. AI-Specific Adaptations

Traditional meta-analysis methods (like Odds Ratios) often don't fit AI performance metrics.

### 3.1. Hierarchical Summary ROC (HSROC)
*   **Problem:** Simple averaging of Sensitivity/Specificity ignores the threshold effect (trade-off between Sens/Spec).
*   **Solution:** HSROC models estimate the underlying ROC curve across multiple studies.
*   **Interpretation:** The area under the HSROC curve gives the pooled diagnostic accuracy.

### 3.2. Forest Plots for AI
*   **Adaptation:** Instead of "Effect Size," plot **AUC** or **F1-Score**.
*   **Heterogeneity ($I^2$):**
    *   High $I^2$ (>75%) is common in AI due to dataset differences.
    *   **Action:** Perform subgroup analysis (e.g., "Deep Learning vs. Traditional ML" or "Public vs. Private Data").

### 3.3. Feature Importance Meta-Analysis
*   Use meta-regression to identify factors driving performance.
*   *Example:* Does "Dataset Size > 10k" significantly increase AUC?
*   *Method:* Linear regression where $Y=AUC$ and $X=Feature$.

## 4. Flow Diagram Construction

Use the standard PRISMA flow:

1.  **Identification:** Records identified from databases (n=X).
2.  **Screening:**
    *   Records screened (n=X).
    *   Records excluded (n=Y).
3.  **Eligibility:**
    *   Full-text articles assessed (n=Z).
    *   Full-text articles excluded (n=W) [Give reasons: e.g., "No validation set"].
4.  **Included:** Studies included in synthesis (n=V).

---
**Related References:**
*   `../shared/prisma-checklist.md`
*   `../shared/grade-framework.md`
