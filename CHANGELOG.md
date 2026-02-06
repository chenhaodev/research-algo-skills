# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-02

### Added
- ✨ Initial release of Research & Algorithm Development Skills
- 📋 3 main skill modules:
  - **research-strategy**: Strategic framework for digital measure development (SOP-R-1)
  - **algo-development**: Algorithm design and development planning (SOP-R-3 Predictive Biomarkers & Evidence Checklist)
  - **review-validation**: Literature review and validation methodologies (SOP-R-3 Feasibility Analysis, Systematic Review, SOP-R-4)
- 🔗 Shared resources library:
  - PRISMA 2020 checklist (27 items)
  - GRADE framework (evidence assessment)
  - PICOS question templates
  - FDA CDS criteria
  - Clinical validation framework
  - Data quality checklist
  - Reference databases guide
  - Statistical methods reference
- 📝 Comprehensive documentation:
  - Installation guide
  - Usage examples
  - QA test scenarios for each skill
  - Real-world case studies (Nocturnal Scratch, Predictive Biomarkers, QT Validation)
- 🎯 Qwen-Pro optimization:
  - Structured tables for key information
  - Step-by-step numbered procedures
  - Progressive disclosure (quick ref → detailed → specialized)
  - Self-contained sections with explicit formatting
- 🔧 Repository infrastructure:
  - Apache 2.0 license
  - Contributing guidelines
  - Issue and PR templates
  - Changelog

### Examples Included
- Nocturnal Scratch measure development (COA design)
- Predictive biomarker algorithm selection
- QT interval validation protocol (Physionet database)

### Quality Metrics
- 3 skills covering 6 original SOPs
- 8 shared resource documents
- 12+ reference files with detailed methodologies
- 3 QA scenario files for testing
- 100% internal link coverage

---

## [1.1.0] - 2026-02-06

### Added
- ✨ 4 new domain-specific skills for digital health workflows:
  - **device-selection**: Wearable sensor and platform selection with validation criteria (Empatica E4/EmbracePlus, LifeQ platform examples)
  - **dtx-development**: Digital therapeutics regulatory pathways (DiGA Germany, FDA PDT) with Pear reSET case study (n=399 RCT, 40.3% vs 17.6% abstinence)
  - **clinical-indices**: Multi-sensor fusion and composite biomarker methodologies (HeartLogic CHF: 70% sensitivity, 34-day early warning; NOL Pain: AUC 0.93)
  - **rpm-platform**: Remote patient monitoring architecture and integration (VitalConnect, GE EK-Pro, Closedloop visualization patterns)

- 📚 12 new reference files:
  - Device selection: `wearable-sensors.md`, `platform-biomarkers.md`, `sensor-evaluation-criteria.md`
  - DTx development: `diga-pathway-germany.md`, `example-pear-reset.md`
  - Clinical indices: `heartlogic-chf-index.md`, `nol-pain-index.md`
  - RPM platform: `vitalconnect-rpm-architecture.md`
  - 4 additional supporting references

- 🔗 4 shared resources for cross-skill integration:
  - `device-comparison-matrix.md`: Quick reference for sensor specifications
  - `dtx-regulatory-pathways.md`: DiGA vs FDA pathway comparison (timeline, evidence, reimbursement)
  - `visualization-best-practices.md`: Closedloop patterns (baseball cards, traffic lights, progressive disclosure)
  - `multi-sensor-fusion-methodology.md`: HeartLogic/NOL multi-sensor approaches

- 🧪 20 QA scenarios demonstrating real-world applications:
  - 5 scenarios per new skill (device-selection, dtx-development, clinical-indices, rpm-platform)
  - Each scenario includes: user request, expected workflow (5 steps), expected recommendation, verification checklist
  - Coverage: clinical use cases, regulatory pathways, cost-benefit analysis, platform integration, HIPAA compliance

### Enhanced
- 🔄 Existing skills now cross-reference new domain expertise:
  - `research-strategy`: Links to device-selection and dtx-development for sensor/regulatory planning
  - `algo-development`: Links to device-selection and clinical-indices for hardware feasibility and fusion methodologies
  - `review-validation`: Cross-reference section added (currently minimal, expandable in future)

### Quality Metrics (v1.1.0)
- **7 total skills** (3 core methodology + 4 domain-specific)
- **26 reference files** (14 original + 12 new)
- **12 shared resources** (8 original + 4 new)
- **20 QA scenarios** (new: 5 per domain skill)
- **3,294+ lines of new content** across 28 files
- **100% cross-reference coverage** between related skills

---

## [Unreleased]

### Planned
- Additional SOP modules (data management, safety monitoring)
- Translation to other languages
- Video tutorials
- Integration examples with research tools

---

**Legend:**
- ✨ New features
- 🐛 Bug fixes
- 📖 Documentation
- 🔧 Infrastructure
- 🎯 Optimization
- ⚠️ Breaking changes
