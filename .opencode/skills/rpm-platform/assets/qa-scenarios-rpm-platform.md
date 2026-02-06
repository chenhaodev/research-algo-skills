# QA Scenarios: RPM Platform Skill

## Scenario 1: VitalConnect Architecture for Multi-Patient CHF Monitoring
**User Request**: "We're a cardiology practice planning to monitor 200 CHF patients remotely. How should we design our RPM platform using VitalConnect sensors?"

**Expected Skill Activation**: `rpm-platform`

**Expected Workflow**:
1. Parse requirements: 200 patients, CHF indication, continuous monitoring
2. Cross-reference `vitalconnect-rpm-architecture.md` for system components
3. Design data flow: VitalPatch sensors → Gateway (Bluetooth) → Cloud (AWS) → Dashboard
4. Plan infrastructure: patient onboarding, clinician dashboard, alert routing
5. Integrate with existing EHR (HL7 FHIR for data exchange)

**Expected Recommendation**:
- **System architecture (VitalConnect-based)**:
  - Sensors: VitalPatch RTM (14-day continuous wear, HR/RR/temperature/activity/posture)
  - Gateway: Patient smartphones (BLE → VitalConnect cloud via cellular)
  - Cloud: AWS deployment (HIPAA-compliant, PHI encryption at rest/transit)
  - Dashboard: Clinician portal (Closedloop.ai-style, see `shared/visualization-best-practices.md`)
- **Data flow**:
  - Real-time: VitalPatch → smartphone → cloud (5-min latency)
  - Storage: 90-day rolling window (HIPAA retention requirement)
  - Alerts: Threshold-based (HR >120 bpm, RR >25 bpm) → SMS to on-call nurse
- **Scalability**: 200 patients = 200 VitalPatch sensors × €50/sensor/month = €10K/month recurring
- **Integration**: HL7 FHIR API to Epic/Cerner (ingest vitals to problem list, push alerts to In-Basket)

**Verification**:
- [ ] VitalConnect architecture components specified (sensor, gateway, cloud)
- [ ] Data flow designed (latency, storage, alerts)
- [ ] Scalability estimated (cost per patient per month)
- [ ] EHR integration approach outlined (FHIR API)

---

## Scenario 2: GE EK-Pro Arrhythmia Detection Logic Customization
**User Request**: "We're using GE EK-Pro for arrhythmia detection but getting too many false alarms. How do we tune the detection algorithm?"

**Expected Skill Activation**: `rpm-platform`

**Expected Workflow**:
1. Identify problem: high false positive rate in arrhythmia detection
2. Cross-reference platform documentation for GE EK-Pro algorithm parameters
3. Analyze common false positive sources: motion artifact, ectopic beats misclassified as AFib
4. Propose parameter tuning: adjust R-R interval variability threshold, minimum AFib episode duration
5. Recommend validation protocol: compare tuned algorithm vs manual ECG review (gold standard)

**Expected Recommendation**:
- **GE EK-Pro arrhythmia tuning parameters**:
  - R-R interval variability threshold: Default 120ms → increase to 150ms (reduces ectopic beat false positives)
  - Minimum AFib episode duration: Default 30 seconds → increase to 2 minutes (filters transient artifacts)
  - Lead quality check: Require lead-off detection <5% of epoch (reject noisy segments)
- **Validation protocol**:
  - Retrospective analysis: 100 ECG segments (50 true AFib + 50 false alarms)
  - Tune parameters on 70% training set, validate on 30% holdout set
  - Target metrics: Recall ≥0.90 (miss <10% true AFib), Precision ≥0.80 (PPV, reduce false alarms)
- **Expected outcome**: False positive rate reduction 40% → 15-20%, maintaining 90% sensitivity
- **Clinical workflow**: Add manual review step for borderline cases (R-R variability 150-180ms)

**Verification**:
- [ ] Tuning parameters identified (R-R variability, episode duration)
- [ ] Validation protocol specified (training/holdout sets, target metrics)
- [ ] Expected outcome quantified (false positive reduction %)
- [ ] Clinical workflow integration (manual review step)

---

## Scenario 3: Closedloop-Style Visualization for Clinician Dashboard
**User Request**: "Our RPM dashboard shows raw vitals (HR, RR, SpO2) but clinicians find it overwhelming. How do we design a better visualization?"

**Expected Skill Activation**: `rpm-platform`

**Expected Workflow**:
1. Identify problem: information overload from raw vitals display
2. Cross-reference `shared/visualization-best-practices.md` for Closedloop patterns
3. Select design patterns: baseball cards (patient summary), traffic lights (risk stratification), sparklines (trends)
4. Prioritize clinician workflows: triage (identify high-risk patients) → drill-down (detailed analysis)
5. Design mockup with progressive disclosure (overview → detail → raw data)

**Expected Recommendation**:
- **Dashboard design (Closedloop-inspired)**:
  - **Level 1: Patient list (baseball cards)**
    - Each patient: Name, age, risk score (0-100, color-coded), trend arrow (↑ worsening, ↓ improving, → stable)
    - Sort by: Risk score (descending), recent alerts (last 24h)
    - Example: "John Doe, 72yo, Risk 85 (🔴), ↑ (HR trend increasing)"
  - **Level 2: Patient detail page**
    - Traffic light summary: HR (🟢 normal), RR (🟡 borderline), SpO2 (🔴 low)
    - Sparklines: 7-day trends for each vital (show directionality without clutter)
    - Alert timeline: Recent events with clinical context ("SpO2 <90% for 15 min at 2:30 AM")
  - **Level 3: Raw data (on-demand)**
    - Full waveform display, exportable CSV for manual review
