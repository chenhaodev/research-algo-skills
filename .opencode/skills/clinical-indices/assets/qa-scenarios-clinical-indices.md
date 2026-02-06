# QA Scenarios: Clinical Indices Skill

## Scenario 1: HeartLogic Integration into CHF Monitoring Protocol
**User Request**: "Our cardiology clinic wants to implement remote CHF monitoring. How should we use the HeartLogic index to reduce readmissions?"

**Expected Skill Activation**: `clinical-indices`

**Expected Workflow**:
1. Parse clinical goal: CHF remote monitoring, readmission reduction
2. Cross-reference `heartlogic-chf-index.md` for index composition and performance
3. Extract key metrics: 70% sensitivity, 34-day early warning, 10× risk stratification
4. Design clinical workflow: alert thresholds, triage protocol, intervention triggers
5. Integrate with existing cardiology infrastructure (EHR, telemonitoring platform)

**Expected Recommendation**:
- **HeartLogic implementation protocol**:
  - Patient selection: NYHA Class II-III, CRT-D implanted (HeartLogic requires compatible device)
  - Alert threshold: HeartLogic >16 (manufacturer default, 70% sensitivity)
  - Triage workflow:
    - Low-risk (HeartLogic 16-20): Phone call + symptom questionnaire within 48h
    - Medium-risk (HeartLogic 21-25): Nurse visit + diuretic adjustment within 24h
    - High-risk (HeartLogic >25): Cardiology consult + IV diuretic within 12h
  - Expected outcomes: 34-day early warning enables proactive diuretic adjustment, reducing ER visits by 40-50% (per validation studies)
- **Integration**: Connect CRT-D telemetry (Medtronic CareLink, Boston Scientific Latitude) to EHR via HL7 FHIR
- **Monitoring cadence**: Daily HeartLogic updates, weekly trend review by CHF nurse coordinator

**Verification**:
- [ ] HeartLogic performance metrics cited (70% sensitivity, 34-day warning)
- [ ] Patient selection criteria specified (NYHA class, device requirement)
- [ ] Triage workflow designed with risk-stratified responses
- [ ] EHR integration approach outlined

---

## Scenario 2: NOL Pain Index for Postoperative Analgesia Titration
**User Request**: "We're an anesthesiology department looking to reduce opioid use post-surgery. Can the NOL index help personalize pain management?"

**Expected Skill Activation**: `clinical-indices`

**Expected Workflow**:
1. Identify clinical context: postoperative analgesia, opioid reduction goal
2. Cross-reference `nol-pain-index.md` for validation data (AUC 0.93, 33% pain reduction)
3. Analyze NOL components: HR, HRV, PPG amplitude, GSR, movement (multi-sensor fusion)
4. Design titration protocol: NOL-guided analgesia vs standard care (patient self-report)
5. Outline equipment requirements (Medasense PMD-200 monitor) and training needs

**Expected Recommendation**:
- **NOL-guided analgesia protocol**:
  - Baseline: Preoperative NOL measurement (establish patient-specific threshold)
  - Intraoperative: Target NOL <25 (corresponds to NRS <4, per validation data)
  - Postoperative: Continuous NOL monitoring in PACU (first 2 hours)
  - Titration algorithm:
    - NOL <10: No analgesia (patient comfortable)
    - NOL 10-25: Non-opioid (acetaminophen 1g IV)
    - NOL 25-50: Weak opioid (tramadol 50mg IV)
    - NOL >50: Strong opioid (morphine 2-4mg IV)
  - Expected outcome: 33% reduction in postoperative pain scores, 20-30% reduction in opioid consumption (per validation studies)
- **Equipment**: Medasense PMD-200 (€15K/unit), requires pulse oximetry + ECG + GSR sensors
- **Training**: 4-hour workshop for anesthesiology staff (NOL interpretation, titration algorithm)

**Verification**:
- [ ] NOL validation data cited (AUC 0.93, 33% pain reduction)
- [ ] Titration algorithm specified with NOL thresholds
- [ ] Equipment requirements outlined (PMD-200, sensors)
- [ ] Expected outcomes quantified (opioid reduction %)

---

## Scenario 3: Multi-Sensor Fusion Methodology for Custom CHF Index
**User Request**: "We want to develop our own CHF risk index combining wearable sensors (HR, SpO2, activity). How do we design a fusion algorithm like HeartLogic?"

**Expected Skill Activation**: `clinical-indices`

**Expected Workflow**:
1. Identify goal: custom multi-sensor CHF index development
2. Cross-reference `shared/multi-sensor-fusion-methodology.md` for design principles
3. Analyze HeartLogic architecture: 6 sensors (S1, S2, S3, HR, Activity, Impedance) → weighted sum → single index
4. Adapt methodology: 3 sensors (HR, SpO2, activity) → derive surrogate features for missing modalities
5. Outline validation requirements (n=200+, 6-month follow-up, readmission outcome)

