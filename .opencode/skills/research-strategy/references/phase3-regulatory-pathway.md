# Phase 3: Regulatory Pathway

This document details the methodology for **Phase 3** of the Research Strategy framework. After defining the concept (Phase 1) and the measurement approach (Phase 2), the goal is to secure regulatory acceptance for the digital measure.

## 1. Classification: COA vs. Biomarker

Correctly classifying the measure is the first step in determining the regulatory requirements.

### 1.1 Clinical Outcome Assessment (COA)
A COA measures a patient's symptoms, overall mental state, or the effects of a disease or condition on how the patient functions.

*   **Key Characteristic**: Directly measures "how a patient feels, functions, or survives."
*   **Digital Sub-types**:
    *   **ePRO (Electronic Patient-Reported Outcome)**: Digital surveys/diaries.
    *   **PerfO (Performance Outcome)**: Standardized tasks (e.g., cognitive tests on a tablet, active gait test).
    *   **Passive COA**: Measures of free-living function (e.g., real-world walking speed, sleep quality) derived from sensors. *Note: This is the most common category for wearables.*

### 1.2 Biomarker
A defined characteristic that is measured as an indicator of normal biological processes, pathogenic processes, or responses to an exposure or intervention.

*   **Key Characteristic**: Physiological or biological measurement, not necessarily a direct measure of function.
*   **Digital Examples**:
    *   ECG-derived arrhythmia burden.
    *   Sweat sensor analytes.
    *   Voice biomarkers for vocal cord tension.

### 1.3 Decision Guide
*   *Does it measure what the patient DOES (behavior/function)?* -> **COA**.
*   *Does it measure the underlying BIOLOGY (physiology)?* -> **Biomarker**.

---

## 2. FDA Critical Path Innovation Meeting (CPIM)

The CPIM is a strategic tool for early regulatory engagement. It is non-binding but provides critical insight into the FDA's thinking.

### 2.1 Purpose
*   To discuss a methodology or technology proposed by the requester.
*   To obtain general advice on how to proceed with validation.
*   **NOT** for discussing specific drug approval applications (IND/NDA).

### 2.2 The Process
1.  **Preparation (Months 1-2)**: Compile the Briefing Packet.
2.  **Submission**: Send request to the CPIM program coordinator (CDER or CBER).
3.  **Scheduling**: FDA accepts and schedules meeting (typically ~60-90 days out).
4.  **The Meeting**: 90-minute presentation and discussion.
5.  **Follow-up**: FDA provides official meeting notes (non-binding).

### 2.3 Briefing Packet Structure (Detailed Template)
The briefing packet should be concise (15-20 pages) and clearly structured.

**Section 1: Introduction**
*   **Purpose**: "To discuss the development of a novel digital endpoint for [Disease]."
*   **Attendees**: List of sponsor participants and requested FDA disciplines (e.g., Division of Dermatology, COA Staff, Biostatistics).

**Section 2: Background & Unmet Need**
*   **Disease Overview**: Brief summary of the condition.
*   **Measurement Gap**: Why current endpoints fail (e.g., "Recall bias in monthly surveys").
*   **Patient Voice**: Summary of qualitative research (Phase 1) showing this concept matters.

**Section 3: The Proposed Measure**
*   **Concept of Interest**: The specific MAH.
*   **Context of Use**: Target population and setting.
*   **Technology**: Description of the sensor and algorithm (Phase 2).
    *   *Include*: Flowchart of data processing.

**Section 4: Validation Evidence**
*   **Completed Studies**: Summary of analytical and clinical validation data.
    *   *Table*: Correlation with Gold Standard.
    *   *Table*: Test-Retest Reliability.
*   **Planned Studies**: Protocol synopsis for the pivotal validation study.

**Section 5: Questions for FDA**
*   **Q1 (Concept)**: "Does the Agency agree that [Concept] represents a meaningful aspect of health for this population?"
*   **Q2 (Validation)**: "Is the proposed validation against [Gold Standard] sufficient to support the use of this measure as an exploratory endpoint?"
*   **Q3 (Endpoint)**: "Does the Agency agree with the proposed definition of the endpoint (e.g., weekly mean)?"

