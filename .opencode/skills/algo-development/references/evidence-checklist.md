# Evidence Checklist (The 25-Item Standard)

This checklist is adapted from the *EVIDENCE Checklist for Digital Health Technologies*. It is used to validate the rigor of a completed study or to plan a new validation study.

**Usage:**
*   **Planning:** Ensure your protocol addresses every "Required" item.
*   **Reviewing:** Check if a third-party paper reports these items. Missing "Required" items is a red flag.

## Section 1: Study Definition

| ID | Item | Type | Description | Example |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Title** | Required | Identify the study design, population, and technology in the title. | "Validation of a Deep Learning Algorithm for AF Detection in Ambulatory Patients using Single-Lead ECG." |
| 2 | **Abstract** | Required | Structured summary: Background, Methods, Results, Conclusions. | (Standard structured abstract format) |
| 3 | **Rationale** | Required | Explain the scientific background and the specific gap this study fills. | "Current Holter monitors are bulky; a patch-based solution is needed." |

## Section 2: Methods

| ID | Item | Type | Description | Example |
| :--- | :--- | :--- | :--- | :--- |
| 4 | **Ethics** | Required | Confirm IRB/Ethics committee approval and informed consent. | "Approved by the XYZ Institutional Review Board (Protocol #123)." |
| 5 | **Protocol** | Preferred | Was the protocol published or registered? | "Registered on ClinicalTrials.gov (NCT00000000)." |
| 6 | **Participants** | Required | Eligibility criteria, setting, and location. | "Adults >18y with history of AF, recruited from XYZ Hospital Cardiology Clinic." |
| 7 | **Sample Size** | Required | How was the sample size determined? | "Power analysis indicated 200 subjects needed for 80% power to detect sensitivity > 90%." |
| 8 | **Sensor Specs** | Required | Precise identification of hardware. | "Apple Watch Series 6 (Model A2292)." |
| 9 | **Sensor Placement** | Required | Where on the body? How attached? | "Volar aspect of the left wrist, snug fit." |
| 10 | **Algorithm Version** | Required | Specific version number or commit hash. | "Algorithm v2.1.0 (Commit 8f3a2b)." |
| 11 | **Algorithm Desc.** | Required | Input data, processing steps, output definition. | "Inputs 30s PPG; outputs probability of AF (0-1)." |
| 12 | **User Interface** | Preferred | Description of what the user sees. | "The app displays a red notification if AF is detected." |
| 13 | **Outcomes** | Required | Primary and secondary endpoints clearly defined. | "Primary: Sensitivity/Specificity for AF vs. NSR." |
| 14 | **Data Collection** | Required | Procedures, minimum wear time, data management. | "Participants wore the device for 14 days. Data uploaded via Bluetooth." |
| 15 | **Reference Standard** | Required | What is the "Ground Truth"? | "Simultaneous 12-lead ECG interpreted by two cardiologists." |
| 16 | **Blinding** | Required | Were assessors blinded to the algorithm results? | "Cardiologists were blinded to the smartwatch algorithm output." |
| 17 | **Statistics** | Required | Methods used to compare algorithm vs. reference. | "Confusion matrix, ROC curve, Cohen's kappa." |

## Section 3: Results

| ID | Item | Type | Description | Example |
| :--- | :--- | :--- | :--- | :--- |
| 18 | **Flow Diagram** | Required | Participant flow (enrolled, allocated, analyzed). | (CONSORT flow diagram) |
| 19 | **Demographics** | Required | Baseline characteristics of the study population. | "Mean age 65 ± 10y, 40% Female, 30% Diabetic." |
| 20 | **Findings** | Required | Estimates of diagnostic accuracy with Confidence Intervals (95% CI). | "Sensitivity 95% (93-97%), Specificity 98% (97-99%)." |
| 21 | **Adverse Events** | Required | Any side effects or issues reported? | "Two participants reported skin irritation from the adhesive." |
| 22 | **Usability** | Preferred | User feedback or adherence data. | "Average wear time was 22 hours/day." |

## Section 4: Interpretation

| ID | Item | Type | Description | Example |
| :--- | :--- | :--- | :--- | :--- |
| 23 | **Summary** | Required | Key findings in context of the hypothesis. | "The algorithm accurately detects AF in an ambulatory setting." |
| 24 | **Comparison** | Required | How does this compare to existing literature? | "Performance is comparable to the Zio Patch (Smith et al., 2019)." |
| 25 | **Limitations** | Required | Honest assessment of bias, generalizability, and errors. | "Limited to a single center; population was predominantly male." |

## Section 5: Other

| ID | Item | Type | Description | Example |
| :--- | :--- | :--- | :--- | :--- |
| 26 | **Funding** | Required | Sources of funding. | "Funded by NIH Grant XYZ." |
| 27 | **Conflicts** | Required | Conflicts of interest. | "Author A is a consultant for the device manufacturer." |
