# QA Scenarios: DTx Development Skill

## Scenario 1: DiGA Pathway Eligibility Assessment
**User Request**: "We developed a CBT-based app for insomnia. Can we apply for DiGA reimbursement in Germany?"

**Expected Skill Activation**: `dtx-development`

**Expected Workflow**:
1. Parse DTx characteristics: CBT-based, insomnia indication, app format
2. Cross-reference `diga-pathway-germany.md` for eligibility criteria
3. Check: (1) Medical purpose (insomnia treatment), (2) CE-marked, (3) Evidence requirement (RCT)
4. Query insomnia as reimbursable indication (DiGA directory list)
5. Outline required clinical evidence: RCT showing symptom improvement vs control

**Expected Recommendation**:
- **Eligible**: Insomnia is a recognized DiGA indication (ICD-10: G47.0)
- Requirements: (1) CE mark as Class I/IIa medical device, (2) RCT evidence (n≥100, primary endpoint: Insomnia Severity Index improvement)
- Timeline: 12 months (3 months trial + 6 months BfArM review + 3 months reimbursement negotiation)
- Reimbursement range: €200-€400 (based on similar mental health DiGAs)
- Next steps: Initiate CE marking process, design RCT protocol with German sleep medicine centers

**Verification**:
- [ ] DiGA eligibility criteria confirmed (medical purpose, CE mark, evidence)
- [ ] Insomnia indication verified as reimbursable
- [ ] RCT design parameters specified (sample size, endpoint)
- [ ] Timeline and reimbursement estimate provided

---

## Scenario 2: FDA vs DiGA Pathway Selection
**User Request**: "We're a startup with a diabetes prevention DTx. Should we pursue FDA clearance or DiGA first?"

**Expected Skill Activation**: `dtx-development`

**Expected Workflow**:
1. Identify dual-market ambition: US (FDA) vs Germany (DiGA)
2. Cross-reference `shared/dtx-regulatory-pathways.md` for pathway comparison
3. Analyze factors: time-to-market, evidence requirements, reimbursement certainty
4. Assess diabetes prevention as indication: FDA 510(k) (predicate exists) vs DiGA (ICD-10: E11)
5. Recommend pathway based on startup resources (budget, timeline, market priority)

**Expected Recommendation**:
- **Recommend DiGA first** (12 months vs 18-24 months for FDA)
  - Rationale: Faster time-to-market, lower upfront trial costs (DiGA accepts n=100 RCT; FDA often requires n=300+)
  - Reimbursement: DiGA guarantees reimbursement (€400-€600 range for chronic disease prevention); FDA clearance ≠ US insurance coverage
  - Leverage: DiGA approval + German RCT data strengthens FDA 510(k) submission (de novo pathway if no predicate)
- **Alternative**: Parallel pathways if well-funded (>$2M runway)

**Verification**:
- [ ] Both pathways explained (FDA vs DiGA)
- [ ] Time and cost trade-offs quantified
- [ ] Market-specific factors addressed (reimbursement certainty)
- [ ] Startup resource constraints considered

---

## Scenario 3: Pear reSET Case Study Application
**User Request**: "How did Pear Therapeutics' reSET get approved? Can we replicate their approach for our alcohol use disorder DTx?"

**Expected Skill Activation**: `dtx-development`

**Expected Workflow**:
1. Query `example-pear-reset.md` for reSET approval details
2. Extract key elements: (1) FDA De Novo pathway, (2) RCT design (n=399), (3) Primary endpoint (abstinence rate), (4) Reimbursement via CPT code
3. Compare indication: reSET (substance use disorder) vs user's AUD (overlapping but distinct)
4. Identify replicable elements vs non-replicable (first-of-kind De Novo vs now-established 510(k) predicates)
5. Adapt strategy: 510(k) with reSET as predicate device

**Expected Recommendation**:
- **Replicable elements**:
  - RCT design: n=300-400, 12-week intervention, primary endpoint (continuous abstinence weeks 9-12)
  - FDA pathway: Now use 510(k) with reSET as predicate (faster than De Novo)
  - Reimbursement: Apply for CPT code (Pear established precedent: CPT 0704T for DTx)
