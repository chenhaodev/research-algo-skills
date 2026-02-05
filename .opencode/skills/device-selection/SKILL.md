---
name: device-selection
description: Guide for sensor and device selection in digital measure development, covering wearables, patches, and implantable devices with validation criteria
version: 1.0.0
author: OpenCode
license: Apache-2.0
tags:
  - device selection
  - sensor selection
  - biomarker feasibility
  - wearable sensors
  - biosensors
  - validation metrics
  - PPG
  - EDA
  - accelerometer
---

# Device Selection for Digital Measures

## Quick Reference

### Device Type Comparison

| Device Type | Form Factor | Typical Sensors | Battery Life | Use Case | Example |
|-------------|-------------|-----------------|--------------|----------|---------|
| **Wrist Wearable** | Watch/band | PPG, Accel, Gyro, EDA, Temp | 1-7 days | Continuous vitals, activity, sleep | EmbracePlus, Apple Watch, LifeQ |
| **Chest Patch** | Adhesive patch | ECG, Accel, Temp, Impedance | 7-14 days | Cardiac monitoring, RPM | VitalPatch, Zio Patch |
| **Ring** | Finger ring | PPG, Temp, Accel | 4-7 days | Sleep, HRV, recovery | Oura Ring |
| **Implantable** | Subcutaneous/cardiac | ECG, Impedance, Pressure, Heart sounds | Years | Long-term monitoring, HF | Implantable loop recorder, CRT-D with HeartLogic |

### Selection Criteria Priority

1. **Signal Quality**: Can the sensor capture the required phenomenon with sufficient fidelity?
2. **Sampling Rate**: Does it meet the minimum frequency for the biomarker (e.g., >50Hz for tremor)?
3. **Validation Evidence**: Has the device been validated for your specific clinical application?
4. **Compliance**: Will patients wear it for the required duration?
5. **Regulatory**: Does it have necessary clearances (CE Mark, FDA 510(k))?

---

## When to Use This Skill

Activate this skill when you need to:
*   Select a sensor or device for a digital biomarker study
*   Evaluate hardware feasibility for a digital measure
*   Compare device specifications and validation evidence
*   Assess whether existing consumer devices are suitable for clinical use
*   Determine sampling requirements for a physiological signal
*   Plan device procurement for a validation study

**Trigger Keywords**: `sensor selection`, `device evaluation`, `biomarker feasibility`, `hardware selection`, `wearable device`, `biosensor`, `sampling rate`, `validation metrics`

---

## How to Use This Skill

### 5-Step Device Selection Workflow

#### Step 1: Define Biomarker Requirements
*   **Signal Type**: What physiological phenomenon are you measuring? (e.g., heart rate, skin conductance, movement)
*   **Sampling Rate**: Minimum frequency required (e.g., 1 Hz for temperature, 64 Hz for PPG, 100+ Hz for ECG, 250+ Hz for high-quality ECG)
*   **Form Factor**: Where must the sensor be placed? (wrist, chest, finger, ankle)
*   **Duration**: How long must it record? (hours, days, weeks)
*   **Context**: Resting vs. active monitoring? Lab vs. free-living?

#### Step 2: Evaluate Signal Quality & Sampling Requirements
*   **Resolution**: Bit depth (8-bit, 12-bit, 16-bit) and dynamic range
*   **Noise Floor**: Acceptable signal-to-noise ratio for your application
*   **Motion Artifacts**: Is motion compensation required?
*   **Environmental Factors**: Temperature, humidity, skin tone effects

#### Step 3: Compare Candidate Devices
Use the device comparison matrix (see `../shared/device-comparison-matrix.md`) to evaluate:
*   Technical specifications (sampling rate, resolution, sensors)
*   Validation evidence (published studies, accuracy metrics)
*   Practical constraints (cost, availability, data access)
*   Regulatory status (CE Mark, FDA clearance)

