# Toolbox Research Strategy

This document outlines the process for identifying, evaluating, and selecting open-source software libraries and toolboxes to accelerate algorithm development. Reusing high-quality existing code is preferred over building from scratch.

## 1. GitHub Search Strategies

GitHub is the primary source for research code and production-ready libraries.

### Search Query Construction
*   **Keywords:** Combine the algorithm name with the domain.
    *   Example: `"heart rate variability"`, `"sleep staging"`, `"QRS detection"`.
*   **Language Filters:** Restrict to your target stack (usually Python for ML).
    *   `language:Python`, `language:C++`, `language:Rust`.
*   **Topic Tags:** Search by topics to find curated lists.
    *   `topic:machine-learning`, `topic:biomedical-signal-processing`.

### Advanced Filters
*   **Stars:** `stars:>50` (Filters out hobby projects).
*   **Forks:** `forks:>10` (Indicates active usage/modification).
*   **Recency:** `pushed:>2023-01-01` (Filters out abandoned projects).
*   **Sort:** Sort by "Recently updated" or "Most stars".

## 2. Package Ecosystem Evaluation

Beyond GitHub, check language-specific package managers for "install-ready" libraries.

*   **Python (PyPI):** Check `pypi.org`. Look for "Development Status" classifiers (e.g., "5 - Production/Stable").
*   **JavaScript/TypeScript (npm):** Check `npmjs.com`. Look at "Weekly Downloads" and "Dependents".
*   **R (CRAN):** Check CRAN task views for "MedicalImaging" or "TimeSeries".
*   **MATLAB File Exchange:** Useful for academic prototypes, but often requires translation to Python/C++ for production.

## 3. Evaluation Criteria (MUCD Framework)

Assess every candidate library using the **MUCD** framework.

### M - Maintenance
*   **Last Commit:** Is the project active? (Ideal: < 3 months ago).
*   **Release Frequency:** Are there regular tagged releases?
*   **Issue Response:** Are issues being closed? Check the "Closed" vs. "Open" ratio.

### U - Usage
*   **Stars:** A proxy for popularity (Target: > 100 for niche, > 1000 for general).
*   **Forks:** A proxy for developer interest.
*   **Downloads:** (If available via PyPI/npm stats).
*   **Dependents:** How many other projects rely on this library? (See "Used by" on GitHub).

### C - Community
*   **Contributors:** Is it a one-person show or a community effort? (More contributors = lower bus factor risk).
*   **Documentation:** Is there a `docs/` folder? Is it hosted on ReadTheDocs? Are there tutorials?
*   **Discussions:** Is there an active Discord, Slack, or GitHub Discussions tab?

### D - Developer Reputation
*   **Affiliation:** Is it backed by a known lab (e.g., MIT, Stanford) or company (e.g., Google, Meta)?
*   **History:** Does the author have other successful open-source projects?

## 4. Code Quality Assessment

If a library passes the MUCD check, inspect the code directly.

*   **Testing:**
    *   Are there unit tests? (Look for `tests/` folder).
    *   Is there CI/CD? (Look for `.github/workflows` or badges like "Build Passing").
    *   What is the test coverage? (Look for Codecov badge).
*   **Linting & Style:**
    *   Does the code follow standard style guides (e.g., PEP 8 for Python)?
    *   Are type hints used? (Crucial for maintainability).
*   **Modularity:**
    *   Is the code easy to read?
    *   Are functions small and single-purpose?

## 5. Licensing Considerations

Check the `LICENSE` file. This is critical for commercial use.

### Permissive (Green Light)
*   **MIT:** Do whatever you want, just keep the copyright notice.
*   **Apache 2.0:** Similar to MIT, but includes patent grants.
*   **BSD (3-Clause):** Similar to MIT.

### Copyleft / Viral (Red Light / Caution)
*   **GPL (v2/v3):** If you use this, your entire project might need to be open-sourced under GPL. **Avoid for proprietary core IP.**
*   **AGPL:** Even stricter than GPL (covers network use). **Strictly Avoid.**

*Note: Always consult legal counsel for final license verification.*

## 6. Summary Table Template

Use this template to compare toolboxes.

| Keyword | Library Name | Link | Stars | Last Commit | License | Why Promising? | Rank (0-4) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `HRV` | `pyhrv` | github.com/... | 450 | 2 months ago | MIT | Comprehensive, well-documented | 4 |
| `ECG` | `neurokit2` | github.com/... | 1.2k | 1 week ago | MIT | Multi-modal, active community | 4 |
| `Sleep` | `yasa` | github.com/... | 800 | 5 months ago | BSD | Specific to sleep staging | 3 |
| `PPG` | `ppg-lib` | github.com/... | 12 | 3 years ago | GPL | Abandoned, restrictive license | 0 |

**Rank Key:**
*   **4:** Production Ready (Active, Tested, Permissive License).
*   **3:** Good Research Code (Needs some cleanup/wrapping).
*   **2:** Reference Only (Read code, re-implement logic).
*   **1:** Poor Quality.
*   **0:** Unusable / Legal Risk.
