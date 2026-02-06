# Visualization Best Practices for Health Indices

> **Referenced By**: [RPM Platform](../rpm-platform/SKILL.md), [Clinical Indices](../clinical-indices/SKILL.md)  
> **Source**: Closedloop visualization patterns (2021)

## Core Principles

### 1. Baseball Card Summaries
**Concept**: High-level risk preview embedded in workflow (not separate portal)  
**Example**: Single card showing patient risk score, percentile, and top 3 risk factors  
**Benefit**: Rapid scanning without context switching

### 2. Traffic Light Color Coding
**Semantic Colors**:
- **Red**: High risk / Risk-increasing factors
- **Yellow**: Elevated risk
- **Green**: Normal / Risk-decreasing factors

**Purpose**: Enable rapid visual triage across patient list

### 3. Progressive Disclosure
**Levels**:
- **Level 1 (Preview)**: Baseball card summary
- **Level 2 (Detail)**: Full 10-15 page drill-down report

**Benefit**: Prevent information overload, allow depth when needed

### 4. Factor Attribution (Explainability)
**Components**:
- List specific variables contributing to score
- **Directional Indicators**: Red bars (risk ↑), Green bars (risk ↓)
- **Raw Data Values**: Show actual measurements (e.g., "Inpatient Days: 0 → 7")

**Purpose**: Build trust through transparency, enable clinical reasoning

### 5. Temporal Trends
**Always Include**: Risk trend line showing changes over time  
**Link Spikes**: Connect risk increases to specific contributing factors at that timepoint  
**Benefit**: Understand narrative of patient's health trajectory

---

## Multi-Biomarker Dashboard Design

**For Platforms (HeartLogic, LifeQ, RPM systems)**:

1. **Combine Multiple Specific Scores**: Individual cards for each risk/biomarker (AFib, Sleep, HF Risk)
2. **Percentile Context**: Show both raw multiplier (e.g., "8.6X risk") and percentile (e.g., "98th percentile")
3. **Intervention Mapping**: Pair risk with specific actionable intervention (e.g., "Avoidable ED" → "Establish after-hours care plan")

---

## Implementation Checklist

- [ ] Embed visualizations in existing EHR/workflow (not standalone portal)
- [ ] Use semantic colors consistently (Red/Yellow/Green)
- [ ] Provide explainability (which factors drove the score?)
- [ ] Show temporal trends (not just current snapshot)
- [ ] Link risks to actions (what should clinician do?)
- [ ] Include raw data for verification (build trust)

---

## References

- Closedloop Index Visualization Manual (2021)
- [Clinical Indices](../clinical-indices/SKILL.md) - HeartLogic contributing trends example
- [RPM Platform](../rpm-platform/SKILL.md) - Dashboard design section