- **Study design**: 2-arm RCT (DTx + treatment-as-usual vs TAU alone), powered for 20% absolute difference in abstinence (reSET achieved 40.3% vs 17.6%)
- **Timeline**: 24 months (12-month trial + 6-month FDA review + 6-month CPT code application)
- **Budget**: $1.5M (trial) + $150K (regulatory) = $1.65M total

**Verification**:
- [ ] reSET case study details accurately cited (n=399, 40.3% vs 17.6%)
- [ ] Pathway adapted to current landscape (510(k) vs De Novo)
- [ ] AUD-specific considerations addressed (indication overlap)
- [ ] Budget and timeline estimates provided

---

## Scenario 4: Post-Market Evidence Plan (DiGA)
**User Request**: "Our COPD DTx just got provisional DiGA approval. What evidence do we need to collect in the next 12 months to convert to permanent approval?"

**Expected Skill Activation**: `dtx-development`

**Expected Workflow**:
1. Identify status: provisional DiGA approval (year 1 of 2-year probation)
2. Cross-reference `diga-pathway-germany.md` for post-market requirements
3. Define permanent approval criteria: positive care effects (PCE) evidence from real-world use
4. Design post-market study: observational cohort (n≥200), 6-month follow-up, primary endpoint (COPD Assessment Test score improvement)
5. Outline data collection infrastructure (in-app analytics, patient-reported outcomes)

**Expected Recommendation**:
- **Post-market study design**:
  - Cohort: n=200 DiGA users (recruited via pulmonologist referrals)
  - Duration: 6 months active use + 3-month follow-up
  - Primary endpoint: CAT score improvement ≥2 points (clinically meaningful)
  - Secondary: exacerbation rate, medication adherence, quality of life (EQ-5D)
- **Data infrastructure**: Integrate FHIR-compliant data export for BfArM submission
- **Timeline**: 6 months enrollment + 6 months follow-up + 3 months analysis = 15 months (within 2-year window)
- **Budget**: €150K (patient incentives, data platform, analysis)
- **Risk mitigation**: If PCE not demonstrated, prepare enhanced intervention (e.g., add telemedicine coaching)

**Verification**:
- [ ] Provisional vs permanent DiGA status explained
- [ ] Post-market study design specified (n, duration, endpoints)
- [ ] Data collection requirements outlined (FHIR compliance)
- [ ] Risk mitigation strategy provided

---

## Scenario 5: Reimbursement Negotiation Strategy
**User Request**: "BfArM approved our migraine DTx. How do we negotiate the best reimbursement price with GKV-SV?"

**Expected Skill Activation**: `dtx-development`

**Expected Workflow**:
1. Identify negotiation stage: post-BfArM approval, pre-GKV-SV price agreement
2. Cross-reference `diga-pathway-germany.md` for pricing factors
3. Analyze comparators: (1) Existing migraine DiGAs (€200-€400), (2) Pharmaceutical comparators (triptans €50/month)
4. Build value dossier: (1) RCT results (migraine day reduction), (2) Cost-offset (ER visits avoided), (3) Quality of life gains
5. Set target range with fallback positions

**Expected Recommendation**:
- **Target price**: €500 (3-month treatment course)
  - Justification: 6-day migraine reduction (from RCT) × €80/migraine day (productivity loss) = €480 value
  - Comparator: Triptan therapy (€150/3 months) + ER visits (2 visits/year × €300) = €600 total
  - Net savings: €100 (€600 - €500) per patient per quarter
- **Negotiation tactics**:
  - Anchor high (€700), expect 20-30% reduction
  - Emphasize cost-offset data (ER visits, sick days)
  - Offer real-world evidence commitment (post-market PCE study already ongoing)
- **Fallback positions**: €400 (acceptable), €300 (minimum viable, renegotiate after 2 years)
- **Timeline**: 3-6 months negotiation window

**Verification**:
- [ ] Reimbursement range justified with health economics data
- [ ] Comparators identified (existing DiGAs + pharmaceuticals)
- [ ] Negotiation tactics specified (anchoring, value dossier)
- [ ] Fallback positions defined
