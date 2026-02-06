# Sensor Evaluation Criteria & Selection Framework

> **Parent Skill**: [Device Selection](../SKILL.md)  
> **Related**: [Wearable Sensors](./wearable-sensors.md), [Platform Biomarkers](./platform-biomarkers.md)

## Overview

This framework provides systematic criteria for evaluating sensors and devices for digital health applications. It covers technical specifications, validation requirements, practical constraints, and regulatory considerations.

---

## Evaluation Matrix

| Category | Criterion | Questions to Ask | Acceptance Threshold |
|----------|-----------|------------------|----------------------|
| **Technical** | Sampling Rate | Is it sufficient for biomarker temporal resolution? | ≥2x Nyquist frequency of signal |
| | Dynamic Range | Can it capture full signal amplitude? | Covers expected physiological range + 20% margin |
| | Resolution | Sufficient bit depth for signal-to-noise ratio? | ≥12-bit for most biosignals |
| | Latency | Real-time processing required? | <1s for alerts, <5s for feedback loops |
| **Validation** | Analytical | Validated against gold standard? | Published metrics (RMSE, correlation, Bland-Altman) |
| | Clinical | Demonstrates clinical relevance? | Correlation with clinical scales/outcomes (r >0.7) |
| | Population | Validated in target population? | Study cohort matches your COU |
| **Practical** | Battery Life | Sufficient for study duration? | ≥Study period or <20% charging burden |
| | Form Factor | Acceptable to target population? | Patient feedback/pilot testing |
| | Water Resistance | Required for compliance? | IP67/IP68 if showering during monitoring |
| | Cost | Fits budget? | Per-patient cost vs. total budget |
| **Regulatory** | Clearance | FDA/CE Mark required? | Depends on COU (medical vs. wellness claim) |
| | Data Ownership | Can you access raw data? | Full raw data access for research |
| | Cybersecurity | HIPAA/GDPR compliant? | Encryption, secure transmission, audit logs |

---

## Technical Specifications Deep Dive

### 1. Sampling Rate Requirements

**Nyquist Theorem**: Sample at ≥2x the highest frequency component in the signal.

| Signal Type | Typical Frequency Range | Minimum Sampling Rate | Recommended Sampling Rate |
|-------------|-------------------------|----------------------|---------------------------|
| **Skin Temperature** | DC - 0.1 Hz | 0.2 Hz | 1 Hz |
| **Electrodermal Activity (EDA)** | DC - 1 Hz | 2 Hz | 4-8 Hz |
| **Respiratory Rate** | 0.1 - 1 Hz (6-60 brpm) | 2 Hz | 4-10 Hz |
| **Heart Rate (from PPG)** | 0.5 - 4 Hz (30-240 bpm) | 8 Hz | 32-64 Hz |
| **Photoplethysmography (PPG waveform)** | DC - 20 Hz | 40 Hz | 64-128 Hz |
| **Electrocardiography (ECG)** | 0.05 - 100 Hz | 200 Hz | 250-500 Hz |
| **Accelerometry (Gait)** | DC - 20 Hz | 40 Hz | 50-100 Hz |
| **Accelerometry (Tremor)** | 3 - 12 Hz (Parkinsonian tremor) | 25 Hz | 50-100 Hz |
| **Gyroscope (Movement)** | DC - 50 Hz | 100 Hz | 100-200 Hz |

**Example Decision**:
- **Biomarker**: Nocturnal scratch detection (rhythmic hand movements during sleep)
- **Frequency**: Scratch frequency ~1-3 Hz
- **Nyquist**: 6 Hz minimum
- **Selected**: 64 Hz accelerometer (provides margin for harmonics and feature extraction)

### 2. Dynamic Range & Resolution

**Dynamic Range**: Ratio between largest and smallest measurable signal.

| Sensor | Typical Range | Bit Depth | Resolution Example |
|--------|---------------|-----------|-------------------|
| **Accelerometer** | ±2g to ±16g | 12-16 bit | 16-bit at ±16g = 0.49 mg/LSB |
| **Gyroscope** | ±250 dps to ±2000 dps | 16 bit | 16-bit at ±2000 dps = 61 mdps/LSB |
| **PPG** | 0 - 3.3V (ADC input) | 12-24 bit | 24-bit = 0.2 μV resolution |
| **EDA** | 0.01 - 100 μSiemens | 16-24 bit | High resolution needed for tonic changes |
| **Temperature** | -40°C to +85°C | 12-16 bit | 0.01°C - 0.1°C resolution |

**Trade-off**: Higher resolution (more bits) increases power consumption and data storage requirements.