- **Progressive disclosure**: Clinician sees 50 patients → triages 10 high-risk (Level 1) → drills into 2 critical (Level 2) → reviews 1 raw ECG (Level 3)
- **Expected outcome**: Clinician time per patient review 5 min → 2 min (60% reduction)

**Verification**:
- [ ] Visualization patterns specified (baseball cards, traffic lights, sparklines)
- [ ] Progressive disclosure designed (3 levels of detail)
- [ ] Clinician workflow optimized (triage → drill-down)
- [ ] Expected efficiency gain quantified (time reduction %)

---

## Scenario 4: Multi-Sensor Fusion for Fall Detection in Elderly RPM
**User Request**: "We're monitoring elderly patients (age 75+) for fall risk. Should we use accelerometers alone or combine with other sensors?"

**Expected Skill Activation**: `rpm-platform`

**Expected Workflow**:
1. Parse clinical context: fall detection, elderly population (age 75+)
2. Cross-reference `shared/multi-sensor-fusion-methodology.md` for fusion strategies
3. Analyze single-sensor limitations: accelerometer-only systems have 20-30% false positive rate (ADLs misclassified as falls)
4. Propose multi-sensor approach: accelerometer + barometric pressure (altitude change) + HR (post-fall tachycardia)
5. Design fusion algorithm: decision tree or weighted voting

**Expected Recommendation**:
- **Multi-sensor fall detection architecture**:
  - Sensors:
    - Accelerometer (primary): Detect sudden deceleration >2g (fall impact)
    - Barometric pressure (confirmatory): Altitude drop >0.5m within 1 second
    - HR (post-event): Tachycardia (HR >100 bpm) or bradycardia (HR <50 bpm) within 30 seconds of impact
  - Fusion logic (decision tree):
    - IF accelerometer >2g AND barometric drop >0.5m → CONFIRMED FALL
    - IF accelerometer >2g AND HR change >20 bpm → PROBABLE FALL (nurse call)
    - IF accelerometer >2g ALONE → POSSIBLE FALL (patient self-report query via smartphone)
- **Expected performance**: Sensitivity 90% (vs 85% accelerometer-only), False positive rate 10% (vs 25% accelerometer-only)
- **Elderly-specific tuning**: Lower threshold for HR change (20 bpm vs 30 bpm in younger adults) due to blunted HR response
- **Alert routing**: Confirmed falls → immediate caregiver notification + ambulance dispatch, Probable falls → nurse call within 5 min

**Verification**:
- [ ] Multi-sensor fusion rationale explained (reduce false positives)
- [ ] Fusion logic specified (decision tree with confirmatory sensors)
- [ ] Elderly-specific tuning addressed (HR threshold adjustment)
- [ ] Performance improvement quantified (sensitivity, false positive rate)

---

## Scenario 5: HIPAA-Compliant Data Pipeline for VitalConnect RPM
**User Request**: "We're deploying VitalConnect sensors for 500 patients. How do we ensure HIPAA compliance for data storage and transmission?"

**Expected Skill Activation**: `rpm-platform`

**Expected Workflow**:
1. Identify regulatory requirement: HIPAA compliance (PHI protection)
2. Cross-reference `vitalconnect-rpm-architecture.md` for security best practices
3. Design data pipeline: sensor → gateway → cloud → dashboard (encryption at each stage)
4. Implement access controls: role-based permissions (clinician, admin, patient)
5. Plan audit logging: track PHI access, modifications, disclosures

**Expected Recommendation**:
- **HIPAA-compliant data pipeline (VitalConnect)**:
  - **Encryption**:
    - In-transit: TLS 1.3 (sensor → cloud), AES-256 (cloud → dashboard)
    - At-rest: AES-256 (AWS S3 buckets for raw data, RDS for structured data)
  - **Access controls**:
    - Role-based: Clinician (read patient data), Admin (read/write/delete), Patient (read own data only)
    - Multi-factor authentication (MFA) required for all users
    - Session timeout: 15 minutes inactivity (HIPAA minimum)
  - **Audit logging**:
    - Log all PHI access events (who, what, when, from where)
    - Retain logs 6 years (HIPAA requirement)
    - Daily automated review for anomalous access patterns (e.g., clinician accessing 100+ records in 1 hour)
  - **Business Associate Agreement (BAA)**:
    - Sign BAA with VitalConnect (cloud provider = business associate)
    - Ensure AWS BAA covers S3, RDS, Lambda services
- **Data retention**: 7 years (HIPAA medical record retention, state-specific may be longer)
- **Breach response**: Incident response plan (detect breach within 24h, notify patients within 60 days)

**Verification**:
- [ ] Encryption specified (in-transit, at-rest, algorithms)
- [ ] Access controls designed (RBAC, MFA, session timeout)
- [ ] Audit logging plan outlined (retention, anomaly detection)
- [ ] BAA requirements identified (VitalConnect, AWS)
