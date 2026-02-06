# DiGA Pathway (Germany): Complete Guide

> **Parent Skill**: [DTx Development](../SKILL.md)  
> **Related**: [FDA PDT Pathway](./fda-pdt-pathway.md), [Clinical Evidence Requirements](./clinical-evidence-requirements.md)

## Overview

The **Digitale Gesundheitsanwendungen (DiGA)** framework is Germany's fast-track regulatory and reimbursement pathway for prescription digital therapeutics. Managed by the Federal Institute for Drugs and Medical Devices (BfArM), it offers two inclusion types: **Provisional** (12-month market access while building confirmatory evidence) and **Permanent** (after completed RCT).

---

## Eligibility Requirements

### 1. Medical Device Status
- Must be **CE-marked** under Medical Device Regulation (MDR)
- Typically **Risk Class I or IIa**
- Digital health application (app-based intervention)

### 2. Prescription Requirement
- Prescribed by **doctor or psychotherapist**
- OR patient submits **proof of diagnosis** directly to insurance

### 3. Data Sovereignty
- Data processing must comply with **GDPR**
- Often requires hosting within **Germany or EU**
- Example: HelloBetter processes data exclusively in Germany

---

## Inclusion Types

### Provisional Inclusion (Fast Track)

**Requirements**:
1. **Pilot Study**: n=30-100 patients demonstrating **plausible justification** of medical benefit
2. **Study Concept**: Detailed plan for confirmatory RCT to be completed within **12 months** (extendable)
3. CE Mark as medical device

**Advantages**:
- **Fast market access** (within months)
- **Immediate reimbursement** while building confirmatory evidence
- Lower initial evidence burden

**Examples**:
- **re.flex** (Knee Osteoarthritis):
  - Pilot: n=61
  - Intervention: Motion sensors + app-based exercises
  - Reimbursement: €784.21 (includes hardware)
- **Endo-App** (Endometriosis):
  - Pilot: n=122
  - Intervention: Multimodal rehabilitation (exercise + education + relaxation)
  - Confirmatory RCT in progress

**Timeline**: 12 months to complete confirmatory study, or risk removal from DiGA directory.

### Permanent Inclusion

**Requirements**:
1. **Completed RCT** proving **"positive healthcare effect"**
2. Evidence must show:
   - **Medical Benefit** (improved health status), OR
   - **Patient-relevant structural/procedural improvements** (e.g., health literacy, treatment adherence)

**Study Design**:
- **Arms**: Intervention Group (DiGA + Standard Care) vs. Control Group (Standard Care alone)
- **Sample Size**: n=200-1200 (based on power analysis)
- **Primary Endpoint**: Validated **Patient-Reported Outcome Measure (PROM)**
- **Duration**: Typically 12-16 weeks

**Examples**:
- **deprexis** (Depression):
  - Multiple RCTs (total n>1000)
  - Primary endpoint: PHQ-9 (depression severity)
  - Reimbursement: €210 / 90 days
- **Kaia Health** (Chronic Back Pain):
  - Rise-uP study: n=1237
  - Primary endpoint: MPI (pain intensity)
  - Reimbursement: €489.39 / 90 days

---

## PICO Framework (Mandatory)

All DiGA applications must define the study using PICO:

| Component | Description | Example (deprexis) |
|-----------|-------------|-------------------|
| **P - Population** | Target patient group | Adults (18-65) with mild-to-moderate depression (PHQ-9 ≥10) |
| **I - Intervention** | DiGA components | 12-week CBT program, 10 modules, chatbot dialogue, homework |
| **C - Comparator** | Control group | Standard Care alone (psychotherapy waitlist) |
| **O - Outcome** | Primary PROM endpoint | Change in PHQ-9 score from baseline to Week 12 |

**Study Design**: Include inclusion/exclusion criteria, randomization method, blinding strategy, follow-up duration.

---

## Patient-Reported Outcome Measures (PROMs)

DiGA studies **must use validated PROMs** as primary endpoints.

### Mental Health

| PROM | Condition | Items | Score Range | MCID |
|------|-----------|-------|-------------|------|
| **PHQ-9** | Depression | 9 | 0-27 | ~5 points |
| **GAD-7** | Anxiety | 7 | 0-21 | ~4 points |
| **Chalder Fatigue Scale** | Chronic Fatigue | 11 | 0-33 | ~3 points |

### Pain

| PROM | Condition | Score Range | MCID |
|------|-----------|-------------|------|
| **VAS (Visual Analogue Scale)** | General Pain | 0-100mm | ~10mm |
| **KOOS (Knee Injury & Osteoarthritis Outcome Score)** | Knee Pain | 0-100 | ~8-10 points |
| **MPI (Multidimensional Pain Inventory)** | Chronic Pain | 0-6 | ~1 point |

### Disease-Specific

| PROM | Condition |
|------|-----------|
| **CAT (COPD Assessment Test)** | COPD |
| **EHP-5 (Endometriosis Health Profile)** | Endometriosis |

**Selection Criteria**:
- Published validation studies
- Translated and culturally adapted for German population
- Permission obtained from scale developers (if proprietary)

---

## Safety & Exclusion Criteria

DiGA applications must define **safety contraindications**:

| DTx Type | Example Exclusions |
|----------|-------------------|
| **Depression Apps** | Active suicidal ideation, psychotic symptoms |
| **Exercise Apps** | Severe cardiovascular disease, recent surgery, physical limitations |
| **Pain Management Apps** | Dependency on opioids (if app includes medication reduction) |

