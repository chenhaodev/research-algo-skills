# Case Study: Sleep Apnea Detection

This document demonstrates the full **Algo-Development** workflow applied to a real-world scenario: selecting an algorithm for detecting Sleep Apnea using wearable sensors.

## 1. Scenario Definition

*   **Goal:** Develop a software module to detect Obstructive Sleep Apnea (OSA) events.
*   **Input:** Single-lead ECG (from a chest patch) or PPG (from a wristband).
*   **Constraint:** Must run on a mobile device (low computational complexity preferred) or cloud.
*   **Target Performance:** Sensitivity > 85%, Specificity > 85% compared to Polysomnography (PSG).

## 2. Phase 1: Academic Research

### Search Strategy
*   **Database:** PubMed & IEEE Xplore.
*   **Query:**
    > `("Sleep Apnea" OR "OSA") AND ("Deep Learning" OR "Machine Learning") AND ("ECG" OR "PPG" OR "Heart Rate Variability")`
*   **Filters:**
    *   Publication Date: 2020 - 2024.
    *   Citations: > 50 (for papers > 2 years old).
    *   Article Type: Journal Article / Conference Proceeding.

### Key Findings (Top 5 Papers)

| ID | Author (Year) | Modality | Method | Validation | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **P1** | Chang et al. (2020) | ECG | 1D-CNN | PhysioNet Apnea-ECG (Retrospective) | High citations, standard benchmark. |
| **P2** | Zhai et al. (2021) | PPG | Feature Eng. + SVM | Internal Clinical Dataset (N=200) | Good physiological explanation. |
| **P3** | Urtnasan et al. (2022) | ECG | CNN + LSTM | Multi-center (Retrospective) | Complex architecture. |
| **P4** | Papini et al. (2020) | PPG | Deep Learning | MESA Dataset (Large Public) | Reproducible, open code. |
| **P5** | Smith et al. (2023) | ECG | Transformer | Small internal set (N=30) | Too new, small sample. |

## 3. Phase 2: Toolbox Research

### Search Strategy
*   **Source:** GitHub.
*   **Keywords:** `sleep-apnea-detection`, `ecg-sleep`, `ppg-sleep`.
*   **Filters:** Stars > 50, Language = Python.

### Key Findings (Top 3 Libraries)

| ID | Library | Stars | Last Commit | License | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T1** | `sleep-ecg` | 250 | 1 month ago | MIT | Focused on ECG sleep staging/apnea. Well tested. |
| **T2** | `py-ppg-sleep` | 80 | 2 years ago | GPL | Good algorithms but restrictive license. |
| **T3** | `apnea-detect` | 400 | 6 months ago | Apache 2.0 | Implementation of Paper P1. |

## 4. Phase 3: Evaluation & Scoring

We score the top candidates using the [Evaluation Criteria](./evaluation-criteria.md).

### Scoring Papers

| Candidate | Overfitting (0/1) | Physiology (0/1) | Math (0/1) | Code (0/1) | **Total** | Decision |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **P1 (Chang)** | 0 (Retro) | 0 (Blackbox) | 1 (Standard) | 1 (Open) | **2** | Backup. |
| **P2 (Zhai)** | 1 (Prospective) | 1 (Features) | 1 (SVM) | 0 (No code) | **3** | Strong, but need to re-code. |
| **P4 (Papini)** | 1 (Large Public) | 1 (Physio) | 1 (DL) | 1 (Open) | **4** | **Winner.** |

### Scoring Toolboxes

| Candidate | Maint. | Usage | Comm. | Rep. | **Rank** | Decision |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **T1 (`sleep-ecg`)** | High | Med | High | High | **4** | **Adopt.** |
| **T3 (`apnea-detect`)** | Med | High | Med | Med | **3** | Good reference. |

## 5. Selection Decision

**Selected Approach:**
*   **Algorithm:** Based on **Paper P4 (Papini et al.)** for PPG-based detection, or **Paper P1 (Chang)** implemented via **Toolbox T1 (`sleep-ecg`)** for ECG-based detection.
*   **Rationale:**
    *   If hardware supports ECG: Use `sleep-ecg` (T1). It is a production-ready library implementing a standard, well-cited method (P1).
    *   If hardware is PPG-only: Implement P4. It has the highest scientific score (4/4) and uses a large public dataset (MESA) for validation.

## 6. Implementation Plan

1.  **Environment Setup:**
    *   `pip install sleep-ecg tensorflow pandas`
    *   Download PhysioNet Apnea-ECG database for benchmarking.
2.  **Baseline Reproduction:**
    *   Run `sleep-ecg` on PhysioNet data.
    *   Verify accuracy matches reported values (~90%).
3.  **Adaptation:**
    *   Retrain the model using our specific sensor sampling rate (e.g., downsample 250Hz -> 100Hz).
4.  **Validation:**
    *   Collect internal dataset (N=20) with simultaneous PSG.
    *   Run **Evidence Checklist** (Phase 4) to ensure study rigor.
