# HeartLogic CHF Index: Multi-Sensor Composite Algorithm

> **Parent Skill**: [Clinical Indices](../SKILL.md)  
> **Related**: [NOL Pain Index](./nol-pain-index.md), [Multi-Sensor Fusion](../../shared/multi-sensor-fusion-methodology.md)

## Overview

**HeartLogic** is a composite index for detecting **heart failure (HF) decompensation** before clinical symptoms appear, embedded in implantable cardiac devices (ICDs, CRT-Ds). It combines data from **5 physiological sensors** into a single numerical index and generates alerts when the index crosses a configurable threshold.

**Key Innovation**: Rather than relying on single-parameter monitoring (e.g., impedance alone), HeartLogic fuses multiple independent signals to overcome individual sensor limitations and reduce false alerts.

---

## Sensor Inputs

### 1. Heart Sounds (Mechanical)

**S3 (Third Heart Sound)**:
- **Physiology**: Ventricular filling sound, associated with elevated filling pressures and volume overload
- **Direction**: **Increases** with worsening HF (fluid accumulation)
- **Measurement**: Accelerometer in device detects low-frequency vibrations during diastole
- **Threshold**: Baseline S3 >1mG associated with significantly greater risk of HF events over 1-year follow-up

**S1 (First Heart Sound)**:
- **Physiology**: Mitral/tricuspid valve closure, reflects ventricular contractility
- **Direction**: **Decreases** with worsening HF (diminished contractile function)
- **Measurement**: Accelerometer detects high-frequency sound at systole

### 2. Thoracic Impedance (Electrical)

**Measurement**:
- Low-amplitude, high-frequency current passed between device electrodes
- Impedance measured across thorax

**Physiology**:
- **Decreases** indicate fluid accumulation (pulmonary edema, thoracic congestion)
- Fluid is a better conductor than air-filled lung tissue → lower impedance

**Direction**: **Decreasing** trend = worsening HF

### 3. Respiration (Mechanical)

**Respiratory Rate**:
- Derived from thoracic impedance fluctuations (breathing modulates impedance)
- **Increases** indicate tachypnea, respiratory distress

**Rapid Shallow Breathing**:
- Pattern analysis: High rate + low tidal volume
- Marker of pulmonary congestion, dyspnea

**Direction**: **Increasing** respiratory rate = worsening HF

### 4. Heart Rate (Electrical)

**Night Heart Rate** (Resting HR during sleep):
- Autonomic imbalance marker
- **Increases** suggest sympathetic activation or arrhythmias

**Direction**: **Increasing** night HR = worsening HF

### 5. Activity (Mechanical)

**Daily Activity Level**:
- Measured via accelerometer (steps, movement intensity)
- **Decreases** reflect reduced functional status, fatigue

**Direction**: **Decreasing** activity = worsening HF

### 6. Sleep Incline (Contextual)

**Measurement**:
- Accelerometer detects body position angle during sleep
- **Increases** in sleep angle (more upright) suggest **orthopnea** or **paroxysmal nocturnal dyspnea (PND)**

**Direction**: **Increasing** incline = worsening HF (patient sleeping more upright to breathe easier)

---

## Algorithm Logic

### Baseline & Trend Analysis

**Personalized Baselines**:
- Each patient's normal values are established during stable periods
- Algorithm compares current sensor values to patient's own historical baseline (not population norms)

**Directional Changes**:
- Algorithm detects **trends** (increasing S3, decreasing impedance, increasing RR, etc.)
- **Degree of worsening** for each sensor quantified

### Multi-Sensor Fusion

**Composite Score**:
- Combines directional changes from all 5 sensor inputs
- Weight each sensor's contribution to the composite
- **Index accumulates over time** as sensors show persistent worsening trends

**Alert Threshold**:
- User-programmable threshold (configurable by clinician)
- **Yellow Alert** triggered when composite index crosses threshold
- Alert remains active until index falls below threshold

### Explainability: Contributing Trends

**Heart Failure Management Report (HFMR)**:
- Visual display showing which sensors are driving the alert
- **Contributing Trends**: Shaded bars indicate "degree of worsening" for each input
- **Example**: High S3 + Low Impedance + High Respiratory Rate → Alert triggered

**Clinical Value**: Allows clinician to understand **why** the alert fired (e.g., "Is it fluid (Impedance) or rhythm (AF)?")

---

## Validation: MultiSENSE Study

**Study Design**:
- **Patients**: >900 with implanted devices (ICD/CRT-D)
- **Methodology**: Prospective, multi-site
- **Endpoint**: Worsening HF events requiring intervention (hospitalization, unplanned IV therapy)

### Key Results

| Metric | Value | Interpretation |
|--------|-------|----------------|
| **Sensitivity** | 70% | Detects 70% of HF decompensation events |
| **Advance Warning** | Median **34 days** | Alert fires 34 days (median) before clinical event |
| **Early Warning (≥2 weeks)** | 89% | 89% of events had alert ≥2 weeks before hospitalization |
| **Alert Burden** | <2 alerts/patient/year | Low false positive rate |
| **Risk Stratification** | **10x higher** event rate in alert state | 0.80 events/patient/year (alert) vs. 0.08 (non-alert) |

