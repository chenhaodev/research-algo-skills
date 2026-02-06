# Platform Biomarkers: LifeQ Multi-Modal Approach

> **Parent Skill**: [Device Selection](../SKILL.md)  
> **Related**: [Wearable Sensors](./wearable-sensors.md), [Multi-Sensor Fusion](../../shared/multi-sensor-fusion-methodology.md)

## Overview

LifeQ (2023) demonstrates a **platform architecture** where base sensors (PPG + accelerometer) feed multiple higher-order biomarker algorithms. This reference documents their multi-biomarker approach, validation strategies, and algorithmic methods across AFib detection, sleep staging, activity classification, VO2max estimation, COVID symptom tracking, and fitness scoring.

**Key Insight**: Rather than building single-purpose devices, modern platforms derive multiple clinical biomarkers from shared sensor inputs, amortizing hardware costs across multiple use cases.

---

## Platform Architecture

### Sensor Layer (Hardware)

**Primary Sensors**:
- **Photoplethysmography (PPG)**: Red, Green, Infrared LEDs + photodiodes
- **Accelerometer**: 3-axis, motion sensing
- **User Profile**: Age, gender, height, weight, resting HR (provided at onboarding)

**Signal Processing Layer** (Real-Time):
- Optimize PPG signal quality accounting for:
  - Skin color
  - Temperature
  - Blood perfusion
  - Motion artifacts
- **Signal Confidence Tracking**: Continuously assess if signal quality is sufficient for metric extraction
- **Adaptive Algorithms**: Adjust to activity state (intense vs. sedentary) to balance accuracy and power consumption

### Biomarker Layer (Algorithms)

From these base sensors, LifeQ derives:
1. AFib Screening & Severity
2. Sleep Architecture & Quality
3. Activity Intensity Minutes
4. VO2max Estimation
5. COVID-19 Onset Detection
6. Fitness Health Score

---

## AFib Detection

### Algorithm Inputs
- **Primary**: Beat-to-Beat Intervals (BBI) from PPG, measured in milliseconds
- **Context**: Heart Rate (HR), Respiratory Rate (RR)

### Method
- Detect **irregular heart rhythms** characteristic of Atrial Fibrillation (chaotic electrical signals)
- Analyze BBI patterns for irregularity vs. normal sinus rhythm

### Outputs
- **AFib Screening**: Binary (detected / not detected)
- **Severity**: High, Moderate

### Constraints
- Requires events **>30 beats** for reliable detection
- Dependent on good HR and RR interval data (quality gating)

### Validation

**Datasets**:
- **Internal Collection**: 143 individuals (4 diagnosed with AFib), wearing ECG (Bitium Faros) + wrist PPG device simultaneously
- **Open Source**:
  - MIT-BIH Atrial Fibrillation Database
  - MIT-BIH Normal Sinus Rhythm Database
  - Long Term Atrial Fibrillation Database

**Methods**:
- Validated using **Annotated PPG data** (manual labels)
- Validated using **Annotated ECG data** (gold standard)

**Results** (PPG testing, 620 datasets):
- **Recall**: 0.9 (90% sensitivity - detects 90% of true AFib events)
- **Specificity**: 0.98 (98% - 2% false positive rate)

**Clinical Implication**: High specificity (0.98) minimizes false alarms, critical for consumer wearable adoption where alert burden must be low.

---

## Sleep Staging

### Algorithm Inputs
- **Heart Rate**: Continuous HR from PPG
- **Accelerometer**: Determine desire/onset of sleep (movement cessation)
- **Beat-to-Beat Intervals (BBI)**: Determine transitions between sleep stages (HRV changes)

### Method
- **Sleep Architecture** derived from HR patterns and movement:
  - **Awake**: High movement, variable HR
  - **Light Sleep**: Reduced movement, moderate HRV
  - **Deep Sleep**: Minimal movement, low HR, reduced HRV
  - **REM**: Minimal movement, elevated HR, increased HRV

### Outputs
- **Sleep Stages**: Awake, Light, Deep, REM
- **Sleep Start/Wake Times**
- **Sleep Quality Score**: 0-100

### Validation

**Reference Standard**: **Polysomnography (PSG)** - gold standard for sleep staging

**Study**:
- Over **250 individual datasets** collected with partners:
  - London Sleep Clinic
  - 7HourSleep (commercial sleep study provider)
