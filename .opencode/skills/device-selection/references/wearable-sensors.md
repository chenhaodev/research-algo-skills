# Wearable Sensors: Detailed Comparison

> **Parent Skill**: [Device Selection](../SKILL.md)  
> **Related**: [Platform Biomarkers](./platform-biomarkers.md), [Sensor Evaluation Criteria](./sensor-evaluation-criteria.md)

## Overview

This reference provides detailed technical specifications and validation metrics for wrist-worn wearable sensors used in digital health research. It compares legacy (Empatica E4, 2014) and modern (EmbracePlus, 2021) devices to illustrate the evolution of validation standards and clinical capabilities.

---

## Device Comparison Matrix

| Specification | Empatica E4 (2014) | EmbracePlus (2021) |
|---------------|--------------------|--------------------|
| **Form Factor** | Wrist band | Wrist watch |
| **Weight** | ~50g | 38g (with battery/band) |
| **Dimensions** | N/A | 32mm diameter, 15mm thickness |
| **Water Resistance** | TBD (not certified at launch) | IP67 (1m depth, 30 mins) |
| **Battery Life** | ~48 hours | 2+ days (Profile A), 1+ day (Profile B) |
| **Charge Time** | N/A | 90 minutes |
| **Memory** | N/A | 128 MB NOR Flash (24-36 hours data) |
| **Connectivity** | Bluetooth Smart (BLE) | Bluetooth 5 (10m range) |
| **Materials** | N/A | Polycarbonate case, SUS 316L stainless steel electrodes, biocompatible silicone band |

---

## Sensor Specifications

### Photoplethysmography (PPG)

| Feature | Empatica E4 (2014) | EmbracePlus (2021) |
|---------|--------------------|--------------------|
| **LEDs** | 2 Green, 2 Red | Red, Green, Infrared (SpO2 capable) |
| **Photodiodes** | 2 (14 mm² total area) | 8 photodiodes |
| **Sampling Rate** | 64 Hz (fixed) | 64 Hz |
| **Resolution** | 0.9 nW/Digit | N/A |
| **Derived Metrics** | Heart Rate, IBI | Pulse Rate, PRV, Respiratory Rate, SpO2 |
| **Activity Limitations** | **Not suitable for running or physical activity** | Validated for motion (RMSE <5 bpm) |

**Key Evolution**: 2021 version adds SpO2 capability (Red/IR LEDs) and validates motion performance, removing the "resting only" limitation of 2014.

### Electrodermal Activity (EDA / Skin Conductance)

| Feature | Empatica E4 (2014) | EmbracePlus (2021) |
|---------|--------------------|--------------------|
| **Sampling Rate** | 4 Hz | 4 Hz |
| **Range** | N/A | 0.01 μSiemens – 100 μSiemens |
| **Resolution** | ~900 pico Siemens | N/A |
| **Excitation** | Alternating current (8Hz) | N/A |
| **Electrodes** | Silver (Ag) plated, ABS core, screw-in replaceable | SUS 316L stainless steel (integrated) |
| **Derived Metrics** | Skin Conductance Level | Skin Conductance Level (1 min resolution) |

**Key Evolution**: 2021 version integrates electrodes (non-replaceable), expanding range to 100 μSiemens.

### Accelerometer & Gyroscope (IMU)

| Feature | Empatica E4 (2014) | EmbracePlus (2021) |
|---------|--------------------|--------------------|
| **Sampling Rate** | 32 Hz | 64 Hz |
| **Range (Accel)** | Default ±2g (±4g/±8g required custom firmware) | ±16g |
| **Range (Gyro)** | N/A | ±2000 dps |
| **Resolution** | 8-bit | 16-bit |
| **Derived Metrics** | Activity classification | Activity, Sleep Detection, Wearing Detection |

**Key Evolution**: 2021 version doubles sampling rate, adds gyroscope, increases resolution from 8-bit to 16-bit, and adds sleep/wearing detection algorithms.

### Temperature

