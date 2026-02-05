---
name: rpm-platform
description: End-to-end design guide for remote patient monitoring (RPM) platforms and telehealth systems
version: 1.0.0
author: OpenCode
license: Apache-2.0
tags:
  - remote monitoring
  - RPM
  - telehealth
  - biosensor
  - patient monitoring
  - alert management
  - clinician dashboard
  - data security
  - HIPAA compliance
---

# RPM Platform Design: Remote Patient Monitoring & Telehealth

## Quick Reference

### Platform Components Overview
| Component | Function | Key Considerations | Example Technologies |
|-----------|----------|--------------------|----------------------|
| **Biosensor Hardware** | Continuous data collection | Form factor, battery life, accuracy | VitalPatch, wearables, ECG patches |
| **Data Pipeline** | Transmission & storage | BLE → App → Cloud architecture, encryption | VitalCloud, AWS HealthLake |
| **Alert System** | Threshold monitoring & notifications | Sensitivity vs specificity, averaging durations | Configurable HR/RR limits, NEWS2 |
| **Clinician Dashboard** | Data visualization & triage | Progressive disclosure, traffic light colors | Baseball cards, trend lines |
| **Patient App** | Data sync & engagement | Adherence tracking, education | VistaPoint, mobile apps |

### Critical Path Summary
1.  **Define Clinical Objectives**: Determine what physiological parameters (HR, RR, SpO2) drive clinical decisions.
2.  **Select Hardware**: Choose biosensors that balance clinical accuracy with patient usability.
3.  **Design Data Flow**: Architect the path from sensor to cloud, ensuring connectivity and security.
4.  **Configure Alerts**: Set thresholds that detect deterioration without causing alarm fatigue.
5.  **Build Dashboard**: Create a UI that highlights at-risk patients immediately.
6.  **Validate System**: Test end-to-end latency, accuracy, and usability.

### Key Terminology
*   **RPM**: Remote Patient Monitoring - Continuous or intermittent monitoring of patients outside clinical settings.
*   **BLE**: Bluetooth Low Energy - Standard protocol for sensor-to-gateway communication.
*   **FHIR**: Fast Healthcare Interoperability Resources - Standard for exchanging healthcare data.
*   **Alarm Fatigue**: Desensitization of clinicians due to frequent false or non-actionable alarms.
*   **NEWS2**: National Early Warning Score 2 - Standardized scoring system for acute illness severity.
*   **MFA**: Multi-Factor Authentication - Security requirement for accessing PHI.

---

## When to Use This Skill

Activate this skill when the user asks to:
*   "Design an RPM system for heart failure patients."
*   "Architect a telehealth platform with continuous monitoring."
*   "Define alert thresholds for a remote monitoring dashboard."
*   "Select biosensors for a clinical trial."
*   "Create a clinician workflow for handling remote alerts."
*   "Ensure HIPAA compliance for a health data platform."
*   "Visualize patient vital signs trends effectively."

**Trigger Keywords**: `RPM system design`, `telehealth platform`, `continuous monitoring`, `remote care`, `alert management`, `clinician workflow`.

---

## How to Use This Skill

Follow this 7-step workflow to design a robust RPM platform:

1.  **Define Monitoring Objectives**:
    *   Identify the target patient population (e.g., post-discharge cardiac, chronic COPD).
    *   Determine the primary clinical endpoints (e.g., readmission reduction, early sepsis detection).
2.  **Select Biosensor**:
    *   Evaluate hardware based on clinical requirements.
    *   *Reference*: See `../device-selection/SKILL.md` for detailed selection criteria.
3.  **Design Data Architecture**:
    *   Map the flow: Sensor → Mobile Gateway (App) → Cloud Ingestion → Data Lake → API → Dashboard.
    *   Ensure offline buffering capabilities in the mobile gateway.
4.  **Configure Alert Thresholds**:
    *   Define upper/lower limits for vitals (HR, RR, SpO2).
    *   Implement averaging windows (e.g., 15s vs 5min) to minimize false positives.
    *   Ensure high sensitivity for critical events while managing specificity.
5.  **Build Clinician Interface**:
    *   Design the triage workflow. How does a nurse see the most critical patient first?
    *   Use "traffic light" indicators for rapid status assessment.
6.  **Integrate with EHR**:
    *   Plan for data export or bi-directional sync using HL7 FHIR.
    *   Avoid creating data silos; ensure RPM data reaches the primary medical record.
7.  **Validate End-to-End System and Pilot Test**:
    *   Conduct technical validation (latency, data loss).
    *   Run a clinical pilot to test workflow integration and adherence.

---

## Platform Architecture & Data Flow

A robust RPM architecture must handle continuous streams of time-series data while ensuring reliability and security.

### 1. The Edge (Patient Side)
*   **Biosensors**: Collect raw physiological data (ECG, acceleration, bio-impedance).
*   **Gateway (Mobile App/Hub)**:
    *   Connects to sensors via BLE.
    *   Performs initial data validation and buffering.
    *   Uploads data to the cloud via Wi-Fi or Cellular (LTE/5G).
    *   *Critical Feature*: Store-and-forward capability to handle network outages.

