# Case Study: Pear Therapeutics reSET

> **Parent Skill**: [DTx Development](../SKILL.md)  
> **Related**: [FDA PDT Pathway](./fda-pdt-pathway.md), [Clinical Evidence Requirements](./clinical-evidence-requirements.md)

## Overview

Pear Therapeutics' **reSET** was the **first prescription digital therapeutic** to receive FDA market authorization (De Novo pathway, 2017). This case study documents the clinical evidence, regulatory strategy, engagement mechanisms, and commercialization approach that established the PDT category.

---

## Product Specifications

**Indication**: Substance Use Disorder (SUD)  
**Regulatory Class**: Class II Medical Device (De Novo DEN160018)  
**Prescription Status**: Prescription-only  
**Platform**: Mobile app (iOS, Android)  
**Duration**: 90-day program (12 weeks active + follow-up)

---

## Clinical Evidence: Pivotal Study

### Study Design

**Title**: Randomized Controlled Trial of reSET for SUD  
**Sample Size**: n=399 patients  
**Duration**: 12 weeks treatment + follow-up  
**Design**: Multi-site, randomized, controlled  
**Sites**: Multiple outpatient SUD treatment centers (USA)

**Randomization**:
- **Intervention Group**: Reduced face-to-face therapy + reSET app
- **Control Group**: Standard "best-of-breed" face-to-face therapy (higher frequency than intervention group)

### Primary Endpoint

**Abstinence during weeks 9-12**, confirmed by:
- Urine drug screening: 2 times per week
- Objective biochemical verification (gold standard)

### Results

| Outcome | reSET Group | Control Group | Statistical Significance |
|---------|-------------|---------------|--------------------------|
| **Abstinence (Weeks 9-12)** | 40.3% | 17.6% | p <0.001 |
| **Retention in Treatment** | Higher | Lower | p <0.05 |
| **Module Completion** | Dose-response relationship observed | N/A | Linear correlation with abstinence |

**Key Finding**: **40.3% abstinence** rate in reSET group vs. **17.6%** in control group represents a **>2x improvement** in primary endpoint.

**Dose-Response Analysis**:
- Linear relationship between number of CBT modules completed and abstinence rate
- Patients completing ≥8 modules had significantly higher abstinence vs. <4 modules

---

## Therapeutic Intervention Components

### 1. Cognitive Behavioral Therapy (CBT) Modules

**Content**:
- Standardized CBT lessons based on **Community Reinforcement Approach (CRA)**
- Developed at Dartmouth Medical School (academic pedigree)
- Digitized version of evidence-based face-to-face therapy

**Structure**:
- Progressive curriculum (12 weeks)
- Interactive lessons with quizzes and exercises
- Fluency training: Drills to reinforce learning

### 2. Contingency Management (Reward System)

**Mechanism**:
- Rewards for **negative urine screens** (biochemically confirmed abstinence)
- Rewards for **module completion** (engagement reinforcement)
- Virtual or financial incentives (study-specific implementation)

**Evidence**: Contingency management is established as effective behavioral intervention in SUD treatment (meta-analyses support).

### 3. Self-Monitoring Tools

**Features**:
- Craving tracker: Log intensity, triggers, coping strategies
- Trigger identification: Recognize high-risk situations
- Coping skills library: Access techniques in real-time during cravings

### 4. Clinician Dashboard ("Clinician Insight")

**Provider Portal**:
- View patient progress: Abstinence status (from urine screens), module completion rate
- Identify at-risk patients: Low engagement, positive screens
- Inform in-person sessions: Data-driven therapy adjustments

**Workflow Integration**: Designed to complement, not replace, face-to-face therapy.

---

## Regulatory Strategy

### FDA Pathway: De Novo

**Why De Novo** (vs. 510(k)):
- No **predicate device** existed (first prescription digital therapeutic)
- Novel mechanism: Software-as-therapy for SUD
- Class II risk profile (moderate risk)

**Process**:
1. **Pre-Submission (Q-Sub)**: Early FDA engagement to discuss:
   - Classification (device vs. drug)
   - Clinical evidence requirements
   - Special controls needed
2. **De Novo Submission**: Included:
   - Clinical data from pivotal RCT (n=399)
   - Software description: Algorithm logic, user interface, data flow
   - Cybersecurity and data privacy documentation
   - Proposed labeling (indications for use, contraindications)
3. **FDA Review**: 120 days + questions/responses
4. **Authorization**: De Novo granted (2017), establishing new device classification for PDTs

**Outcome**: reSET authorization created a **regulatory pathway** for subsequent PDTs (now 510(k) predicates exist).

### reSET-O: Breakthrough Designation

**Product**: reSET-O (Opioid Use Disorder)  
**Milestone**: **First PDT to receive Breakthrough Designation** (December 2017)

**Breakthrough Criteria Met**:
1. Treats **serious condition** (Opioid Use Disorder, public health crisis)
2. **Preliminary evidence** of substantial improvement over existing therapies
3. Novel mechanism: Digital adjunct to buprenorphine or methadone