| Feature | Empatica E4 (2014) | EmbracePlus (2021) |
|---------|--------------------|--------------------|
| **Sensor Type** | Infrared thermopile (optical) | Contact thermometer |
| **Sampling Rate** | 4 Hz | 1 Hz |
| **Resolution** | 0.02°C | 0.01°C |
| **Accuracy** | N/A | ±0.1°C (30-45°C range) |
| **Range** | N/A | 0 - 85°C |
| **Ambient Temperature** | Required custom firmware | N/A |

**Key Evolution**: 2021 version has validated accuracy specification (±0.1°C), validated against reference thermometer (max error 0.07°C).

---

## Validation Metrics

### Empatica E4 (2014)

**Limitations Explicitly Stated**:
- Heart Rate / IBI: **"Not suitable for running or physical activity"**
- Designed strictly for **resting heart rate** in everyday scenarios
- Algorithm discards non-prototypical beats but does **not** smooth the sequence
- Motion artifacts remain limiting factor despite multi-wavelength combination

**No Published Validation Metrics**: Specification sheet did not include external validation studies, gold-standard comparisons, or numerical accuracy metrics.

### EmbracePlus (2021)

**Pulse Rate Validation** (vs. ECG):
- **No-motion condition**: RMSE < 3 bpm
- **Motion condition**: RMSE < 5 bpm
- **Method**: Compared against ECG gold standard

**SpO2 Validation** (vs. FDA-cleared co-oximeter):
- **Accuracy**: RMSE < 3%
- **Method**: Desaturation study using FDA-cleared reference device

**Respiratory Rate Validation** (vs. FDA-cleared reference):
- **Accuracy**: RMSE < 3 brpm (breaths per minute)

**Sleep Detection Validation** (vs. Polysomnography):
- **Sensitivity**: 100% for sleep periods
- **Sleep/Wake Classification**: F-score 90%
- **Gold Standard**: PSG (polysomnography)

**Wearing Detection Validation**:
- **True Positive Rate**: Median 100%
- **False Positive Rate**: Median 0%

**Temperature Validation** (vs. reference thermometer):
- **Max Error**: 0.07°C

**Time Synchronization**:
- **Accuracy**: Drift < 1 second per day (NTP sync)

---

## Derived Algorithms

### Pulse Rate (PR)

**EmbracePlus (2021)**:
- **Input**: PPG (Green/Red) + Accelerometer
- **Processing**: 10-second overlapping windows, aggregated every 1 minute
- **Range**: 24-240 bpm
- **Output Suppression**: Algorithm suppresses output if confidence is low (high motion or poor fit)

### Pulse Rate Variability (PRV)

**EmbracePlus (2021)**:
- **Metric**: RMSSD (Root Mean Square of Successive Differences) calculated from inter-beat intervals (systolic peaks)
- **Resolution**: 1 minute
- **Use Case**: HRV proxy when ECG is not available

### Respiratory Rate (RR)

**EmbracePlus (2021)**:
- **Input**: PPG (Green) + Accelerometer
- **Processing**: 30-second overlapping windows
- **Range**: 4-60 brpm
- **Method**: Extract respiratory modulation from PPG amplitude and accelerometer respiratory band

### SpO2 (Oxygen Saturation)

**EmbracePlus (2021)**:
- **Input**: Red/IR PPG
- **Processing**: 10-second windows
- **Range**: 70-100%
- **Profile**: Requires Profile B configuration (Green/Red/IR LEDs active), reduces battery life to 1+ day

### Sleep Detection

**EmbracePlus (2021)**:
- **Input**: Activity-based algorithm (accelerometer patterns)
- **Output**: Classifies as Awake, Sleep, Wake (during sleep period)
- **Validation**: 100% sensitivity for sleep periods, 90% F-score for sleep/wake classification vs. PSG

---

## Practical Considerations

### Battery Life Trade-offs