- Method: Simultaneous PSG + LifeQ wrist device

**Metrics**:
- **Confusion matrices**: Per-stage classification accuracy
- **Kappa scores**: Agreement between LifeQ and PSG staging
- **Competitive Benchmarking**: Compared against Oura, Fitbit, Garmin algorithms

**Result**: LifeQ claims competitive performance vs. established consumer sleep trackers, validated against PSG.

---

## Activity Classification & Intensity Minutes

### Algorithm Inputs
- **Real-time Heart Rate**: Continuous HR from PPG
- **Heart Rate Reserve (HRR)**: Calculated as (Max HR - Resting HR)

### Method: LifeQ Intensity Minutes
- Classify activity intensity based on **percentage of HRR utilized**:
  - **Light**: <40% HRR
  - **Moderate**: 40-60% HRR
  - **Vigorous**: >60% HRR
- Accumulate minutes in each intensity zone over time

### Outputs
- **Daily Intensity Minutes**: Breakdown by Light / Moderate / Vigorous
- **Weekly Totals**: For tracking WHO physical activity guidelines (150 min moderate or 75 min vigorous per week)

### Validation
- **Based on peer-reviewed literature**: Dose-response curves between moderate-to-vigorous physical activity (MVPA) and reduced all-cause mortality risk
- **Method**: Indirect validation through established HR-activity relationships rather than direct gold-standard comparison

---

## VO2max Estimation

LifeQ offers **four distinct solutions** for VO2max estimation based on available data:

### 1. Profile VO2max
- **Inputs**: Age, Gender, Height, Weight, Resting HR
- **Method**: Population-based regression equations
- **Use Case**: Initial estimate for users without activity data
- **Accuracy**: MAPE ~15-16% (Mean Absolute Percentage Error)

### 2. Treadmill Protocol
- **Inputs**: User-initiated treadmill test using speed and HR
- **Method**: Sub-maximal exercise test estimation
- **Use Case**: Gym-based assessment
- **Accuracy**: MAPE ~5% (best accuracy)

### 3. Lifestyle VO2max
- **Inputs**: Profile data + history of moderate/vigorous activity sessions
- **Method**: Regression incorporating activity pattern over time
- **Use Case**: General users with consistent activity tracking
- **Accuracy**: MAPE ~15-16%

### 4. Automated Running
- **Inputs**: GPS speed + HR for users who run ≥3 times/month
- **Method**: Running economy equations
- **Use Case**: Runners with consistent training
- **Accuracy**: MAPE ~10-12%

### Validation

**Reference Standard**: **Graded Exercise Testing (GXT)** using **indirect calorimetry** (Cosmed device - gold standard for VO2max measurement)

**Study Cohorts**:
- High BMI individuals
- Athletic individuals (runners, cyclists)
- General population

**Results**:
| Method | MAPE vs. GXT | Recommended Use Case |
|--------|--------------|----------------------|
| Treadmill Protocol | ~5% | Gym-based testing, highest accuracy |
| Automated Running | ~10-12% | Regular runners (≥3x/month) |
| Profile / Lifestyle | ~15-16% | General users, initial estimate |

**Clinical Implication**: For research studies requiring validated VO2max, request Treadmill Protocol from participants. For population health monitoring, Profile/Lifestyle is acceptable.

---

## COVID-19 Symptom Tracking

### Algorithm Components

#### 1. Pre-Infection Risk Calculation
- **Inputs**: Profile (age, BMI, gender) + co-morbidities (captured via questionnaire)
- **Output**: Risk category (Low, Moderate, High) for severe COVID-19 outcomes
- **Validation**: Risk categorization validated against cohort of **843 individuals**

#### 2. Disease Onset Detection
- **Inputs**: Heart Rate + Breathing Rate during sleep
- **Method**: Detect **deviations from user's established baseline**
  - Track nightly HR and BR patterns
  - Flag anomalies (sustained elevation in resting HR, increased BR)
- **Output**: Alert to user suggesting potential illness onset

**Validation**:
- **Pilot Study**: 126 individuals monitored over 27 days
- **Positive Cases**: 8 individuals tested positive for COVID-19 during study
- **Results**: Algorithm correctly flagged **6/8 positive cases** (75% sensitivity)
  - **Timing**: Flagged on or before symptom onset day
  - **Caveat**: 2/8 cases missed due to insufficient baseline data (enrolled too close to infection)