#### Step 4: Assess Validation Evidence
*   **Analytical Validation**: Does the device accurately measure the physical parameter? (e.g., steps = steps)
*   **Clinical Validation**: Does the measurement reflect clinical status? (e.g., step count = mobility)
*   **Key Metrics**: Sensitivity, specificity, RMSE, Bland-Altman limits of agreement, correlation with gold standard
*   **Population**: Was validation performed in your target population?

#### Step 5: Consider Practical Constraints
*   **Cost**: Purchase price, consumables, data platform fees
*   **Data Access**: Can you access raw data? Or only processed outputs?
*   **Battery Life**: Sufficient for study duration without frequent charging?
*   **Compliance**: Will patients tolerate wearing it? (comfort, aesthetics, water resistance)
*   **Regulatory**: Does it meet your study's regulatory requirements?

---

## Device Categories & Technical Specifications

### Wrist Wearables

**Advantages**: High compliance, familiar form factor, multi-sensor integration  
**Limitations**: Motion artifacts, skin contact variability, battery life trade-offs

#### Example: EmbracePlus (2021)
*   **Sensors**:
    *   PPG: 64 Hz sampling, Red/Green/IR LEDs + 8 photodiodes (SpO2 capable)
    *   EDA (Electrodermal Activity): 4 Hz, range 0.01-100 μSiemens
    *   Accelerometer + Gyroscope (IMU): 64 Hz, ±16g / ±2000 dps, 16-bit resolution
    *   Temperature: 1 Hz, 0.01°C resolution, ±0.1°C accuracy (30-45°C)
*   **Battery**: 2+ days (Profile A: PR/RR), 1+ day (Profile B: SpO2)
*   **Water Resistance**: IP67 (1m depth, 30 mins)
*   **Validation Metrics**:
    *   Pulse Rate: RMSE <3 bpm (no motion), RMSE <5 bpm (motion) vs. ECG
    *   SpO2: RMSE <3% vs. FDA-cleared co-oximeter
    *   Respiratory Rate: RMSE <3 brpm vs. FDA-cleared reference
    *   Sleep Detection: 100% sensitivity, 90% F-score vs. polysomnography
    *   Temperature: Max error 0.07°C vs. reference thermometer

#### Example: Empatica E4 (2014 - Legacy)
*   **Activity Limitation**: Not suitable for running or high-intensity physical activity
*   **Firmware-Locked Features**: Ambient temperature and accelerometer range (±4g/±8g) required custom firmware
*   **Water Resistance**: Not certified at launch (TBD)
*   **Evolution Note**: Compare to EmbracePlus 2021 to see 7-year advancement in validation, water resistance, and clinical use cases

#### Example: LifeQ Multi-Biomarker Platform (2023)
*   **Platform Architecture**: PPG + Accelerometer → Real-time signal management → Higher-order biomarkers
*   **Derived Biomarkers**:
    *   **AFib Detection**: Beat-to-Beat Interval (BBI) analysis, Recall 0.9, Specificity 0.98
    *   **Sleep Staging**: HR + BBI + Accelerometer → Sleep architecture (Awake, Light, Deep, REM), validated against PSG
    *   **VO2max Estimation**: 4 methods depending on data availability, MAPE 5-16% vs. indirect calorimetry (Cosmed)
    *   **COVID Onset Detection**: HR + Breathing Rate during sleep, pilot study flagged all 6/8 positive cases with sufficient baseline data
*   **Key Insight**: Demonstrates multi-biomarker platform approach where base sensors (PPG, accel) feed multiple derived metrics

### Chest Patches

**Advantages**: ECG-quality cardiac monitoring, good skin contact, disposable  
**Limitations**: Single-use cost, adhesive irritation, limited battery life

#### Example: VitalPatch (VitalConnect)
*   **Sensors**: HR, Respiratory Rate, Body Posture, Activity (steps), Skin Temperature
*   **Duration**: 7-14 days continuous wear
*   **Use Case**: Remote patient monitoring (RPM), post-discharge monitoring
*   **Integration**: Bluetooth → App → Cloud → Clinician dashboard