**Selection Rule**:
- **Low-noise environment**: 12-bit sufficient (most wearables)
- **High-noise or subtle signals**: 16-24 bit (research-grade devices)

### 3. Motion Artifact Tolerance

**Challenge**: Movement creates noise in most biosignals (especially PPG, ECG).

**Mitigation Strategies**:
| Strategy | Description | Example Device Feature |
|----------|-------------|------------------------|
| **Multi-Wavelength PPG** | Combine Red + Green LEDs to cancel motion artifacts | EmbracePlus uses Red/Green/IR |
| **Accelerometer Fusion** | Use accelerometer data to detect and filter motion epochs | "Motion-validated" algorithms |
| **Adaptive Filtering** | Dynamically adjust filter cutoffs based on detected motion | Real-time signal processing |
| **Template Matching** | Compare current signal to established templates, reject outliers | QRS detection in ECG (GE EK-Pro) |

**Validation Metric**: Compare accuracy during **no-motion** vs. **motion** conditions.
- Example: EmbracePlus Pulse Rate - RMSE <3 bpm (no motion) vs. RMSE <5 bpm (motion)

---

## Validation Requirements

### Analytical Validation (V3 Framework - Step 2)

**Question**: Does the device measure the **physical parameter** accurately?

**Gold Standards by Modality**:
| Measurement | Gold Standard | Validation Metric |
|-------------|---------------|-------------------|
| **Heart Rate** | ECG (3-12 lead) | RMSE (bpm), Correlation (r), Bland-Altman |
| **SpO2** | FDA-cleared co-oximeter (arterial blood gas) | RMSE (%), ≤3% acceptable |
| **Blood Pressure** | Auscultatory sphygmomanometer | AAMI/ISO 81060-2 standard (±5 mmHg) |
| **Sleep Staging** | Polysomnography (PSG) | Confusion matrix, Kappa, F-score per stage |
| **Gait Parameters** | Instrumented walkway (GAITRite) | RMSE (stride length, cadence), ICC |
| **Arrhythmia Detection** | Holter monitor + expert annotation | Sensitivity, Specificity, PPV, NPV per arrhythmia type |

**Acceptance Criteria**:
- **Correlation**: r > 0.9 (excellent), r > 0.7 (acceptable)
- **RMSE**: <5% of measurement range
- **Bland-Altman**: 95% limits of agreement within clinically acceptable range

### Clinical Validation (V3 Framework - Step 3)

**Question**: Does the measurement reflect **clinical status** or **health outcomes**?

**Types of Clinical Validity**:
1. **Convergent Validity**: Correlation with established clinical scales
   - Example: Step count (device) vs. mobility questionnaire (UPDRS Mobility subscore) → r > 0.7
2. **Known-Groups Validity**: Ability to distinguish between groups
   - Example: Gait variability distinguishes PD patients from healthy controls (p < 0.001)
3. **Sensitivity to Change**: Detect treatment effects
   - Example: Scratch duration decreases after therapy (effect size d > 0.5)

---

## Practical Constraints Checklist

### Battery Life Analysis

**Formula**: Battery Life (hours) = Battery Capacity (mAh) / Average Current Consumption (mA)

**Typical Current Draw**:
| Component | Current (mA) | Power Management |
|-----------|--------------|------------------|
| **Microcontroller (active)** | 5-20 mA | Duty cycle, sleep modes |
| **PPG (continuous)** | 10-50 mA | LED intensity, sampling rate, active channels (R/G/IR) |
| **Accelerometer (continuous)** | 0.1-1 mA | Low power modes, motion-triggered wake |
| **Bluetooth (transmitting)** | 10-30 mA | Batched transmission, connection intervals |
| **GPS (active)** | 50-100 mA | Intermittent fixes, A-GPS |

**Study Duration Planning**:
- **24-hour study**: 1-day battery acceptable, charge overnight
- **7-day study**: Multi-day battery (2-7 days) or plan charging protocol
- **14+ day study**: Disposable patch (VitalPatch 7-14 days) or swap devices mid-study

### Compliance Factors

**Form Factor Preferences** (patient feedback studies):
| Population | Preferred Form Factor | Compliance Rate |
|------------|----------------------|-----------------|
| **Elderly (65+)** | Chest patch > Wrist (avoid watch clasp difficulty) | Patch: 85%, Wrist: 70% |
| **Young Adults (18-35)** | Wrist > Chest (aesthetics, familiarity) | Wrist: 90%, Patch: 75% |
| **Athletes** | Chest strap > Wrist (accuracy during exercise) | Chest: 95%, Wrist: 80% |
| **Children (8-12)** | Wrist > Patch (peer acceptance, less intrusive) | Wrist: 85%, Patch: 60% |

