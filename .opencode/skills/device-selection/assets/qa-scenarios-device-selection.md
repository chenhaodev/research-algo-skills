# QA Scenarios: Device Selection Skill

## Scenario 1: Free-Living HR Monitoring Device Selection
**User Request**: "I need to select a wearable sensor for a 6-month free-living study tracking heart rate in 200 elderly participants (age 65-80). What device should I use?"

**Expected Skill Activation**: `device-selection`

**Expected Workflow**:
1. Identify study context: free-living, 6 months, elderly population
2. Cross-reference `wearable-sensors.md` for device candidates with extended battery life
3. Evaluate Empatica EmbracePlus (7-day battery) vs LifeQ (24-hour battery)
4. Check validation metrics: PR RMSE <3 bpm requirement
5. Recommend device with logistical considerations (charging frequency)

**Expected Recommendation**:
- Primary: **Empatica EmbracePlus** (7-day battery reduces compliance burden in elderly)
- Alternative: LifeQ (if budget constrained, but requires daily charging protocol)
- Validation: Verify PR RMSE <3 bpm in age-matched population (65+ years)
- Logistics: Plan charging stations at weekly check-ins

**Verification**:
- [ ] Device recommendation matches study duration requirements
- [ ] Validation metrics cited from `wearable-sensors.md`
- [ ] Age-specific considerations addressed (elderly compliance)
- [ ] Battery life vs study duration trade-offs explained

---

## Scenario 2: Multi-Biomarker Platform Selection for Sleep Study
**User Request**: "We're designing a sleep apnea detection study. Which platform can capture SpO2, respiratory rate, and heart rate simultaneously?"

**Expected Skill Activation**: `device-selection`

**Expected Workflow**:
1. Parse biomarker requirements: SpO2, RR, HR (multi-modal)
2. Query `platform-biomarkers.md` for multi-sensor platforms
3. Filter platforms with SpO2 capability (subset of wearables)
4. Cross-reference validation: SpO2 RMSE <3%, RR MAE <2 bpm, HR RMSE <3 bpm
5. Evaluate sleep-specific constraints (comfort, sensor placement)

**Expected Recommendation**:
- **LifeQ** platform (supports SpO2 + RR + HR + PPG-derived features)
- Validation: SpO2 RMSE <3%, RR MAE <2 bpm (from `platform-biomarkers.md`)
- Design consideration: Finger-worn sensor may disrupt sleep; recommend wrist-based backup (Empatica EmbracePlus for HR only)
- Alternative: Multi-device setup (Empatica HR + dedicated pulse oximeter)

**Verification**:
- [ ] All 3 biomarkers (SpO2, RR, HR) addressed
- [ ] Platform capabilities matched to biomarker list
- [ ] Sleep-specific constraints mentioned (comfort, placement)
- [ ] Validation thresholds cited for each biomarker

---

## Scenario 3: AFib Detection in High-Risk Population
**User Request**: "Our clinic wants to screen 500 post-stroke patients (age 70+) for atrial fibrillation. What's the best wearable device?"

**Expected Skill Activation**: `device-selection`

**Expected Workflow**:
1. Identify clinical context: AFib detection, high-risk population (post-stroke)
2. Reference `sensor-evaluation-criteria.md` for AFib validation requirements
3. Check recall (sensitivity) ≥0.90 and specificity ≥0.98 thresholds
4. Cross-reference `wearable-sensors.md` for AFib-validated devices
5. Consider regulatory approval (FDA clearance for AFib detection)

**Expected Recommendation**:
- **Empatica EmbracePlus** (AFib Recall 0.90, Specificity 0.98 - meets criteria)
- Regulatory: Verify FDA 510(k) clearance for AFib detection in age 70+ population
- Clinical workflow: Integrate with cardiology referral pathway for positive detections
- Alternative: Apple Watch Series 8+ (if participants already own devices, but validate age-specific performance)

**Verification**:
- [ ] AFib-specific validation metrics cited (recall ≥0.90, specificity ≥0.98)
- [ ] Regulatory approval status mentioned (FDA clearance)
- [ ] Age-specific validation confirmed (70+ years)
- [ ] Clinical integration considerations (referral pathway)

---

## Scenario 4: Cost-Performance Trade-off Analysis
**User Request**: "Budget constraints: Empatica EmbracePlus costs $500/device, but LifeQ costs $200/device. For a 100-participant stress study, which is better value?"

**Expected Skill Activation**: `device-selection`

**Expected Workflow**:
1. Extract cost information: EmbracePlus ($500) vs LifeQ ($200)
2. Query `shared/device-comparison-matrix.md` for side-by-side specs
3. Analyze stress-relevant biomarkers: HR, HRV, EDA (Empatica has EDA, LifeQ lacks)
4. Calculate total cost: 100 devices × price + infrastructure (data storage, software)
5. Perform cost-benefit analysis: EDA value vs $30k price difference

**Expected Recommendation**:
- **If EDA is critical**: Empatica EmbracePlus ($50k total, but EDA enables autonomic stress detection)
- **If budget-constrained**: LifeQ ($20k total, HR/HRV sufficient for basic stress metrics)
- Trade-off: EDA provides ~30% more stress detection sensitivity (per literature), worth $30k premium if primary outcome depends on it
- Alternative: Hybrid approach (50 Empatica for validation subset + 50 LifeQ for scale)

**Verification**:
- [ ] Total cost calculated correctly (100 × unit price)
- [ ] Biomarker capabilities compared (EDA presence/absence)
- [ ] Cost-benefit trade-off quantified (sensitivity gain vs price delta)
- [ ] Hybrid approach offered as compromise

---

## Scenario 5: Sensor Validation Gap Identification
**User Request**: "I want to use a consumer Fitbit for a clinical trial measuring resting heart rate in diabetic patients. Is this acceptable?"

**Expected Skill Activation**: `device-selection`

**Expected Workflow**:
1. Identify device category: consumer wearable (Fitbit) vs research-grade
2. Check `sensor-evaluation-criteria.md` for validation requirements
3. Query validation status: Fitbit validation in diabetic population (likely missing)
4. Cross-reference regulatory requirements: FDA clearance for clinical use (Fitbit lacks)
5. Flag validation gap: consumer device not validated in target population

**Expected Recommendation**:
- **Not recommended**: Fitbit validation data in diabetic population is sparse/absent
- Risk: Diabetes-related peripheral vascular changes may affect PPG accuracy (unvalidated)
- Regulatory: Consumer devices lack FDA clearance for clinical trial endpoints
- Alternative: Use research-grade device with diabetes-specific validation (e.g., Empatica E4/EmbracePlus with custom validation study)
- Compromise: Run pilot validation (n=20) comparing Fitbit vs gold-standard ECG in diabetic cohort before full trial

**Verification**:
- [ ] Validation gap explicitly identified (diabetic population)
- [ ] Regulatory concerns flagged (FDA clearance)
- [ ] Physiological mechanism explained (peripheral vascular changes)
- [ ] Pilot validation study suggested as compromise