---

## Validation Requirements

### Analytical Validation
Confirm the device measures the physical parameter accurately:
*   **Reference Standard**: What is the ground truth? (e.g., ECG for HR, polysomnography for sleep)
*   **Metrics**: RMSE, MAE, correlation (Pearson's r), Bland-Altman agreement
*   **Conditions**: Test across activity levels, skin tones, body positions

### Clinical Validation
Confirm the measurement reflects clinical status:
*   **Convergent Validity**: Correlation with established clinical scales (e.g., NRS for pain, UPDRS for Parkinson's)
*   **Known-Groups Validity**: Distinguish between healthy and diseased populations
*   **Sensitivity to Change**: Detect treatment effects or disease progression

### Real-World Performance
*   **Compliance**: Actual wear time in free-living conditions
*   **Data Completeness**: Percentage of valid data captured
*   **Alert Performance**: False positive rate, sensitivity for clinical events

For detailed validation protocols, see `../review-validation/references/validation-protocol.md`

---

## Common Pitfalls & Solutions

| Pitfall | Problem | Solution |
|---------|---------|----------|
| **"Black Box" Algorithms** | Consumer device uses proprietary algorithm you can't validate | Negotiate raw data access or choose research-grade device with open algorithms |
| **Validation Mismatch** | Device validated in healthy volunteers, but you need it for sick patients | Conduct your own validation study in target population |
| **"Good Enough" Sampling** | Chose 32 Hz sampling, but tremor analysis needs >50 Hz | Define minimum sampling requirements BEFORE device selection |
| **Battery vs. Sampling Trade-off** | High sampling rate drains battery too fast for study duration | Use Profile A/B configurations or select device with longer battery |
| **Water Resistance Gap** | Device not waterproof → patients remove during showers → data gaps | Require IP67/IP68 rating or plan for missing data imputation |

---

## Case Studies

### Case Study 1: Nocturnal Scratch Detection (Atopic Dermatitis)
*   **Requirement**: Detect rhythmic hand movements during sleep
*   **Device Selected**: Wrist accelerometer + gyroscope (64 Hz)
*   **Validation**: 90% sensitivity/specificity vs. video annotation (IR camera gold standard)
*   **Outcome**: Strong correlation (r > 0.7) with patient-reported itch severity

### Case Study 2: Gait Analysis (Parkinson's Disease)
*   **Requirement**: Detect gait asymmetry and freezing of gait
*   **Device Selected**: Ankle-worn IMU (100 Hz)
*   **Validation**: Step Time Variability metric validated against instrumented walkway
*   **Outcome**: Ability to distinguish PD patients from healthy controls (known-groups validity)

---

## Cross-References & Related Skills

### Internal Skills
*   `../algo-development/SKILL.md` - Algorithm selection after device is chosen
*   `../research-strategy/SKILL.md` - Phase 2: Measurement Approach (device selection context)
*   `../clinical-indices/SKILL.md` - Multi-sensor fusion when combining multiple devices

### Shared Resources
*   `../shared/device-comparison-matrix.md` - Detailed comparison of research-grade devices
*   `../shared/clinical-validation-framework.md` - V3 Framework (Verification, Analytical, Clinical Validation)

### External Standards
*   **V3 Framework (DiMe)**: Verification, Analytical Validation, Clinical Validation
*   **FDA Guidance**: Digital Health Technologies for Remote Data Acquisition
*   **ISO 13485**: Quality management for medical devices

---

## Disclaimer

**Professional Judgment Required**: This skill provides guidance for device selection based on technical specifications and validation evidence. It does not constitute regulatory, clinical, or legal advice. Device suitability must be determined on a case-by-case basis considering the specific clinical application, patient population, and regulatory requirements. Always consult with regulatory affairs professionals, clinical experts, and device manufacturers before making final device selections for clinical studies.