**Clinical Implication**: Requires ≥7-14 days baseline data for personalized threshold calibration. Early detection capability demonstrated, but not a diagnostic tool.

#### 3. Symptom Status Tracking
- **User Feedback**: Web dashboard for logging symptoms (fever, cough, fatigue, loss of taste/smell)
- **Progression Monitoring**: Track symptom evolution over time

---

## Fitness Health Score (FHS)

### Algorithm Inputs
- **LifeQ Lifestyle VO2max**: Estimated VO2max from Profile + Activity history

### Method
- **Normalize for age and gender**: Compare user's VO2max to age-matched population norms
- **Rolling Average**: 31-day average to smooth daily fluctuations
- **Score**: 0-100, where higher score = better cardiovascular fitness

### Validation
- **Reference**: Engineered to reflect literature-derived VO2max algorithms
- **Mortality Data**: Stamatakis et al. analysis of **32,319 subjects** showing relationship between VO2max and mortality rate
- **Outcome**: Higher FHS corresponds to lower hazard ratios (mortality risk) in pilot cohorts

**Use Case**: Population health dashboards, wellness programs, longitudinal fitness tracking

---

## Platform Advantages

### 1. Multi-Biomarker Efficiency
- **Single Hardware** (PPG + Accel) → **Multiple Clinical Outputs** (AFib, Sleep, VO2max, COVID, Fitness)
- **Cost Amortization**: R&D and manufacturing costs spread across multiple biomarkers
- **User Experience**: One device provides comprehensive health monitoring vs. multiple single-purpose devices

### 2. Shared Validation Infrastructure
- **Data Collection**: Sleep study data can validate both sleep staging AND resting HR metrics
- **Algorithm Synergy**: Improvements to BBI extraction benefit both AFib detection and sleep staging

### 3. Continuous Algorithm Updates
- **Over-the-Air Updates**: Algorithms can improve post-deployment as more validation data is collected
- **Adaptive Baselines**: Personalized thresholds improve over time with user-specific data

---

## Limitations & Considerations

### Signal Quality Gating
- All biomarkers require **"good enough" signal quality**
- **During low motion**: BBI extraction is reliable
- **During high-intensity exercise**: PPG signal may degrade → metrics suppressed
- **Implication**: Not all biomarkers available 100% of the time; data completeness varies by activity level

### Validation Gaps
- **AFib**: Validated against annotated datasets (620 cases), but real-world prospective validation in free-living conditions not detailed
- **Sleep**: Validated against PSG in controlled sleep lab, but free-living performance may differ
- **VO2max**: Treadmill protocol most accurate (~5% MAPE), but Lifestyle method has higher error (~15-16%)

### Regulatory Status
- **Not explicitly stated** in reviewed documentation whether LifeQ biomarkers have FDA 510(k) or CE Mark as medical devices
- **Implication**: Likely positioned as **wellness** platform rather than medical device; verify regulatory status before using in clinical trials requiring medical-grade data

---

## Selection Guidance

**When to Choose a Platform Approach (like LifeQ)**:
- Study requires multiple biomarkers (e.g., sleep + activity + cardiovascular)
- Budget constraints favor single device over multiple specialized devices
- Longitudinal monitoring where multiple health domains are relevant

**When to Choose Specialized Devices**:
- Regulatory requirement for medical-grade, cleared device (e.g., FDA-cleared ECG)
- Single biomarker with highest accuracy priority (e.g., gold-standard PSG for sleep clinical trials)
- Research question requires raw sensor data access (platforms may provide only processed outputs)

---

## Cross-References

- **Multi-Sensor Fusion Methodology**: See [../../shared/multi-sensor-fusion-methodology.md](../../shared/multi-sensor-fusion-methodology.md)
- **Clinical Validation Framework**: See [../../shared/clinical-validation-framework.md](../../shared/clinical-validation-framework.md)
- **Algorithm Selection**: See [../../algo-development/SKILL.md](../../algo-development/SKILL.md)
- **Composite Indices**: See [../../clinical-indices/SKILL.md](../../clinical-indices/SKILL.md) for more on HeartLogic and NOL multi-sensor approaches

---

## References

- LifeQ Platform Documentation (2023)
- Stamatakis et al. Mortality analysis (32,319 subjects, VO2max dose-response)
- MIT-BIH Databases (Atrial Fibrillation, Normal Sinus Rhythm)