| Profile | LEDs Active | Derived Metrics | Battery Life |
|---------|-------------|-----------------|--------------|
| **Profile A** | Green, Red | Pulse Rate, Respiratory Rate, PRV | 2+ days |
| **Profile B** | Green, Red, Infrared | SpO2, Pulse Rate, Respiratory Rate | 1+ day |

**Implication**: For studies requiring SpO2, plan for daily charging or accept ~50% battery life reduction.

### Motion Artifact Management

**Empatica E4 (2014)**:
- Motion compensation limited
- Activity limitation: "Not suitable for running or physical activity"
- **Use Case**: Sedentary monitoring, sleep studies, low-intensity activity

**EmbracePlus (2021)**:
- Motion-validated (RMSE <5 bpm during motion)
- **Use Case**: Free-living monitoring including moderate-intensity activity
- **Limitation**: Still not suitable for very high-intensity exercise (sprinting, contact sports)

### Water Resistance

**Empatica E4 (2014)**:
- No certified water resistance at launch
- **Implication**: Patients must remove during showers/swimming → data gaps

**EmbracePlus (2021)**:
- IP67 rated (1m depth, 30 minutes)
- **Implication**: Can wear during showers, handwashing → improved compliance and data completeness

---

## Selection Decision Tree

**Question 1: Do you need SpO2 measurement?**
- **YES** → EmbracePlus Profile B (or other SpO2-capable device)
- **NO** → Continue

**Question 2: Will patients be physically active during monitoring?**
- **YES (moderate-vigorous activity)** → EmbracePlus (motion-validated) or chest strap ECG
- **NO (sedentary/resting only)** → Empatica E4 acceptable (legacy), or EmbracePlus for better validation

**Question 3: Is water resistance critical for compliance?**
- **YES** → EmbracePlus (IP67) or other waterproof device
- **NO** → Empatica E4 acceptable if budget-constrained

**Question 4: Study duration and charging logistics?**
- **Continuous 7+ days without charging** → Consider chest patch (VitalPatch 7-14 days) or ring (Oura 4-7 days)
- **1-2 days acceptable** → EmbracePlus suitable

---

## Clinical Use Cases

### Use Case 1: Epilepsy Monitoring (Empatica E4)

- **FDA Clearance**: Embrace system (Empatica E4-based) cleared for detection of Generalized Tonic-Clonic Seizures
- **Sensors Used**: EDA + Accelerometer (not heart rate)
- **Setting**: Home monitoring during sleep
- **Rationale**: Resting-only limitation is acceptable; EDA spike detection is primary

### Use Case 2: Atopic Dermatitis Nocturnal Scratch (EmbracePlus)

- **Biomarker**: Scratch duration (rhythmic hand movements)
- **Sensors Used**: Accelerometer + Gyroscope (64 Hz)
- **Validation**: 90% sensitivity/specificity vs. video annotation
- **Rationale**: Sleep monitoring (resting), improved IMU resolution (64 Hz, 16-bit), wearing detection ensures data quality

### Use Case 3: Cardiovascular Study with Free-Living Activity (EmbracePlus)

- **Biomarkers**: Pulse Rate, PRV, Activity
- **Setting**: Home monitoring, patients instructed to maintain normal activity
- **Rationale**: Motion-validated PPG (RMSE <5 bpm during motion), waterproof for showering, better compliance

---

## Cross-References

- **Validation Standards**: See [../../shared/clinical-validation-framework.md](../../shared/clinical-validation-framework.md) for V3 Framework (Verification, Analytical, Clinical Validation)
- **Algorithm Selection**: See [../../algo-development/SKILL.md](../../algo-development/SKILL.md) for choosing algorithms for derived metrics
- **Platform Approach**: See [./platform-biomarkers.md](./platform-biomarkers.md) for multi-biomarker platforms like LifeQ

---

## References

- Empatica E4 Specification Sheet (Revision 001, November 19, 2014)
- EmbracePlus Specification Sheet (2021 version)
- Empatica FDA Clearance: Embrace system for GTCS detection (K163676)
