# GRADE Evidence Assessment Framework

The **Grading of Recommendations Assessment, Development and Evaluation (GRADE)** approach provides a system for rating the quality (or certainty) of evidence and grading the strength of recommendations in systematic reviews and clinical practice guidelines.

## 1. Certainty of Evidence Levels

GRADE classifies the quality of evidence into four levels. This reflects the extent to which we can be confident that an estimate of effect is correct.

| Level | Symbol | Definition |
| :--- | :---: | :--- |
| **High** | ⊕⊕⊕⊕ | We are very confident that the true effect lies close to that of the estimate of the effect. |
| **Moderate** | ⊕⊕⊕◯ | We are moderately confident in the effect estimate: The true effect is likely to be close to the estimate of the effect, but there is a possibility that it is substantially different. |
| **Low** | ⊕⊕◯◯ | Our confidence in the effect estimate is limited: The true effect may be substantially different from the estimate of the effect. |
| **Very Low** | ⊕◯◯◯ | We have very little confidence in the effect estimate: The true effect is likely to be substantially different from the estimate of effect. |

### Initial Ratings
*   **Randomized Controlled Trials (RCTs)** start as **High** quality.
*   **Observational Studies** start as **Low** quality.

---

## 2. Domains for Downgrading Certainty

Five factors can lower the quality of evidence. If present, downgrade by -1 (serious concern) or -2 (very serious concern).

### 1. Risk of Bias
Limitations in the study design and execution.
*   **Key Issues:** Lack of allocation concealment, lack of blinding, incomplete accounting of patients and outcome events, selective outcome reporting.
*   **Tools:** Cochrane Risk of Bias Tool (RoB 2), ROBINS-I (for non-randomized studies).

### 2. Inconsistency
Unexplained heterogeneity or variability in results across studies.
*   **Indicators:** Widely differing point estimates, non-overlapping confidence intervals, high $I^2$ statistic (>50%), small p-value for heterogeneity test.

### 3. Indirectness
The evidence does not directly answer the research question.
*   **Types:**
    *   **Population:** Differences between study population and target population.
    *   **Intervention:** Differences in the intervention implemented.
    *   **Comparator:** Indirect comparisons (e.g., A vs B and B vs C to infer A vs C).
    *   **Outcome:** Surrogate outcomes instead of clinical endpoints.

### 4. Imprecision
Wide confidence intervals or small sample sizes.
*   **Criteria:** Confidence intervals cross the threshold for clinical decision-making (null effect or appreciable benefit/harm). Total number of events is low (Optimal Information Size not met).

### 5. Publication Bias
Systematic under-reporting of studies with negative or non-significant results.
*   **Indicators:** Asymmetrical funnel plots, small studies showing large effects, industry-sponsored studies with no negative findings.

---

## 3. Domains for Upgrading Certainty

Three factors can increase the quality of evidence (primarily for observational studies).

### 6. Large Effect
*   **Large:** Relative Risk (RR) > 2 or < 0.5 (+1 level).
*   **Very Large:** RR > 5 or < 0.2 (+2 levels).
*   *Note: Only applies if no plausible confounders would reduce the effect.*

### 7. Dose-Response Gradient
Evidence that increased exposure leads to increased effect.
*   **Example:** Higher drug dosage leads to greater symptom relief (+1 level).

### 8. Plausible Confounding
All plausible confounders or biases would reduce the demonstrated effect or suggest a spurious effect when results show no effect.
*   **Example:** If only sickest patients received the intervention but still did better, the actual effect might be even larger (+1 level).

---

## 4. GRADE Assessment Template

Use this template to summarize the evidence profile for each outcome.

### Outcome: [Insert Outcome Name]

**1. Study Design & Numbers**
*   **Number of studies:** [Count]
*   **Design:** [RCT / Observational]
*   **Total Participants:** [N]

**2. Risk of Bias Assessment**
*   **Rating:** [Not serious / Serious / Very serious]
*   **Justification:** [Brief explanation]

**3. Inconsistency**
*   **Rating:** [Not serious / Serious / Very serious]
*   **Justification:** [e.g., $I^2$ = 60%, visual heterogeneity]

**4. Indirectness**
*   **Rating:** [Not serious / Serious / Very serious]
*   **Justification:** [e.g., Surrogate outcome used]

**5. Imprecision**
*   **Rating:** [Not serious / Serious / Very serious]
*   **Justification:** [e.g., CI crosses 1.0, small sample size]

**6. Publication Bias**
*   **Rating:** [Undetected / Strongly suspected]
*   **Justification:** [e.g., Funnel plot asymmetry]

**7. Upgrading Factors**
*   **Large Effect:** [Yes/No]
*   **Dose-Response:** [Yes/No]
*   **Confounders:** [Yes/No]

**Final Certainty Rating:** [High / Moderate / Low / Very Low]

---

## Summary of Findings Table (Example)

| Outcome | Impact (Absolute Effect) | Certainty | Importance |
| :--- | :--- | :--- | :--- |
| **Mortality** | **Risk with Control:** 100 per 1000<br>**Risk with Intervention:** 80 per 1000 (CI 60-110) | ⊕⊕⊕◯<br>Moderate | Critical |
| **Adverse Events** | **Risk with Control:** 20 per 1000<br>**Risk with Intervention:** 25 per 1000 (CI 15-40) | ⊕⊕◯◯<br>Low | Important |

## When to Use GRADE
*   Systematic Reviews
*   Health Technology Assessments (HTA)
*   Clinical Practice Guidelines
*   Evaluating the strength of evidence for digital health interventions