---

## 3. Endpoint Definition

Transforming a measure into a statistical endpoint requires precision.

### 3.1 Structure of an Endpoint
An endpoint must define **Variable**, **Timeframe**, and **Population**.

*   **Variable**: The specific metric.
    *   *Example*: "Moderate-to-vigorous physical activity (MVPA)."
*   **Analysis Method**: How is it calculated?
    *   *Example*: "Mean daily duration (minutes)."
*   **Timeframe**: When is it measured?
    *   *Example*: "Over a 7-day period prior to the Week 12 visit."
*   **Handling Missing Data**: What if the patient takes the device off?
    *   *Example*: "Days with <10 hours of wear time are excluded. A minimum of 4 valid days is required."

### 3.2 Estimands (ICH E9 R1)
Define the treatment effect precisely.
*   **Population**: Intent-to-Treat (ITT).
*   **Variable**: Change from baseline in [Measure].
*   **Intercurrent Events**: How to handle rescue medication or discontinuation? (e.g., Treatment Policy strategy).
*   **Population-level Summary**: Difference in means.

### 3.3 Hierarchy of Endpoints
*   **Primary Endpoint**: The main result used to judge efficacy. Requires the highest level of validation.
*   **Secondary Endpoint**: Supports the primary claim.
*   **Exploratory Endpoint**: Used for hypothesis generation. Lower validation barrier. *Start here for novel digital measures.*

---

## 4. Qualification Process (DDT)

The Drug Development Tool (DDT) qualification program allows a measure to be approved for use across multiple drug programs.

### 4.1 Stages of Qualification
1.  **Letter of Intent (LOI)**:
    *   Administrative information.
    *   Concept of Interest and Context of Use.
    *   High-level description of the tool.
2.  **Qualification Plan (QP)**:
    *   Detailed gap analysis.
    *   Proposed validation studies (analytical and clinical).
    *   Statistical analysis plan.
3.  **Full Qualification Package (FQP)**:
    *   Results of all validation studies.
    *   Evidence of clinical meaningfulness.
    *   User manual and standard operating procedures (SOPs).

### 4.2 Letter of Support (LOS)
A "lighter" alternative to full qualification.
*   **Purpose**: FDA encourages the exploration of a promising biomarker.
*   **Benefit**: Signals to the industry that the FDA is interested, facilitating data sharing and collaboration.

---

## 5. Regulatory Risk Assessment

Evaluate the risk profile of your strategy.

| Risk Category | Low Risk | Medium Risk | High Risk |
|---------------|----------|-------------|-----------|
| **Novelty** | Digital version of established test (e.g., digital trail making). | Novel metric for known concept (e.g., gait speed). | Completely new concept (e.g., social isolation index). |
| **Technology** | Medical-grade device (510k). | Consumer device with raw data. | Prototype / Custom hardware. |
| **Algorithm** | Simple arithmetic / Rule-based. | Linear regression / Random Forest. | Deep Learning / Neural Networks. |
| **Relationship to Outcome** | Direct measure of function. | Proximal biomarker. | Distal / Theoretical link. |

---

## 6. Key FDA Guidance Documents

Familiarity with these documents is essential.

*   **Patient-Focused Drug Development (PFDD) Guidance 1-4**: The "bible" for COA development.
    *   *Guidance 1*: Collecting Comprehensive and Representative Input.
    *   *Guidance 2*: Methods to Identify What is Important to Patients.
    *   *Guidance 3*: Selecting, Developing, or Modifying Fit-for-Purpose COAs.
    *   *Guidance 4*: Incorporating COAs into Endpoints for Regulatory Decision-Making.
*   **Digital Health Technologies for Remote Data Acquisition**: Draft guidance on using DHTs in clinical investigations.
*   **Biomarker Qualification Program**: Framework for biomarker development.

---

## Cross-References
*   **Inputs**: Requires outputs from `phase1-concept-relevance.md` and `phase2-measurement-approach.md`.
*   **Shared Resources**: See `../shared/fda-cds-criteria.md` for specific acceptance criteria.