**Benefits**:
- **Priority review** by FDA
- More frequent FDA interaction during development
- Dedicated FDA resources for guidance

**Authorization**: reSET-O authorized January 2019 (after reSET in 2017).

---

## Commercialization Strategy

### Prescription Model

**Workflow**:
1. **Clinician Prescribes**: Provider writes prescription for reSET (90-day program)
2. **Fulfillment**: Patient receives access code via pharmacy or direct from Pear
3. **Patient Activation**: Download app, enter code, begin program
4. **Monitoring**: Clinician views dashboard throughout treatment
5. **Reimbursement**: Insurance covers cost via claims submission

**Payor Coverage**:
- Marketed to commercial payers, Medicaid, Medicare
- Requires establishing product codes and coverage policies
- Reimbursement model similar to pharmaceutical drugs

### Partnership Strategy: Pharma Collaboration

**Partnership**: Pear Therapeutics + Sandoz (Novartis)

**Rationale**:
- **Sandoz Strengths**: Established sales force, reimbursement infrastructure, market access expertise
- **Pear Strengths**: R&D, clinical development, software platform

**Division of Labor**:
- Pear: Retains R&D control, platform development, clinical trials
- Sandoz: Commercialization, sales, payer negotiations, distribution

**Advantage**: Accelerates market access by leveraging pharma's existing infrastructure rather than building de novo.

---

## Real-World Evidence (RWE) Generation

**Platform Feature**: "Real-world data" collection built into Pear Connect platform architecture.

**Data Collected**:
- App usage metrics: Session frequency, duration, module completion
- Clinical outcomes: Abstinence rates, relapse events (where urine screening continues)
- Patient demographics and comorbidities

**Purpose**:
- **Health Outcomes Research**: Support pricing and payor coverage
- **Algorithm Refinement**: Improve engagement and efficacy over time
- **Regulatory Support**: Post-market surveillance, label expansion

---

## Key Lessons for DTx Developers

### 1. "Software as Drug" Rigor

**Approach**: Validate software through rigorous RCTs and FDA pathways (vs. "wellness" app route) to secure reimbursement.

**Implication**: Higher development cost and timeline, but establishes medical device status and insurance coverage.

### 2. Adjunctive Therapy Model

**Design**: reSET works **alongside** standard care (face-to-face therapy), not as replacement.

**Benefits**:
- Easier clinician adoption (complements vs. competes)
- Reduces regulatory risk (lower bar vs. "monotherapy" claim)
- Addresses access-to-care gaps (extends therapy between sessions)

### 3. Platform Strategy

**Pear Connect**: Scalable infrastructure handling:
- Prescription fulfillment
- Data security (HIPAA compliance)
- RWE collection
- Multi-indication support (reSET, reSET-O, pipeline assets)

**Advantage**: Build once, deploy across multiple disease indications (SUD, OUD, insomnia, schizophrenia pipeline).

### 4. Established Behavioral Science Foundation

**Credibility**: CBT and Community Reinforcement Approach have decades of clinical evidence.

**Implication**: Digitizing proven therapies is lower risk than inventing novel therapeutic mechanisms.

---

## Comparison: reSET vs. reSET-O

| Feature | reSET (SUD) | reSET-O (OUD) |
|---------|-------------|---------------|
| **Indication** | Substance Use Disorder (alcohol, cannabis, cocaine, stimulants) | Opioid Use Disorder |
| **Adjunct To** | Outpatient therapy | Buprenorphine or methadone maintenance |
| **Breakthrough Designation** | No | Yes (Dec 2017) |
| **FDA Authorization** | 2017 (De Novo) | 2019 (De Novo) |
| **Pivotal Study** | n=399, 40.3% vs. 17.6% abstinence | 3 RCTs, >450 patients |
| **Core Mechanism** | CBT + Contingency Management | CBT + Medication adherence support |

---

## Pipeline Expansion

**Other Pear Products** (as of 2020):
- **Pear-003**: Insomnia (9 RCTs)
- **Pear-004**: Schizophrenia (8 studies)
- **Pear-005**: [Not disclosed]

**Strategy**: Leverage reSET platform infrastructure for new indications, reducing per-product development cost.

---

## Cross-References

- **FDA PDT Pathway**: See [./fda-pdt-pathway.md](./fda-pdt-pathway.md) for De Novo and Breakthrough Designation details
- **Clinical Evidence Requirements**: See [./clinical-evidence-requirements.md](./clinical-evidence-requirements.md) for RCT design
- **Regulatory Engagement**: See [../../research-strategy/references/phase3-regulatory-pathway.md](../../research-strategy/references/phase3-regulatory-pathway.md)

---

## References

- Pear Therapeutics Case Study (June 2019)
- FDA De Novo Summary (DEN160018): reSET
- Pear Therapeutics Presentation (February 2020)
- Campbell et al., "A Digital Therapeutic for SUD": Clinical trial publication
