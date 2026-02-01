# Contributing to Research & Algorithm Development Skills

Thank you for your interest in contributing to Research & Algorithm Development Skills! This project provides standard operating procedures (SOPs) for research strategy, algorithm development, and validation in digital health and biomarker development.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Reporting Issues](#reporting-issues)
- [Suggesting Enhancements](#suggesting-enhancements)
- [Contributing SOP Content](#contributing-sop-content)
- [Pull Request Process](#pull-request-process)
- [Content Standards](#content-standards)
- [Quality Review Requirements](#quality-review-requirements)

---

## Code of Conduct

This project adheres to a professional code of conduct. By participating, you are expected to uphold this standard:

- **Be respectful**: Treat all contributors with respect and kindness
- **Be constructive**: Provide helpful feedback and suggestions
- **Be collaborative**: Work together to improve the project
- **Prioritize accuracy**: Scientific rigor and methodological soundness take precedence

---

## How Can I Contribute?

### Reporting Issues

**Before submitting an issue**, please:

1. **Search existing issues** to avoid duplicates
2. **Check the documentation** (README.md and skill reference files)
3. **Verify the issue** with the latest version

**When creating an issue**, include:

- **Clear title**: Summarize the issue in one line
- **Description**: Detailed explanation of the problem
- **Steps to reproduce**: How to recreate the issue
- **Expected behavior**: What should happen
- **Actual behavior**: What actually happens
- **Skill affected**: Which skill (research-strategy, algo-development, review-validation)
- **Reference context**: Cite specific guidelines or standards if applicable

**Issue Types:**

- 🐛 **Bug Report**: Content errors, broken links, incorrect methodology descriptions
- 📖 **Documentation**: Unclear instructions, missing information
- 🔬 **Methodological Accuracy**: Outdated standards, incorrect research procedures
- ✨ **Feature Request**: New SOPs, additional methodologies, tools

---

## Suggesting Enhancements

We welcome suggestions for:

- **New SOP modules** (e.g., data management, regulatory submissions, safety monitoring)
- **Additional methodologies** (e.g., real-world evidence, pragmatic trials)
- **Enhanced evaluation criteria**
- **Tool integrations** (research databases, statistical software)
- **Translation to other languages**

**Enhancement proposals should include:**

1. **Scientific rationale**: Why is this enhancement valuable?
2. **Evidence base**: Standards, guidelines, or best practices supporting the enhancement
3. **Implementation scope**: What files/sections would be affected?
4. **Compatibility**: Impact on existing workflows

---

## Contributing SOP Content

### SOP Content Guidelines

**ALL SOP content changes MUST**:

1. **Be evidence-based**: Reference current research standards (PRISMA, GRADE, FDA guidelines, etc.)
2. **Include source citations**: Link to standard year and organization
3. **Follow structured format**: Maintain consistency with existing SOP structure
4. **Use clear language**: Avoid jargon where possible; define technical terms
5. **Follow Qwen-Pro optimization**: Structured tables, step-by-step instructions, explicit formatting

### Content Structure Requirements

**For new SOP modules**, include:

- **Main skill file** (`.opencode/skills/{skill-name}/SKILL.md`)
  - Quick reference table
  - When to use this SOP
  - How to use (step-by-step)
  - Key methodologies
  - Examples
  - Trigger keywords

- **Reference documentation** (`.opencode/skills/{skill-name}/references/*.md`)
  - Detailed procedures
  - Templates and checklists
  - Case studies and examples
  - Standards and guidelines

- **QA scenarios** (`.opencode/skills/{skill-name}/assets/qa-scenarios-*.md`)
  - Test cases for verification
  - Example queries and expected responses

- **Updates to shared resources** (if applicable):
  - Standards and frameworks
  - Templates
  - Statistical methods

---

## Pull Request Process

### 1. Fork and Branch

```bash
# Fork the repository on GitHub
# Clone your fork
git clone https://github.com/YOUR-USERNAME/research-algo-skills.git
cd research-algo-skills

# Create a feature branch
git checkout -b feature/new-sop-module
# or
git checkout -b fix/methodology-correction
```

### 2. Make Changes

- **Follow existing file structure**
- **Match formatting style** (see Content Standards below)
- **Add cross-references** to related files
- **Test cross-references** to ensure links resolve
- **Include examples** for complex procedures

### 3. Commit Changes

```bash
# Stage your changes
git add .

# Commit with descriptive message
git commit -m "feat(validation): add adaptive trial design validation SOP"
# or
git commit -m "fix(systematic-review): correct PRISMA 2020 checklist reference"
```

**Commit message format:**

```
<type>(<scope>): <short description>

[optional body]
[optional footer]
```

**Types:**
- `feat`: New feature (SOP module, methodology)
- `fix`: Bug fix (content correction)
- `docs`: Documentation only
- `refactor`: Content restructuring without methodology change
- `test`: Adding or updating QA scenarios

**Scopes:**
- `strategy`, `algo`, `validation`, `shared`, `examples`

### 4. Push and Create PR

```bash
# Push to your fork
git push origin feature/new-sop-module

# Go to GitHub and create Pull Request
```

**Pull Request Template:**

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] New SOP module
- [ ] Methodology correction
- [ ] Documentation update
- [ ] Template addition
- [ ] Standard/guideline update

## Evidence Base
- Standard: [e.g., PRISMA 2020]
- Reference: [Link to standard/guideline]

## Checklist
- [ ] All files follow existing structure
- [ ] Cross-references updated
- [ ] Evidence-based content with citations
- [ ] Qwen-Pro optimized formatting (tables, lists)
- [ ] Self-reviewed for accuracy
- [ ] Examples included for complex procedures

## Testing
- [ ] Verified all internal links resolve
- [ ] Checked methodology against current standards
- [ ] Validated templates and checklists
```

### 5. Review Process

**Your PR will be reviewed for:**

1. **Methodological accuracy** (requires subject matter expert approval)
2. **Evidence base** (standards cited and current)
3. **Formatting consistency** (matches existing style)
4. **Cross-reference integrity** (all links work)
5. **Clarity** (understandable by target audience)

**Reviewers may request:**
- Additional citations
- Formatting changes
- Methodological clarifications
- Evidence for novel recommendations

### 6. Merge

Once approved:
- PR will be merged to `main`
- Contributors will be acknowledged in CHANGELOG.md

---

## Content Standards

### Markdown Formatting

**Headers:**
```markdown
# Top-level (skill name only)
## Major sections
### Subsections
#### Details
```

**Tables** (preferred for structured data):
```markdown
| Criterion | Definition | Score | Example |
|-----------|------------|-------|---------|
| Impact Factor | Journal IF | +1 if >4.0 | JAMA: 157.3 |
```

**Lists:**
```markdown
- Use bullet lists for non-sequential items
- Keep items concise (one line preferred)

1. Use numbered lists for step-by-step procedures
2. Each step should be actionable
```

**Links:**
```markdown
<!-- Relative internal links -->
[PRISMA Checklist](../../shared/prisma-checklist.md)

<!-- External links -->
[PRISMA 2020](http://www.prisma-statement.org/)
```

**Emphasis:**
- **Bold** for critical warnings, key terms, important concepts
- *Italics* sparingly for emphasis
- `Code blocks` for parameters, values, commands, file names

### File Naming

```
methodology-name.md          # lowercase, hyphen-separated
example-case-study.md
template-name.md
```

### YAML Frontmatter (SKILL.md files only)

```yaml
---
name: research-strategy
description: |
  Strategic framework for digital measure development from concept to regulatory acceptance.
  **Triggers**: project strategy, digital measure, COA design, regulatory endpoint
version: "1.0.0"
author: "Research & Algorithm Development Skills Contributors"
license: "Apache-2.0"
---
```

---

## Quality Review Requirements

### Mandatory for ALL Content Changes

**Changes to SOP content REQUIRE review by**:

1. **Subject Matter Expert** (researcher with relevant expertise)
   - Biostatistician for validation methods
   - Clinical researcher for feasibility analysis
   - Data scientist for algorithm development
   - Regulatory specialist for FDA guidance

2. **Methodology Review**
   - Standards cited must be current
   - Deviations from established methodologies must be documented

3. **Accuracy Review**
   - Procedures must be replicable
   - Templates and checklists must be complete and correct

### Content NOT Allowed

**Do NOT include:**
- Proprietary methodologies without permission
- Unpublished or unvalidated procedures
- Personal opinions presented as standards
- Commercial product endorsements

### Disclaimer

All skills include this disclaimer:

> These skills provide standard operating procedures based on published research standards and guidelines. They are meant to support, not replace, professional judgment and institutional review processes. Users are responsible for ensuring compliance with their institution's policies and regulatory requirements.

**This disclaimer must remain in all skill files.**

---

## Questions?

- **GitHub Issues**: [Create an issue](https://github.com/YOUR-USERNAME/research-algo-skills/issues)
- **GitHub Discussions**: [Ask a question](https://github.com/YOUR-USERNAME/research-algo-skills/discussions)

Thank you for contributing to Research & Algorithm Development Skills! 🔬