### 2. The Cloud (Infrastructure)
*   **Ingestion Layer**: MQTT or HTTP endpoints to receive high-frequency data packets.
*   **Processing Engine**: Stream processing (e.g., Apache Kafka, AWS Kinesis) for real-time analysis.
*   **Storage**:
    *   *Hot Storage*: Redis/DynamoDB for real-time dashboard state.
    *   *Cold Storage*: S3/Data Lake for historical analysis and audit trails.
*   **Algorithm Service**: Runs arrhythmia detection, fall detection, and risk scoring models.

### 3. The Interface (Clinician Side)
*   **API Layer**: REST/GraphQL APIs serving the frontend.
*   **Web Dashboard**: React/Angular application for monitoring patient status.
*   **Notification Service**: SMS, Email, or PagerDuty integration for critical alerts.

---

## Biosensor Selection & Integration

Selecting the right hardware is foundational. The sensor must be comfortable enough for the patient to wear and accurate enough for the clinician to trust.

*   **Form Factors**:
    *   *Adhesive Patches*: Good for continuous, multi-day monitoring (e.g., VitalPatch).
    *   *Wrist Wearables*: Better for long-term adherence, often less accurate for ECG.
    *   *Finger/Ear Clips*: High accuracy for SpO2, but restrictive for daily life.
*   **Integration Protocols**:
    *   Standard BLE profiles (Heart Rate Profile) vs. Proprietary Raw Data Services.
    *   Battery optimization is key; high-frequency sampling drains power.

> **Note**: For a comprehensive methodology on selecting the right device, refer to `../device-selection/SKILL.md`.

---

## Alert Threshold Design & Management

The success of an RPM program depends on the signal-to-noise ratio of its alerts. Too many false alarms lead to alarm fatigue and ignored critical events.

### Strategies for Reducing False Alarms
1.  **Averaging Windows**:
    *   Don't trigger on a single data point.
    *   *Example*: Require HR > 120 bpm for *at least* 30 seconds.
    *   *VitalConnect Approach*: Configurable durations from 15 seconds to 30 minutes.
2.  **Multi-Parameter Logic**:
    *   Combine signals to increase confidence.
    *   *Example*: Trigger "Sepsis Alert" only if (Temp > 38°C) AND (HR > 90) AND (RR > 20).
3.  **Personalized Thresholds**:
    *   Set limits based on the patient's baseline rather than population averages.
    *   *Example*: Alert if HR increases by 20% over baseline for 1 hour.
4.  **Smart Delays**:
    *   Allow self-correction for minor deviations before notifying staff.

### Clinical Indices Integration
Use validated scores to aggregate complexity.
*   **NEWS2**: Aggregates RR, SpO2, Air/Oxygen, Systolic BP, Pulse, Consciousness, and Temp into a single score (0-20).
*   *Reference*: See `../clinical-indices/SKILL.md` for details on implementing these scores.

---

## Clinician Dashboard & Workflow

The dashboard is not just a display; it is a workflow tool. It must support rapid triage.

### Design Principles
1.  **Traffic Light System**:
    *   **Red**: Critical/Immediate Action (e.g., V-Tach, SpO2 < 85%).
    *   **Yellow**: Warning/Watch (e.g., HR elevated, Battery low).
    *   **Green**: Stable/Normal.
2.  **Progressive Disclosure**:
    *   *Level 1 (Fleet View)*: List of all patients sorted by risk/severity.
    *   *Level 2 (Patient Card)*: Summary of current vitals and active alerts.
    *   *Level 3 (Detail View)*: High-resolution trend graphs and raw ECG strips.
3.  **Workflow Integration**:
    *   Ability to "Acknowledge" alerts.
    *   Ability to add "Clinical Notes" directly on the timeline.
    *   Audit trail of who viewed the alert and when.

---

## Data Security & Compliance

Handling PHI (Protected Health Information) requires strict adherence to regulations.

### Key Requirements
*   **HIPAA (USA) / GDPR (EU)**: Legal frameworks for data privacy.
*   **Encryption**:
    *   *In Transit*: TLS 1.2+ for all data transmission.
    *   *At Rest*: AES-256 encryption for database and file storage.
*   **Access Control**:
    *   **MFA**: Mandatory Multi-Factor Authentication for all clinical access.
    *   **RBAC**: Role-Based Access Control (e.g., Admin vs. Nurse vs. Doctor).
    *   **SSO**: Single Sign-On integration for enterprise management.
*   **Audit Logging**:
    *   Immutable logs of every access, view, and export of patient data.

---

## Visualization Best Practices

Effective visualization reduces cognitive load.

*   **Sparklines**: Small, word-sized charts in tables to show 24h trends.
*   **Contextual Bands**: Shaded areas on graphs indicating "Normal Range".
*   **Event Markers**: Vertical lines indicating medication administration or patient-reported symptoms.
*   **Closedloop Example**:
    *   *Baseball Cards*: High-level summaries embedded in EHR.
    *   *Factor Attribution*: Red/Green bars showing which factors are driving risk up or down.

---