**Data Security**:
- ISO 27001 certification (information security management)
- GDPR Article 32 compliance (technical and organizational measures)
- Regular security audits

---

## Reimbursement Model

### Pricing Structure

**Initial 12 Months**:
- Manufacturer sets the price (free pricing period)
- Automatic coverage by all 73+ million statutory health insurance members

**After 12 Months**:
- Pricing negotiation with **GKV-Spitzenverband** (National Association of Statutory Health Insurance Funds)
- Price based on **comparative effectiveness** vs. standard care
- Dossier submission required (health economics evidence)

### Observed Pricing (2023)

| DiGA | Indication | Price (€ / 90 days) | Inclusion Type | Notes |
|------|------------|---------------------|----------------|-------|
| **deprexis** | Depression | €210 | Permanent | CBT program, multiple RCTs |
| **HelloBetter** | Anxiety, Depression | €240-330 | Permanent | Includes psychologist feedback within 24h |
| **Kaia Health** | Chronic Back Pain | €489.39 | Permanent | Multimodal (exercise + education) |
| **Endo-App** | Endometriosis | €360 | Provisional | Multimodal rehabilitation |
| **re.flex** | Knee Osteoarthritis | €784.21 | Provisional | Includes motion sensor hardware |

**Factors Influencing Price**:
- Hardware inclusion (sensors, devices) → Higher price
- Human-in-the-loop components (therapist feedback) → Higher price
- Comparative effectiveness (larger effect size vs. control) → Higher price
- Disease burden and healthcare cost offset → Higher price

---

## Application Process

### Step 1: Pre-Submission Consultation
- Contact BfArM for initial consultation
- Discuss study design, endpoints, evidence plan
- Clarify CE Mark status and data protection compliance

### Step 2: Submit Application
- Complete **DiGA application form**
- Technical documentation (software specifications, algorithm description)
- Clinical evidence (pilot study + confirmatory plan OR completed RCT)
- Data protection and security documentation
- Usability testing results

### Step 3: BfArM Review
- Assessment of medical benefit / procedural improvement
- Review of data security and interoperability (HL7 FHIR, ISiK/Vesta)
- Decision: Provisional, Permanent, or Rejection
- Timeline: 3-6 months review

### Step 4: DiGA Directory Listing
- Once approved, listed in official **DiGA Directory** (https://diga-api.bfarm.de)
- Accessible to all prescribers and insurers
- Automatic reimbursement activated

### Step 5: Post-Market Surveillance (Provisional)
- If provisional: Complete confirmatory RCT within 12 months
- Submit results to BfArM
- Convert to permanent OR extension OR removal

---

## Case Study: Kaia Health (Permanent DiGA)

**Indication**: Chronic Back Pain

**Clinical Evidence**:
- **Rise-uP Study**: n=1237 patients, RCT
- **Design**: Kaia app + Standard Care vs. Standard Care alone
- **Duration**: 12 weeks
- **Primary Endpoint**: Pain intensity (MPI scale)
- **Results**: Statistically significant pain reduction in Kaia group (p<0.001)

**Therapeutic Content**:
- **Physical Exercise**: Guided video exercises (physiotherapy-based)
- **Education**: Pain science, posture, ergonomics
- **Relaxation**: Mindfulness, breathing techniques
- **AI Movement Coach**: Smartphone camera analyzes posture, provides real-time feedback

**Reimbursement**: €489.39 per 90-day prescription (2023)

**Regulatory Path**:
- CE Mark as Class I medical device (MDR)
- Permanent DiGA inclusion after confirmatory RCT
- Covered by statutory health insurance since [approval date]

---

## Common Pitfalls

| Pitfall | Problem | Solution |
|---------|---------|----------|
| **Using Non-Validated PROMs** | BfArM rejects custom questionnaires | Use only published, validated scales (PHQ-9, GAD-7, KOOS, etc.) |
| **Underpowered Pilot** | n=20 insufficient for provisional inclusion | Plan for ≥30 patients minimum, ideally 50-100 |
| **No Control Group** | Cannot demonstrate "positive healthcare effect" | Always include Standard Care control arm |
| **Data Hosting Outside EU** | GDPR compliance issues | Host data in Germany or EU, document data flows |
| **Missing Confirmatory Plan** | Provisional application incomplete | Submit detailed RCT protocol with sample size calculation |

---

## Cross-References

- **FDA PDT Pathway**: See [./fda-pdt-pathway.md](./fda-pdt-pathway.md) for comparison with USA regulatory approach
- **Clinical Evidence Requirements**: See [./clinical-evidence-requirements.md](./clinical-evidence-requirements.md) for RCT design details
- **PROM Validation**: See [../../shared/clinical-validation-framework.md](../../shared/clinical-validation-framework.md)
- **Regulatory Engagement**: See [../../research-strategy/references/phase3-regulatory-pathway.md](../../research-strategy/references/phase3-regulatory-pathway.md) for general guidance

---

## References

- DiGA Directory: Official BfArM listing (https://diga-api.bfarm.de/de)
- DiGA-Leitfaden: BfArM guidance document (2023)
- Medical Device Regulation (EU) 2017/745 (MDR)
- GDPR: General Data Protection Regulation (EU) 2016/679