**Water Resistance Impact**:
- **No water resistance**: Patients must remove during showers → 10-20% data loss
- **IP67/IP68**: Continuous wear → <5% data loss (only during charging)

---

## Regulatory Clearance Pathways

### FDA Classification

| Class | Risk | Clearance | Examples |
|-------|------|-----------|----------|
| **Class I** | Low | Exempt or 510(k) | General wellness devices, fitness trackers (if no medical claims) |
| **Class II** | Moderate | 510(k) (predicate) | Most wearable ECG/PPG monitors, arrhythmia detectors |
| **Class III** | High | PMA (Premarket Approval) | Implantable cardiac devices, life-sustaining devices |

**Medical Device vs. Wellness**:
- **Medical Claim** (requires clearance): "Detects atrial fibrillation", "Monitors blood glucose"
- **Wellness Claim** (exempt): "Tracks activity", "Estimates sleep quality", "Monitors general fitness"

**Implication for Research**:
- **Clinical Trial Endpoint**: Require FDA-cleared or CE-marked device
- **Exploratory Biomarker**: Wellness device acceptable, but mention limitation in publications

### Data Access & Ownership

**Critical Questions**:
1. **Raw Data Access**: Can you export raw PPG, accelerometer data? Or only processed outputs (HR, steps)?
2. **Data Retention**: How long is data stored on device/cloud?
3. **Third-Party Use**: Can manufacturer use your study data for algorithm improvements?
4. **GDPR/HIPAA**: Is data pipeline compliant with regulations?

**Red Flags**:
- Proprietary "black box" algorithms with no raw data access
- Data retention <study duration (risk of data loss before export)
- Unclear data ownership terms in user agreement

---

## Decision Framework: Scorecard

Use this scorecard to compare devices objectively:

| Criterion | Weight | Device A | Device B | Device C |
|-----------|--------|----------|----------|----------|
| **Sampling Rate** | 20% | 4/5 | 5/5 | 3/5 |
| **Validation Evidence** | 25% | 5/5 | 3/5 | 4/5 |
| **Battery Life** | 15% | 3/5 | 5/5 | 4/5 |
| **Compliance (Form Factor)** | 15% | 4/5 | 4/5 | 5/5 |
| **Cost** | 10% | 3/5 | 4/5 | 2/5 |
| **Regulatory Clearance** | 10% | 5/5 | 0/5 | 5/5 |
| **Data Access** | 5% | 5/5 | 3/5 | 5/5 |
| **Weighted Score** | 100% | **4.15** | **3.85** | **4.00** |

**Score Interpretation**:
- 4.5-5.0: Excellent fit, proceed with procurement
- 3.5-4.4: Good fit, acceptable with minor trade-offs
- 2.5-3.4: Marginal fit, consider alternatives
- <2.5: Poor fit, do not proceed

---

## Common Selection Errors

| Error | Problem | Solution |
|-------|---------|----------|
| **Choosing Consumer Device for Clinical Endpoint** | No regulatory clearance, proprietary algorithms | Use research-grade or FDA-cleared device for primary endpoints |
| **Ignoring Motion Artifacts** | Device validated only at rest, but study involves activity | Verify motion-validated performance metrics |
| **Underestimating Compliance Impact** | Selected chest patch for 6-month study in young adults | Pilot test form factor with target population before full study |
| **Black Box Algorithm** | Can't validate or reproduce results | Negotiate raw data access or select open-algorithm device |
| **Sampling Rate Mismatch** | 32 Hz accelerometer for tremor detection (needs >50 Hz) | Define minimum sampling requirements BEFORE device selection |

---

## Cross-References

- **Validation Framework**: See [../../shared/clinical-validation-framework.md](../../shared/clinical-validation-framework.md) for V3 Framework details
- **Algorithm Selection**: See [../../algo-development/SKILL.md](../../algo-development/SKILL.md) for choosing algorithms after device is selected
- **Device Comparison Matrix**: See [../../shared/device-comparison-matrix.md](../../shared/device-comparison-matrix.md) for side-by-side specs

---

## References

- V3 Framework: Verification, Analytical Validation, Clinical Validation (Digital Medicine Society)
- FDA Guidance: Digital Health Technologies for Remote Data Acquisition (2023)
- ISO 81060-2: Non-invasive sphygmomanometers - Clinical investigation of automated measurement type
- AAMI/ANSI Standard: Electronic or automated sphygmomanometers