## Case Studies & Examples

### 1. VitalConnect RPM (2021)
A comprehensive platform for hospital-at-home and cardiac monitoring.
*   **Hardware**: **VitalPatch** adhesive biosensor.
    *   *Sensors*: Single-lead ECG, Heart Rate, Respiration Rate, Posture, Activity (Steps), Skin Temp.
    *   *Form Factor*: Disposable, 7-day battery life.
*   **Data Flow**:
    *   VitalPatch → **VistaPoint App** (Mobile Gateway) via BLE.
    *   VistaPoint → **VitalCloud** via Wi-Fi/LTE.
    *   VitalCloud → **VistaCenter Dashboard** (Web Interface).
*   **Alert Logic**:
    *   *Configurable Thresholds*: Clinicians set upper/lower limits for HR and RR.
    *   *Averaging*: Durations configurable from 15 sec to 30 min to prevent false alarms.
    *   *Logic*: Can combine up to 3 vital signs with AND/OR logic.
    *   *Notifications*: Configurable notification hours (e.g., silence non-critical alerts at night).
*   **Arrhythmia Detection**:
    *   Cloud-based algorithms analyze continuous ECG.
    *   *Detects*: AFib, Tachycardia (>170 BPM), Pause (>15 sec), AV Block.
*   **NEWS2 Integration**:
    *   Calculates 7-parameter Early Warning Score (0-20) automatically.
    *   Visualizes score trends to detect clinical deterioration early.
*   **Security**:
    *   MFA, SSO, Role-based access control, full HIPAA compliance.

### 2. GE EK-Pro (2016)
Advanced arrhythmia detection algorithms used in clinical monitoring.
*   **Algorithm Core**: Continuous correlation and QRS template matching.
    *   *Multi-lead Analysis*: Processes 4 leads (I, II, III, V) simultaneously.
    *   *Fallback*: Automatically switches to Lead II if signal quality degrades.
*   **Contextual Analysis**:
    *   Evaluates R-R interval, beat width, and run length.
    *   *Pause Detection*: Triggers if R-R interval exceeds threshold (1-5s).
*   **Classifications**:
    *   **AFib**: Irregular R-R intervals with absent uniform P-waves.
    *   **V-Tach**: ≥6 Premature Ventricular Contractions (PVCs) with HR >100 bpm.
    *   **Asystole**: HR = 0 (Critical alarm).
    *   **Bigeminy/Trigeminy**: Pattern recognition for repeating PVC sequences.

### 3. Closedloop Visualization (2021)
Focuses on presenting AI-driven risk data to clinicians effectively.
*   **Baseball Card Summaries**:
    *   High-level risk preview embedded directly in the EHR workflow.
    *   Allows clinicians to see risk without leaving their primary workspace.
*   **Traffic Light Colors**:
    *   **Red**: High risk.
    *   **Yellow**: Elevated risk.
    *   **Green**: Normal.
    *   *Purpose*: Enables rapid scanning of patient lists.
*   **Progressive Disclosure**:
    *   *Level 1*: Preview card.
    *   *Level 2*: 10-15 page drill-down report for deep analysis.
*   **Factor Attribution**:
    *   Displays raw data values alongside directional indicators.
    *   *Visuals*: Red bars = risk increasing; Green bars = risk decreasing.
*   **Temporal Trends**:
    *   Risk trend lines show changes over time.
    *   Spikes in risk are visually linked to specific contributing factors (e.g., missed medication).

---

## Troubleshooting & Common Pitfalls

*   **Connectivity Issues**:
    *   *Problem*: Bluetooth dropouts between sensor and phone.
    *   *Solution*: Implement robust reconnection logic and on-sensor buffering.
*   **Data Gaps**:
    *   *Problem*: Missing data due to network outages.
    *   *Solution*: Store-and-forward architecture in the mobile gateway.
*   **User Adherence**:
    *   *Problem*: Patients forget to charge the phone or wear the device.
    *   *Solution*: Automated reminders (SMS/Push) and battery level monitoring on the dashboard.
*   **Scalability**:
    *   *Problem*: Dashboard becomes slow with thousands of patients.
    *   *Solution*: Use time-series optimized databases and paginate data efficiently.

---

## Shared Resources

### Internal References
*   `../device-selection/SKILL.md`: Detailed methodology for selecting biosensors.
*   `../clinical-indices/SKILL.md`: Guide to implementing clinical scores like NEWS2.
*   `../shared/visualization-best-practices.md`: (Planned) Comprehensive guide to medical data visualization.

### External Standards
*   **HL7 FHIR**: Standard for healthcare data interoperability.
*   **IEEE 11073**: Health informatics standard for personal health device communication.
*   **FDA SaMD**: Software as a Medical Device guidance.

---

## Disclaimer

**Professional Judgment Required**: This skill provides a technical and design framework for RPM platforms. It does not constitute medical, legal, or regulatory advice. Compliance with HIPAA, GDPR, FDA (e.g., SaMD), and other regulations is mandatory and requires consultation with qualified professionals. Clinical algorithms and alert thresholds must be validated by medical experts before deployment in patient care.