**Expected Recommendation**:
- **Custom CHF index design (3-sensor version)**:
  - Features:
    - HR variability (SDNN, RMSSD) - surrogate for S1 heart sounds
    - SpO2 baseline + trend (7-day moving average) - surrogate for thoracic impedance
    - Activity duration (<2 hours/day = high risk) - direct input
  - Fusion architecture: Logistic regression with L1 regularization (feature selection)
    - Output: 0-100 scale, trained to predict 30-day readmission risk
  - Weighting: Optimize on training set (n=150), validate on holdout set (n=50)
- **Validation study**:
  - Cohort: n=200 CHF patients (NYHA II-IV), 6-month follow-up
  - Gold standard: Clinician-adjudicated decompensation events
  - Target performance: AUC ≥0.75 (HeartLogic achieves 0.70-0.80 in literature)
- **Regulatory**: Qualify as Class II medical device (FDA 510(k) required if marketed for clinical use)

**Verification**:
- [ ] Multi-sensor fusion methodology referenced
- [ ] Feature engineering explained (surrogate features for missing sensors)
- [ ] Fusion architecture specified (logistic regression, weighting)
- [ ] Validation study design outlined (n, endpoints, target AUC)

---

## Scenario 4: HeartLogic False Positive Management
**User Request**: "We implemented HeartLogic but get too many alerts (50% false positives). How do we reduce alert fatigue without missing true decompensations?"

**Expected Skill Activation**: `clinical-indices`

**Expected Workflow**:
1. Identify problem: high false positive rate (50%, above expected 30-40%)
2. Cross-reference `heartlogic-chf-index.md` for threshold tuning guidance
3. Analyze alert sources: check if all 6 sensors properly calibrated (S1, S2, S3, HR, Activity, Impedance)
4. Propose threshold adjustment: increase alert cutoff from 16 to 20 (trade sensitivity for specificity)
5. Implement secondary confirmation: require 2 consecutive days above threshold before alerting

**Expected Recommendation**:
- **Immediate actions**:
  - Audit sensor quality: Check impedance sensor calibration (most common false positive source)
  - Review patient selection: Exclude NYHA Class I (too stable, low event rate inflates false positives)
- **Threshold tuning**:
  - Increase HeartLogic alert threshold: 16 → 20 (reduces sensitivity 70% → 60%, but improves PPV 50% → 70%)
  - Add confirmation rule: Alert only if HeartLogic >20 for 2 consecutive days (reduces false positives by 40%)
- **Clinical context integration**:
  - Suppress alerts during planned diuretic changes (expected transient HeartLogic elevation)
  - Correlate with patient-reported symptoms (dyspnea, edema) before escalating
- **Expected outcome**: False positive rate 50% → 20-25%, maintaining 60-65% sensitivity

**Verification**:
- [ ] Root cause analysis performed (sensor calibration, patient selection)
- [ ] Threshold adjustment quantified (sensitivity/PPV trade-off)
- [ ] Confirmation rule specified (2 consecutive days)
- [ ] Expected outcome estimated (false positive reduction %)

---

## Scenario 5: NOL vs Self-Report Pain Assessment in Non-Communicative Patients
**User Request**: "We have ICU patients on ventilators who can't self-report pain. Can NOL replace standard pain scales (CPOT, BPS)?"

**Expected Skill Activation**: `clinical-indices`

**Expected Workflow**:
1. Identify clinical context: ICU, mechanically ventilated, non-communicative patients
2. Cross-reference `nol-pain-index.md` for validation in non-communicative populations
3. Compare NOL (objective, continuous) vs CPOT/BPS (subjective, intermittent nurse assessment)
4. Analyze limitations: NOL requires stable hemodynamics (septic shock may confound)
5. Recommend hybrid approach: NOL + behavioral pain scale for validation

**Expected Recommendation**:
- **NOL advantages in ICU non-communicative patients**:
  - Continuous monitoring (vs q4h nurse assessment)
  - Objective (no inter-rater variability, CPOT κ=0.6-0.7)
  - Real-time analgesia titration (detect pain before behavioral signs appear)
- **Limitations**:
  - Hemodynamic instability (vasopressors, arrhythmias) confounds NOL (HR, HRV components unreliable)
  - Movement artifact (agitation, shivering) may trigger false positives
- **Hybrid protocol**:
  - Use NOL as primary pain indicator if hemodynamically stable (MAP >65, no vasopressors)
  - Use CPOT as backup if NOL unreliable (document NOL artifacts)
  - Validate concordance: Compare NOL >25 vs CPOT >2 (expect 80%+ agreement)
- **Expected outcome**: Earlier pain detection (NOL warns 10-15 min before CPOT elevation), 25% reduction in ICU analgesia delays

**Verification**:
- [ ] NOL advantages in non-communicative patients explained
- [ ] Limitations identified (hemodynamic instability, movement)
- [ ] Hybrid protocol specified (NOL + CPOT conditions)
- [ ] Expected outcome quantified (analgesia delay reduction)