**Clinical Impact**:
- **34-day advance warning** provides clinicians time for **intervention** (adjust diuretics, intensify monitoring) before acute decompensation
- **10x risk stratification** enables prioritizing high-risk patients for outreach

### Sensor Validation (Literature-Cited)

**References** (Boehmer et al., Gardner et al.):
- Each sensor demonstrated statistically significant changes **prior** to HF events in MultiSENSE data
- Multi-sensor combination outperformed single-sensor alerts

---

## Clinical Workflow: 3A Process

HeartLogic integrates into HF management via the **3A Process**:

### 1. Alert
- Clinician receives **Yellow Alert** notification via remote monitoring system (LATITUDE NXT, CareLink, etc.)
- Alert indicates composite index crossed threshold

### 2. Assessment

**Remote Review**:
- Access **Heart Failure Management Report (HFMR)**
- Identify **Contributing Trends**:
  - **Fluid-driven**: Low impedance, high S3 → Likely volume overload
  - **Rhythm-driven**: High AF burden, elevated night HR → Arrhythmia trigger
  - **Activity-driven**: Decreased activity → Functional decline

**Patient Contact**:
- Call patient to screen for:
  - **Precipitating factors**: Medication non-adherence, dietary indiscretion (high salt intake), recent illness
  - **Symptoms**: Shortness of breath, weight gain, edema, orthopnea

### 3. Action

**Interventions**:
- **Adjust Diuretics**: Increase dose if fluid overload suspected
- **Medication Adherence**: Reinforce diet/fluid restrictions
- **Treat Arrhythmias**: Rate control for AF, optimize beta-blocker
- **Device Optimization**: Adjust CRT settings if suboptimal pacing
- **Schedule Follow-Up**: In-person visit if symptoms present

**Escalation**: If patient symptomatic or high-risk features → urgent clinic visit or hospitalization

---

## Practical Implementation

### Device Integration

**Compatible Devices**:
- **Resonate™ family** (Boston Scientific ICD and CRT-D systems)
- HeartLogic enabled via software (not all implanted devices have this feature)

**Data Transmission**:
- Continuous monitoring in background
- Data transmitted to remote monitoring platform (e.g., LATITUDE NXT) nightly
- Alerts delivered to clinician portal/email

### Threshold Configuration

**Default**: Set by manufacturer based on MultiSENSE study  
**Customization**: Clinician can adjust threshold based on:
- Patient risk tolerance (higher threshold = fewer alerts, potentially lower sensitivity)
- Alert burden vs. detection trade-off
- Pilot testing: Observe alert frequency in first 30 days, adjust if needed

**Recommendation**: Start with default, adjust only if excessive false alerts or missed events during pilot period.

---

## Limitations & Considerations

### Not a Diagnostic Tool
- HeartLogic provides **early warning** of physiological changes
- **Clinical judgment required**: Alert does not diagnose HF, nor prescribe treatment
- **Differential**: Other conditions (pneumonia, AF, dehydration) can trigger alerts

### Sensor Dependency
- Requires **implantable device** (ICD/CRT-D)
- Not applicable to HF patients without device indication
- **Patient Population**: Typically HF with reduced ejection fraction (HFrEF) and device indication for primary/secondary prevention

### Alert Fatigue
- Even with low burden (<2/patient/year), clinician workflow must accommodate remote triage
- **Infrastructure Requirement**: Dedicated HF nurse or remote monitoring team

---

## Composite Index Development Best Practices

**Lessons from HeartLogic**:

1. **Explainability**: Provide breakdown of contributing factors (not just a single number)
2. **Personalized Baselines**: Use patient's own history, not population norms
3. **Holistic Monitoring**: Combine mechanical (heart sounds, activity) and electrical (HR, impedance) signals
4. **Clinical Validation**: Demonstrate advance warning timeline and risk stratification (not just sensitivity/specificity)
5. **Workflow Integration**: Design 3A process (Alert → Assessment → Action) rather than standalone metric

---

## Cross-References

- **Multi-Sensor Fusion Methodology**: See [../../shared/multi-sensor-fusion-methodology.md](../../shared/multi-sensor-fusion-methodology.md)
- **Algorithm Validation**: See [../../review-validation/references/validation-protocol.md](../../review-validation/references/validation-protocol.md)
- **NOL Pain Index**: See [./nol-pain-index.md](./nol-pain-index.md) for another multi-sensor composite example
- **Alert Threshold Design**: See [../../rpm-platform/references/alert-threshold-design.md](../../rpm-platform/references/alert-threshold-design.md)

---

## References

- HeartLogic Alert Management Guide (Boston Scientific)
- MultiSENSE Study: Boehmer et al., Gardner et al.
- HeartLogic Presentation (2019): Real-world performance metrics
