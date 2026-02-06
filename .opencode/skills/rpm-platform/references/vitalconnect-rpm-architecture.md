# VitalConnect RPM Platform Architecture

> **Parent Skill**: [RPM Platform](../SKILL.md)  
> **Related**: [Alert Threshold Design](./alert-threshold-design.md), [Visualization Best Practices](../../shared/visualization-best-practices.md)

## Platform Components

### 1. VitalPatch (Biosensor Hardware)
- **Form Factor**: Adhesive chest patch, disposable
- **Sensors**: HR, Respiratory Rate, Body Posture, Activity (steps), Skin Temperature
- **Duration**: 7-14 days continuous wear
- **Connectivity**: Bluetooth Low Energy (BLE)

### 2. VistaPoint App (Patient-Side Gateway)
- **Devices**: VistaTablet (bedside), VistaPhone (mobile)
- **Functions**: Receive data from VitalPatch via BLE, upload to cloud, manual vital entry (SpO2, BP, weight from third-party Bluetooth devices)

### 3. VitalCloud (Server Infrastructure)
- **Data Storage**: Secure HIPAA-compliant cloud
- **Processing**: Cloud-based arrhythmia detection algorithms
- **Transmission**: Encrypted data flow to clinician dashboard

### 4. VistaCenter (Clinician Dashboard)
- **Access**: Web-based portal
- **Features**: Patient list, vital sign trends, alert management, ECG review, report generation
- **User Roles**: Administrator, Clinical User, View-Only

---

## Data Flow Architecture

```
VitalPatch Biosensor
  ↓ (BLE)
VistaPoint App (VistaTablet/VistaPhone)
  ↓ (WiFi/Cellular)
VitalCloud (Secure Server)
  ↓ (HTTPS)
VistaCenter Dashboard (Web Browser)
```

**Key Advantage**: Multi-hop architecture allows patient mobility (patch → phone → cloud) vs. direct device-to-cloud dependency.

---

## Alert System Design

### Vital Sign Thresholds

**Configurable Parameters**:
- Upper/lower limits for HR, RR, etc.
- **Averaging Duration**: 15 seconds to 30 minutes (prevents false alarms from transient spikes)
- **Custom Logic**: Combine up to 3 vital signs with AND/OR operators

**Example**: Alert if (HR >120 bpm AND RR >25 brpm) sustained for 5 minutes.

### Arrhythmia Detection

**Cloud-Based Algorithms**:
- AFib, Tachycardia (>170 BPM), Pause (>15 sec), AV Block
- **Configurable**: Rate thresholds, duration, notification hours (24/7 vs. business hours only)

### NEWS2 Integration

**Early Warning Score**: 7-parameter system (0-20) for clinical deterioration detection
- RR, SpO2, Systolic BP, PR, Consciousness, Temperature, Supplemental O2
- **Manual Calculation**: Clinician-initiated, not auto-triggered

---

## Security & Compliance

- **Multi-Factor Authentication (MFA)**: SMS-based
- **Single Sign-On (SSO)**: Enterprise integration
- **Role-Based Access Control**: Limit data visibility by role
- **HIPAA Compliance**: VitalCloud designed as secure environment

---

## Cross-References

- **Alert Threshold Design**: See [./alert-threshold-design.md](./alert-threshold-design.md)
- **Device Selection**: See [../../device-selection/SKILL.md](../../device-selection/SKILL.md)
- **Visualization**: See [../../shared/visualization-best-practices.md](../../shared/visualization-best-practices.md)

---

## References

- VistaCenter 3.2 Instructions for Use (VitalConnect, 2021)
