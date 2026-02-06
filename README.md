# Research & Algorithm Development Skills

**Standard Operating Procedures (SOPs) for digital health research, algorithm development, and clinical validation.**

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-Apache%202.0-green)
![OpenCode](https://img.shields.io/badge/OpenCode-compatible-purple)
![Qwen-Pro](https://img.shields.io/badge/Qwen--Pro-optimized-orange)
![Status](https://img.shields.io/badge/status-stable-success)
![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen)

---

## 📖 Overview

The **Research & Algorithm Development Skills** repository transforms complex Standard Operating Procedures (SOPs) into interactive, AI-driven capabilities. Designed for the **OpenCode** ecosystem and optimized for **Qwen-Pro**, this collection empowers researchers, data scientists, and clinical leads to execute rigorous scientific workflows with speed and precision.

This repository encapsulates **seven specialized skills** derived from industry-standard SOPs:

**Core Skills (Methodology):**
1.  **Research Strategy (`research-strategy`)**: From concept to study design.
2.  **Algorithm Development (`algo-development`)**: Technical feasibility, selection, and implementation.
3.  **Review & Validation (`review-validation`)**: Systematic reviews and clinical validation protocols.

**Domain-Specific Skills:**
4.  **Device Selection (`device-selection`)**: Wearable sensor and platform selection for clinical studies.
5.  **DTx Development (`dtx-development`)**: Digital therapeutics regulatory pathways (DiGA/FDA).
6.  **Clinical Indices (`clinical-indices`)**: Multi-sensor fusion and composite biomarker methodologies.
7.  **RPM Platform (`rpm-platform`)**: Remote patient monitoring architecture and integration.

### What Problems Does This Solve?
*   **Complexity Overload**: Navigating FDA guidance, PRISMA checklists, and technical feasibility studies is overwhelming. These skills break them down into step-by-step interactive guides.
*   **Inconsistency**: Ensures every research proposal, literature review, and validation plan follows the same high standard.
*   **Knowledge Gaps**: Bridges the gap between clinical requirements and technical implementation.

### Who Is This For?
*   **Digital Health Researchers**: Designing studies and defining digital measures.
*   **Data Scientists**: Selecting algorithms and planning validation strategies.
*   **Regulatory Affairs**: Ensuring evidence generation meets compliance standards.
*   **Grant Writers**: Structuring robust research proposals.

---

## ✨ Features

### 🤖 Designed for AI Agents (Qwen-Pro + OpenCode)
These skills are not just text files; they are engineered prompts and structured data designed for Large Language Models.
*   **Structured Markdown**: Tables, headers, and lists are formatted for optimal token ingestion.
*   **Progressive Disclosure**: Complex workflows are broken into manageable steps to prevent context overflow.
*   **Cross-Referencing**: Skills intelligently link to shared resources and templates.

### 📚 Evidence-Based Content
Built on the foundation of rigorous scientific standards:
*   **PRISMA 2020**: For systematic literature reviews.
*   **GRADE**: For grading quality of evidence.
*   **FDA Digital Health Guidance**: For regulatory alignment.
*   **PICOS Framework**: For defining research questions.

### 📦 Comprehensive Coverage
*   **7 Specialized Skills** covering 12 distinct domain areas.
*   **26 Reference Files** containing detailed methodologies, case studies, and checklists.
*   **12 Shared Resources** including device comparison matrices, regulatory pathway guides, and visualization best practices.
*   **20 QA Scenarios** demonstrating real-world applications with expected workflows and verification criteria.

---

## 🚀 Installation

### Prerequisites
1.  **OpenCode CLI**: Ensure you have the OpenCode environment installed.
    *   [OpenCode Installation Guide](https://github.com/opencode/cli)
2.  **LLM Access**: Optimized for Qwen-Pro (via API or local), but compatible with GPT-4, Claude 3.5 Sonnet, and Gemini Pro.

### Install Steps

#### 1. Clone the Repository
```bash
git clone https://github.com/chenhaodev/research-algo-skills.git
cd research-algo-skills
```

#### 2. Install Skills to OpenCode
Copy the skills directory to your local OpenCode configuration.

**For macOS / Linux:**
```bash
# Create directory if it doesn't exist
mkdir -p ~/.opencode/skills

# Copy skills
cp -r .opencode/skills/* ~/.opencode/skills/
```

**For Windows (PowerShell):**
```powershell
# Create directory if it doesn't exist
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.opencode\skills"

# Copy skills
xcopy /E /I .opencode\skills "$env:USERPROFILE\.opencode\skills"
```

#### 3. Verify Installation
Run the following command to ensure OpenCode recognizes the new skills:
```bash
opencode list-skills
```
*You should see 7 skills: `research-strategy`, `algo-development`, `review-validation`, `device-selection`, `dtx-development`, `clinical-indices`, and `rpm-platform` in the list.*

---

## 💡 Usage

You can activate these skills using **Contextual Auto-Load** (natural language) or **Explicit Commands**.

### Method 1: Contextual Auto-Load
The AI agent monitors for specific keywords and intent.

*   **Research Strategy**:
    > "I need to develop a digital measure for nocturnal scratching in atopic dermatitis."
    > *Agent activates `research-strategy` skill to guide you through the Concept of Interest (COI) and Context of Use (COU).*

*   **Algorithm Development**:
    > "Help me evaluate algorithms for detecting atrial fibrillation from PPG data."
    > *Agent activates `algo-development` to assist with technical feasibility and algorithm selection.*

*   **Review & Validation**:
    > "I need to validate my sleep staging algorithm against PSG gold standard."
    > *Agent activates `review-validation` to draft a validation protocol.*

### Method 2: Explicit Slash Commands
Force the use of a specific skill.

*   `/research-strategy` - Start a new research planning session.
*   `/algo-development` - Begin algorithm selection or feasibility analysis.
*   `/review-validation` - Start a systematic review or validation protocol.

### Example Interaction

**User:**
> "I want to do a systematic literature review on wearable sensors for Parkinson's disease."

**Agent (using `review-validation`):**
> "I can help with that. I've loaded the **Systematic Review & Validation** skill.
>
> To ensure we follow the **PRISMA 2020** guidelines, let's start by defining your search strategy using the **PICOS** framework:
>
> 1.  **Population**: (e.g., Patients with early-stage Parkinson's)
> 2.  **Intervention**: (e.g., Wrist-worn accelerometry)
> 3.  **Comparator**: (e.g., UPDRS clinical scores)
> 4.  **Outcomes**: (e.g., Tremor frequency, bradykinesia)
> 5.  **Study Design**: (e.g., RCTs, observational studies)
>
> Please provide details for these categories, and I will help you construct the search query strings."

---

## 📂 Repository Structure

```text
research-algo-skills/
├── README.md                   # This documentation
├── LICENSE                     # Apache 2.0 License
├── CONTRIBUTING.md             # Guidelines for contributors
├── CHANGELOG.md                # Version history
├── .gitignore                  # Git ignore rules
├── .opencode/
│   └── skills/
│       ├── research-strategy/  # Core: Study design & planning
│       │   ├── SKILL.md        # Main prompt logic
│       │   ├── references/     # SOP-R-1 guides
│       │   └── assets/         # QA scenarios
│       ├── algo-development/   # Core: Algorithm selection
│       │   ├── SKILL.md
│       │   ├── references/     # SOP-R-3 technical guides
│       │   └── assets/
│       ├── review-validation/  # Core: Validation protocols
│       │   ├── SKILL.md
│       │   ├── references/     # SOP-R-4, PRISMA
│       │   └── assets/
│       ├── device-selection/   # Domain: Wearable sensor selection
│       │   ├── SKILL.md
│       │   ├── references/     # Sensor evaluation criteria
│       │   └── assets/         # QA scenarios (5 scenarios)
│       ├── dtx-development/    # Domain: Digital therapeutics
│       │   ├── SKILL.md
│       │   ├── references/     # DiGA/FDA pathways, Pear reSET case
│       │   └── assets/         # QA scenarios (5 scenarios)
│       ├── clinical-indices/   # Domain: Multi-sensor fusion
│       │   ├── SKILL.md
│       │   ├── references/     # HeartLogic CHF, NOL Pain examples
│       │   └── assets/         # QA scenarios (5 scenarios)
│       ├── rpm-platform/       # Domain: Remote monitoring
│       │   ├── SKILL.md
│       │   ├── references/     # VitalConnect architecture
│       │   └── assets/         # QA scenarios (5 scenarios)
│       └── shared/             # Cross-skill resources
│           ├── device-comparison-matrix.md
│           ├── dtx-regulatory-pathways.md
│           ├── visualization-best-practices.md
│           └── multi-sensor-fusion-methodology.md
└── examples/                   # Example outputs and case studies
    ├── example_research_plan.md
    ├── example_validation_protocol.md
    └── ...
```

---

## 📊 Skill Coverage

### Skill 1: Research Strategy & Planning (`research-strategy`)
Focuses on the early stages of research, defining *what* to measure and *why*.

| Phase | Duration | Key Activities | Primary Outcome |
|-------|----------|----------------|-----------------|
| **1. Concept** | 1-2 Weeks | Define Concept of Interest (COI), Context of Use (COU), Patient Population. | **Research Concept Document** |
| **2. Feasibility** | 2-3 Weeks | Assess clinical relevance, technical feasibility, and operational requirements. | **Feasibility Report** |
| **3. Design** | 2-4 Weeks | Study design (observational vs. interventional), endpoint definition. | **Study Synopsis** |
| **4. Planning** | Ongoing | Resource allocation, timeline estimation, risk assessment. | **Project Plan** |

### Skill 2: Algorithm Development (`algo-development`)
Focuses on the *how*—selecting and developing the technical solution.

| Step | Focus | Key Resources | Output |
|------|-------|---------------|--------|
| **1. Tech Feasibility** | Signal Quality, Data Availability | `SOP-R-3_Feasibility` | **Technical Feasibility Assessment** |
| **2. Algo Selection** | Literature Search, Benchmark Comparison | `SOP-R-3_Systematic_Review` | **Algorithm Selection Report** |
| **3. Development** | Training, Testing, Optimization | `SOP-R-3_Technique_Plan` | **Algorithm Development Plan** |
| **4. Documentation** | Code structure, API design, Reproducibility | `OpenCode Standards` | **Technical Documentation** |

### Skill 3: Review & Validation (`review-validation`)
Focuses on *proof*—verifying the solution works as intended.

| Methodology | When to Use | Key Standards | Deliverable |
|-------------|-------------|---------------|-------------|
| **Systematic Review** | Before development; to establish state-of-the-art. | PRISMA 2020, GRADE | **Literature Review Summary** |
| **Analytical Validation** | Lab setting; testing sensor accuracy. | V3 Framework | **Analytical Validation Report** |
| **Clinical Validation** | Real-world; testing clinical relevance. | FDA Guidance, ICH E6 | **Clinical Validation Protocol** |

---

## 🔑 Key Features by Skill

### 1. Research Strategy
*   **What it covers**: The "SOP-R-1" workflow. It guides users from a vague idea to a concrete research proposal.
*   **When to use it**: At the very beginning of a project, or when pivoting to a new therapeutic area.
*   **Key Methodologies**:
    *   **Meaningful Aspect of Health (MAH)**: Linking digital signals to patient quality of life.
    *   **Concept of Interest (COI)**: Defining exactly what is being measured.
*   **Reference Files**: `SOP-R-1_Project_Strategy`, `Nocturnal_Scratch_Example`.

### 2. Algorithm Development
*   **What it covers**: The "SOP-R-3" workflow. It handles the technical heavy lifting of choosing and planning algorithm implementation.
*   **When to use it**: After the research question is defined, when you need to determine *how* to measure the signal.
*   **Key Methodologies**:
    *   **Evidence Checklist**: Scoring potential algorithms based on published performance.
    *   **Predictive Biomarker Framework**: Evaluating utility for prediction vs. diagnosis.
*   **Reference Files**: `SOP-R-3_Technique_Develop_Plan`, `Predictive-Biomarkers_v1.0`.

### 3. Review & Validation
*   **What it covers**: The "SOP-R-4" workflow and Systematic Reviews. It ensures scientific rigor.
*   **When to use it**: When gathering evidence or proving performance.
*   **Key Methodologies**:
    *   **PRISMA**: Preferred Reporting Items for Systematic Reviews and Meta-Analyses.
    *   **Gold Standard Comparison**: Statistical methods for comparing against ground truth (e.g., Bland-Altman, Kappa).
*   **Reference Files**: `SOP-R-4_Validation_Protocol`, `Systematic_Review_v1.0`.

---

## ⚡ Qwen-Pro Optimization

This repository is specifically tuned for **Qwen-Pro** (and similar high-reasoning models) within the OpenCode environment.

### Why Qwen-Pro?
*   **Large Context Window**: Capable of holding multiple SOPs and the user's project details simultaneously.
*   **Structured Output**: Excellent at generating markdown tables, JSON configurations, and formatted reports.
*   **Reasoning Capability**: Can infer missing details in a research plan and suggest improvements based on standard guidelines.

### Optimization Techniques
1.  **Structured Tables**: Data is presented in markdown tables to help the model parse relationships between study phases and deliverables.
2.  **Step-by-Step Procedures**: SOPs are broken down into numbered lists, allowing the model to track progress ("Step 3 of 10").
3.  **Self-Contained Sections**: Each skill module contains all necessary context, reducing the need for the model to "hallucinate" external standards.
4.  **Consistent Terminology**: Terms like "COI", "COU", and "V3 Framework" are defined once and used consistently.

---

## 🧪 Use Cases

### Scenario 1: New Digital Measure Development
**Challenge**: A researcher wants to develop a digital biomarker for "fatigue" in Multiple Sclerosis patients using a smartwatch.
**How Skills Help**: `research-strategy` guides the definition of "fatigue" (is it physical? cognitive?) and maps it to sensor data (accelerometer, heart rate).
**Query**: "Help me design a study to measure fatigue in MS patients using an Apple Watch."
**Outcome**: A Research Concept Document outlining the COI (Fatigue), COU (Monitoring treatment response), and required sensor inputs.

### Scenario 2: Algorithm Selection for Biomarker
**Challenge**: A data scientist needs to detect "gait freezing" in Parkinson's patients but doesn't know which algorithm is best.
**How Skills Help**: `algo-development` triggers a search for existing algorithms, evaluates them using the Evidence Checklist, and recommends a starting point (e.g., a specific CNN architecture).
**Query**: "Find and evaluate algorithms for detecting freezing of gait in Parkinson's disease."
**Outcome**: An Algorithm Selection Report comparing 3 top candidates with accuracy metrics and implementation complexity.

### Scenario 3: Systematic Literature Review
**Challenge**: A team needs to summarize the state of the art in "voice biomarkers for depression" for a grant application.
**How Skills Help**: `review-validation` enforces PRISMA standards, helping generate search strings for PubMed/IEEE and structuring the extraction table.
**Query**: "Conduct a systematic review on voice biomarkers for depression diagnosis."
**Outcome**: A PRISMA-compliant flow diagram and a data extraction table of relevant papers.

### Scenario 4: Validation Study Design
**Challenge**: An algorithm is ready, but it needs to be validated to FDA standards.
**How Skills Help**: `review-validation` drafts a protocol that defines the "Gold Standard" (e.g., psychiatrist interview), sample size, and statistical analysis plan.
**Query**: "Draft a clinical validation protocol for my depression voice biomarker."
**Outcome**: A comprehensive Clinical Validation Protocol document ready for IRB submission.

### Scenario 5: Regulatory Pathway Planning
**Challenge**: A startup wants to know if their tool is a "Medical Device" (SaMD) or a "Wellness Tool".
**How Skills Help**: `research-strategy` helps map the intended use to FDA guidance documents to assess regulatory risk.
**Query**: "Is my sleep tracking algorithm a medical device? It diagnoses sleep apnea."
**Outcome**: A Regulatory Assessment summary citing relevant FDA guidance on SaMD.

---

## 🤝 Contributing

We welcome contributions from the scientific and open-source community!

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

### Areas Where Help is Needed
*   **New SOP Modules**: Data Management, Safety Monitoring, IRB Submission.
*   **Translations**: Adapting SOPs for EU (EMA) or Asian regulatory environments.
*   **Integration Examples**: Jupyter notebooks demonstrating the algorithms.
*   **Case Studies**: Real-world examples of successful validations.

---

## 📄 License

This project is licensed under the **Apache 2.0 License** - see the [LICENSE](LICENSE) file for details.

**Summary**:
*   ✅ **You can**: Commercialize, modify, distribute, and use privately.
*   ❌ **You cannot**: Hold the authors liable.
*   ℹ️ **You must**: Include the original license and copyright notice.

**Disclaimer**: *These skills and SOPs are for educational and research planning purposes. They do not constitute professional medical or legal advice. Always consult with qualified regulatory and clinical professionals for human subjects research.*

---

## 📞 Support & Contact

*   **Issues**: [GitHub Issues](https://github.com/chenhaodev/research-algo-skills/issues)
*   **Email**: support@opencode.dev
*   **Community**: Join the [OpenCode Discord](https://discord.gg/opencode)

---

## 🙏 Acknowledgments

*   **SOP Sources**: Based on internal SOP-R-1, SOP-R-3, and SOP-R-4 frameworks for digital health excellence.
*   **Standards**:
    *   [PRISMA 2020](http://www.prisma-statement.org/)
    *   [GRADE Working Group](https://www.gradeworkinggroup.org/)
    *   [FDA Digital Health](https://www.fda.gov/medical-devices/digital-health)
*   **Technology**: Powered by [OpenCode](https://opencode.dev) and optimized for [Qwen-Pro](https://huggingface.co/Qwen).
*   **Inspiration**: Modeled after the `carepath-skills` architecture.

---

## 📜 Version History

See [CHANGELOG.md](CHANGELOG.md) for full history.

*   **v1.1.0** (2026-02-06): Domain-specific skills expansion.
    *   Added 4 new domain-specific skills: `device-selection`, `dtx-development`, `clinical-indices`, `rpm-platform`.
    *   Created 12 new reference files with clinical examples (HeartLogic CHF, NOL Pain, Pear reSET).
    *   Added 4 shared resources for cross-skill reference (device matrix, regulatory pathways, visualization patterns, fusion methodology).
    *   Developed 20 QA scenarios (5 per new skill) demonstrating real-world workflows.
    *   Enhanced existing skills with cross-references to new domain expertise.

*   **v1.0.0** (2026-02-02): Initial release.
    *   Added `research-strategy` skill.
    *   Added `algo-development` skill.
    *   Added `review-validation` skill.
    *   Included 6 core SOPs and 14 reference documents.

---

## 🔗 Additional Resources

*   **Training Materials**: Check the `examples/` directory for walkthroughs.
*   **Related Projects**:
    *   `carepath-skills`: Clinical pathway automation.
    *   `med-stats-skills`: R/Python scripts for medical statistics.
