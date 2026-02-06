# Device Comparison Matrix

> **Referenced By**: [Device Selection](../device-selection/SKILL.md), [RPM Platform](../rpm-platform/SKILL.md)

## Wearable Sensors

| Device | Form Factor | Key Sensors | Sampling Rate | Battery Life | Water Resistance | Validation Highlights |
|--------|-------------|-------------|---------------|--------------|------------------|----------------------|
| **Empatica E4 (2014)** | Wrist | PPG, EDA, Accel, Temp | PPG: 64Hz, Accel: 32Hz, EDA: 4Hz | ~48h | Not certified | **Legacy**: Not suitable for running/activity |
| **EmbracePlus (2021)** | Wrist | PPG, EDA, IMU, Temp, SpO2 | PPG: 64Hz, IMU: 64Hz, EDA: 4Hz | 2+ days (no SpO2), 1+ day (SpO2) | IP67 | **PR**: RMSE <3bpm rest, <5bpm motion; **SpO2**: RMSE <3%; **Sleep**: F-score 90% vs PSG |
| **LifeQ Platform** | Wrist | PPG, Accel | 64Hz+ | Platform-dependent | Varies | **AFib**: Recall 0.9, Spec 0.98; **VO2max**: MAPE 5-16%; **Sleep**: vs PSG |
| **Oura Ring** | Finger | PPG, Temp, Accel | Varies | 4-7 days | Water resistant | Sleep, HRV, recovery metrics |
| **VitalPatch** | Chest Patch | ECG, Accel, Temp | ECG-quality | 7-14 days | Yes | Continuous cardiac monitoring, RPM platform |

## Selection Quick Guide

**Continuous Cardiac (ECG-quality)**: VitalPatch  
**Multi-Biomarker Platform**: LifeQ, EmbracePlus  
**Sleep & Recovery**: Oura Ring, EmbracePlus  
**Motion-Validated Activity**: EmbracePlus, LifeQ  
**Long Battery (7+ days)**: VitalPatch, Oura Ring  
**SpO2 Monitoring**: EmbracePlus (Profile B)

---

## References

See individual device references in [device-selection/references/](../device-selection/references/)
