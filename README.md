# 🛡️ AI-Based Phishing & Email Security — Regulatory Graph Automation Artefact

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]
> **Interactive, touch-responsive knowledge graph** mapping the full regulatory obligations, risks, stakeholders, and automation artefacts for an AI-based phishing & email security system (Microsoft Defender for Office 365) deployed in a representative NHS/Corporate UK environment.

**Module:** Enterprise Security Management (7CS085) · 2026  
**System under analysis:** Microsoft Defender for Office 365 — NHS/Corporate UK Deployment  
**Regulatory frameworks covered:** EU AI Act (2024/1689) · UK GDPR/DPA 2018 · UK AI White Paper (DSIT 2023) · NIS Regulations 2018/NIS2 · Equality Act 2010 · Investigatory Powers Act 2016

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Graph Structure](#-graph-structure)
- [Regulatory Layers](#-regulatory-layers)
- [Automation Artefacts](#-automation-artefacts)
- [Quick Start](#-quick-start)
- [Running in Google Colab](#-running-in-google-colab)
- [Running Locally](#-running-locally)
- [Notebook Structure](#-notebook-structure)
- [Key Findings](#-key-findings)
- [Exported Files](#-exported-files)
- [Repository Structure](#-repository-structure)
- [Dependencies](#-dependencies)
- [References](#-references)

---

## 🔍 Overview

This notebook produces an **interactive relational graph database** of the regulatory and governance landscape surrounding AI-based email security systems. Rather than a static diagram, every node is queryable, draggable, and searchable. Clicking any node reveals its full regulatory description, article reference, and URL.

The central argument motivating the graph:

> *AI phishing detection systems occupy a regulatory grey zone — consequential enough to warrant high-risk designation under the EU AI Act, yet routinely deployed without the transparency, oversight, and accountability mechanisms such designation requires.*

The graph makes this argument visible by connecting:
- **Laws → Articles → Risks** (which articles each risk violates)
- **Risks → Mitigations → Compliance modules** (what addresses each risk)
- **Stakeholders → Obligations** (who is accountable under which law)
- **Automation artefacts → Compliance enablement** (which tools deliver compliance)

---

## 📊 Graph Structure

| Layer | Node Count | Description |
|-------|-----------|-------------|
| 🖥️ **AI System** | 1 | Microsoft Defender for Office 365 (centre node) |
| 🔵 **EU AI Act** | 12 | Art. 9, 10, 11, 12, 13, 14, 15, 16, 50, 51 + Annex III |
| 🔴 **UK GDPR / DPA 2018** | 5 | Art. 5, 6, 15, 22, 35 + IPA 2016 |
| 🟠 **UK AI White Paper 2023** | 5 | Five cross-sector principles |
| 🟣 **NIS Regulations / NIS2** | 3 | Essential service obligations + NCSC ACD |
| ⚖️ **Equality Act 2010** | 1 | Indirect discrimination via algorithmic bias |
| 🟡 **Risk Register** | 7 | R-01 through R-07 |
| 🟢 **Stakeholders** | 6 | Vendor, IT Security, Employees, DPO, Executive, Regulators |
| 🩷 **Automation Artefacts** | 5 | Compliance Checker, DPIA, HITL Workflow, Risk Matrix, Bias Audit |
| **Total nodes** | **~50** | |
| **Total edges** | **84** | REQUIRES, SUBJECT_TO, VIOLATES, IMPLEMENTS, MITIGATES, ALIGNS_WITH… |

### Relationship Types

| Relationship | Meaning |
|---|---|
| `REQUIRES` | Article mandates this obligation |
| `SUBJECT_TO` | System/process subject to this law/article |
| `VIOLATES` | Risk potentially violates this article |
| `IMPLEMENTS` | Artefact/mitigation implements this requirement |
| `MITIGATES` | Mitigation addresses this risk |
| `ALIGNS_WITH` | White Paper principle alignment |
| `HELD_BY` | Stakeholder holds this obligation/right |
| `ADDRESSES` | Compliance module addresses this area |
| `ASSESSED_BY` | Risk/article assessed by this module |

---

## ⚖️ Regulatory Layers

### 🔵 EU AI Act (Regulation 2024/1689)

The graph argues that Microsoft Defender for Office 365 in NHS deployments meets **Annex III High-Risk** criteria across two categories:

- **Category 2 — Critical Infrastructure:** NHS email = NIS-designated critical infrastructure; AI blocking communications on it meets Annex III Cat. 2
- **Category 4 — Employment Management:** Autonomous quarantine of work communications affects employment conditions

Currently misclassified as **Limited Risk** (transparency obligations only).

Key articles modelled: Art. 9 (Risk Mgmt), Art. 10 (Data Governance), Art. 11 (Technical Docs), Art. 12 (Record Keeping), Art. 13 (Transparency), Art. 14 (Human Oversight), Art. 15 (Accuracy & Cybersecurity), Art. 16 (Provider Obligations), Art. 50 (User Notification), Art. 51 (Registration).

### 🔴 UK GDPR / DPA 2018

| Article | Issue |
|---------|-------|
| **Art. 22** | Automated quarantine without substantive human review — highest risk node in graph |
| **Art. 35** | DPIA not conducted — M3 module scored **0.0%** |
| **Art. 15** | Employees have right of access to AI-derived threat scores |
| **Art. 6(1)(f)** | Legitimate interest balancing exercise required but rarely completed |
| **Art. 5** | Data principles — M1 module scored 33.3% |

### 🟣 NIS Regulations 2018 / NIS2

NHS Trusts and financial operators of essential services must take appropriate and proportionate security measures. NIS2 significantly raises supply chain AI assurance requirements — vendor model refresh cadence must be documented in procurement contracts.

### ⚖️ Equality Act 2010

NLP models trained on Western English corpora produce higher false positive rates for non-native English speakers — R-04 (Algorithmic Bias) rated **MEDIUM** risk with potential Equality Act s.19 (indirect discrimination) exposure.

---

## 🤖 Automation Artefacts

Four structured artefacts are generated and exported by the notebook:

### 1. Governance Compliance Checker
**Overall NHS Trust Score: 42/150 = 28.0% — HIGH RISK**

| Module | Regulatory Basis | Questions | NHS Score | Status |
|--------|-----------------|-----------|-----------|--------|
| M1 — GDPR Lawful Basis | UK GDPR Art. 5, 6, 13 | 6 | 33.3% | ⚠️ Non-Compliant |
| M2 — Article 22 Compliance | UK GDPR Art. 22; ICO 2024 | 8 | 21.3% | 🔴 Non-Compliant |
| M3 — DPIA Completion | UK GDPR Art. 35; ICO DPIA | 5 | **0.0%** | 🚨 Critical |
| M4 — EU AI Act Transparency | EU AI Act Art. 50; UK WP Prin. 3 | 5 | 40.0% | ⚠️ Non-Compliant |
| M5 — NIS / Human Oversight | NIS Regs 2018; AI Act Art. 14 | 6 | 35.7% | ⚠️ Non-Compliant |

### 2. Risk Register (R-01 to R-07)

| ID | Description | Risk Level | Regulatory Exposure |
|----|-------------|------------|---------------------|
| R-01 | False Negative — ransomware infection | 🔴 HIGH | NIS Regs; NHS DSPT; CQC |
| R-02 | False Positive — patient safety | 🔴 HIGH | UK GDPR Art. 22; CQC |
| R-03 | Art. 22 non-compliance | 🔴 HIGH | ICO enforcement; 4% turnover |
| R-04 | Algorithmic bias — indirect discrimination | 🟠 MEDIUM | Equality Act 2010; ICO |
| R-05 | Automation bias — analyst over-reliance | 🟡 MED-HIGH | NIS Regs; Art. 14 |
| R-06 | Adversarial ML evasion | 🟠 MEDIUM | NIS Regs; NIS2 supply chain |
| R-07 | DPIA absent | 🟡 MED-HIGH | ICO; UK GDPR Art. 35 |

### 3. HITL Workflow (Human-in-the-Loop)
Implements EU AI Act Art. 14 + UK GDPR Art. 22 safeguards. Routes ambiguous-zone cases (confidence 35–75%) to mandatory human review with SHAP feature attribution before verdict is accepted.

### 4. DPIA Template
Structured Data Protection Impact Assessment template for AI email security deployments. Pre-populated with processing description, necessity/proportionality test, risks identified, and ICO consultation trigger criteria.

---

## 🚀 Quick Start

### Option A — Google Colab (Recommended, zero setup)

1. Click the **Open in Colab** badge at the top of this README
2. Select **Runtime → Run all** (`Ctrl+F9`)
3. Wait ~60 seconds for installation and graph rendering
4. Interact with the graph — click, drag, zoom, search

### Option B — Local Jupyter

```bash
# 1. Clone the repository
git clone (https://github.com/Adnanvk/AI-Based_Phishing_-_Email_Security_Systems)
cd YOUR_REPO

# 2. Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # Linux/macOS
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch Jupyter
jupyter notebook AI_Phishing_Regulatory_Graph_Artefact.ipynb
```

---

## ☁️ Running in Google Colab

The notebook is fully configured for Colab. Cell 1 automatically:
- Installs `yfiles_jupyter_graphs`, `networkx`, `pyyaml`, `matplotlib`
- Enables the custom widget manager required for interactive graphs in Colab
- Detects the environment and prints confirmation

**No API keys, credentials, or local files required.**

> ⚠️ If the graph widget appears blank in Colab, go to **Runtime → Restart and run all**. This is a known widget initialisation quirk in some Colab environments.

---

## 💻 Running Locally

### Requirements

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab

### Tested Environments

| Environment | Status |
|-------------|--------|
| Google Colab (recommended) | ✅ Fully supported |
| JupyterLab 3.x / 4.x | ✅ Supported |
| Jupyter Notebook 6.x | ✅ Supported |
| VS Code (Jupyter extension) | ✅ Supported |

### Widget Support Note

`yfiles_jupyter_graphs` requires the Jupyter widget infrastructure. If widgets do not render:

```bash
# For JupyterLab
pip install jupyterlab_widgets
jupyter labextension install @jupyter-widgets/jupyterlab-manager

# For classic Notebook
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension
```

---

## 📓 Notebook Structure

| Step | Cell | Description |
|------|------|-------------|
| **Step 1** | Setup | Install packages, enable Colab widget manager |
| **Step 2** | Nodes & Edges | Define all 50 nodes and 84 edges with full descriptions |
| **Step 3** | Colour & Style | `build_graph()` helper with category-based colour mapping |
| **Step 4** | Full Graph | Complete interactive graph — all layers and relationships |
| **Step 5** | Subgraphs | 6 themed subgraphs (risks, GDPR, EU AI Act, stakeholders, etc.) |
| **Step 6** | Analytics | NetworkX degree centrality, matplotlib compliance bar chart |
| **Step 7** | Artefact Content | Full YAML output for all 4 automation artefacts |
| **Step 8** | Export | Writes YAML/JSON/PNG files; auto-downloads in Colab |

### Subgraphs Available (Step 5)

1. **Risk Register × Legal Violations** — which risks violate which articles
2. **GDPR Focus** — all nodes connected to UK GDPR obligations
3. **EU AI Act Focus** — Art. 9–16 + Annex III argument chain
4. **Stakeholder Accountability** — who is accountable under which law
5. **HIGH Risk Only** — R-01, R-02, R-03 and their full connections
6. **High-Centrality Nodes** — regulatory "pressure points" (degree ≥ 5)

---

## 🎯 Key Findings

The graph makes five structural findings visible:

1. **UK GDPR Art. 22 is the highest-centrality law node** — connected simultaneously to R-02, R-03, R-05, EU AI Act Art. 14, the HITL artefact, and three stakeholder groups. Non-compliance exposes deployers to ICO enforcement up to 4% of global turnover.

2. **M3 (DPIA) = 0% is the most critical gap** — R-07 shows no DPIA was conducted before deployment, directly violating Art. 35 UK GDPR. This is mandatory, not optional.

3. **The HITL Artefact is a dual-compliance node** — simultaneously satisfies EU AI Act Art. 14 (human oversight) and UK GDPR Art. 22 (automated decision safeguards). Most efficient single investment.

4. **Accountability laundering is structurally visible** — ST_VENDOR, ST_IT, and ST_EXEC are all connected to legal obligations but no single stakeholder node holds full accountability.

5. **NHS Trust overall compliance: 28%** — all five compliance modules rated non-compliant. The graph confirms immediate regulatory action is required before the system can be considered lawfully deployed.

---

## 💾 Exported Files

Running Step 8 generates the following files (auto-downloaded in Colab):

| File | Format | Description |
|------|--------|-------------|
| `compliance_checker.yaml` | YAML | Full 5-module compliance checker with NHS Trust scores and remediation list |
| `risk_register.yaml` | YAML | All 7 risks (R-01 to R-07) with mitigations, owners, and review schedules |
| `hitl_workflow.yaml` | YAML | Human-in-the-Loop review workflow (Art. 14 + Art. 22 safeguards) |
| `dpia_template.yaml` | YAML | DPIA template pre-populated for AI email security deployments |
| `regulatory_graph.json` | JSON | Full graph (nodes + edges) for import into Neo4j, Gephi, or D3.js |
| `compliance_analysis.png` | PNG | Static matplotlib bar chart of compliance scores and degree centrality |

---

## 📁 Repository Structure

```
.
├── AI_Phishing_Regulatory_Graph_Artefact.ipynb   # Main notebook
├── README.md                                       # This file
├── requirements.txt                                # Python dependencies

---

## 📦 Dependencies

See [`requirements.txt`](requirements.txt) for pinned versions. Core packages:

| Package | Purpose |
|---------|---------|
| `yfiles_jupyter_graphs` | Interactive graph widget (touch + mouse, drag, zoom, search) |
| `networkx` | Graph analytics — degree centrality, path analysis |
| `pyyaml` | YAML serialisation for artefact export |
| `matplotlib` | Static compliance bar chart and degree centrality plot |
| `ipywidgets` | Jupyter widget infrastructure |

---

## 📚 References

| # | Citation |
|---|---------|
| [1] | European Parliament and Council. 2024. Regulation (EU) 2024/1689 (EU AI Act). *Official Journal of the EU.* |
| [2] | DSIT. 2023. *A Pro-Innovation Approach to AI Regulation.* UK AI White Paper. CP 815. HMSO. |
| [3] | Adams, A. and Sasse, M.A. 1999. Users are not the enemy. *Commun. ACM* 42, 12, 40–46. |
| [4] | Blodgett, S.L. et al. 2020. Language (Technology) is Power. *ACL 2020,* 5454–5476. |
| [5] | Hadlington, L. 2017. Human factors in cybersecurity. *Heliyon* 3, 7, e00346. |
| [6] | ICO. 2024. *Guidance on AI and Data Protection.* London: ICO. |
| [7] | Lipton, Z.C. 2018. The mythos of model interpretability. *Queue* 16, 3, 31–57. |
| [8] | NCSC. 2024. *Phishing Attacks: Defending Your Organisation.* NCSC. |
| [9] | Parasuraman, R. and Manzey, D.H. 2010. Complacency and bias in human use of automation. *Human Factors* 52, 3. |
| [10] | Shneiderman, B. 2022. *Human-Centered AI.* Oxford University Press. |
| [11] | UK Government. 2018. *Network and Information Systems (NIS) Regulations 2018.* SI 2018/506. |
| [12] | UK Government. 2018. *Data Protection Act 2018.* c.12. London: HMSO. |
| [13] | Equality Act 2010. c.15. London: HMSO. |
| [14] | Investigatory Powers Act 2016. c.25. London: HMSO. |

---

## 📄 Licence

This project is licensed under the **MIT Licence** — see the [LICENSE](LICENSE) file for details.

---

*Enterprise Security Management (7CS085) · 2026 · AI-Based Phishing & Email Security Systems*  
*Microsoft Defender for Office 365 — Representative NHS/Corporate UK Deployment*
