<div align="center">

# Fraud Behavior Analysis & Compromised Identity Investigation

### A behavioral and network-based investigation of coordinated account takeover activity

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NetworkX](https://img.shields.io/badge/NetworkX-4B8BBE?style=flat-square)
![GeoIP](https://img.shields.io/badge/GeoIP-Enrichment-2E8B57?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)

[Technical Notebook](./Notebooks/1-Technical_Notebook.ipynb) · [Analysis Notebook](./Notebooks/2-%20Analysis_Notebook.ipynb) · [Investigation Report](./fraud_Investigation_Report.pdf)

</div>

---

## Executive Summary

This project investigates coordinated fraud and **Account Takeover (ATO)** behavior across multiple banking environments. It connects identities, devices, fingerprints, IP addresses, network providers, and geographic attributes to uncover patterns that isolated rule-based checks can miss.

The analysis found strong indicators of automation, device emulation, IP rotation, and shared attacker infrastructure. The final output translates technical evidence into an executive-ready fraud assessment and practical mitigation recommendations.

## Business Problem

Modern fraud campaigns can bypass conventional controls by rotating IP addresses, spoofing device fingerprints, and distributing activity across multiple identities and banks. The core challenge is not simply identifying one suspicious event—it is **connecting related entities to reveal coordinated behavior**.

This investigation answers four questions:

1. Which identities and devices show compromised behavior?
2. Are IPs, fingerprints, and devices being reused abnormally?
3. Do the suspicious entities share infrastructure or geography?
4. Which controls would reduce the risk of future attacks?

## Data at a Glance

| Measure | Value |
|---|---:|
| Raw event records | 1,436 |
| IP-level observations after expansion | 1,802 |
| Unique identities | 333 |
| Unique devices | 169 |
| Unique device fingerprints | 36 |
| Banks represented | 11 |
| Unique raw IP values | 830 |

> The original dataset is confidential and is not included in this public repository. The notebooks document the methodology, transformations, and analytical logic.

## Investigation Workflow

```text
Raw device and identity events
            ↓
Data quality and placeholder checks
            ↓
IP normalization and row-level expansion
            ↓
GeoIP, ASN, provider, OS, and browser enrichment
            ↓
Behavioral frequency and duplication analysis
            ↓
Identity ↔ Device ↔ Fingerprint ↔ IP link analysis
            ↓
Cross-bank comparison and evidence consolidation
            ↓
Executive findings and mitigation recommendations
```

### 1. Data Preparation & Enrichment

- Audited structure, formatting, and placeholder values.
- Normalized identity, device, and fingerprint fields.
- Split multi-IP cells into individual IP-level observations.
- Enriched IPs with country, city, timezone, ASN, and provider.
- Parsed operating system and browser strings into structured attributes.
- Classified device types and standardized missing values.

### 2. Behavioral & Network Analysis

- Profiled high-frequency identities, devices, fingerprints, and IPs.
- Measured device and network reuse across accounts.
- Compared suspicious activity across banks.
- Tested identity-to-device, identity-to-IP, and device-to-fingerprint integrity.
- Evaluated shared ASN, country, and provider infrastructure.
- Used relationship mapping to identify coordinated activity.

## Key Findings

| Finding | Evidence | Risk Signal |
|---|---|---|
| Fingerprint cloning | One fingerprint appeared across **113 devices** | Emulator or cloned environment |
| Identity concentration | One identity generated **496 events** | Automated or repeated account activity |
| Device concentration | One device generated **400 events** | Device farm or scripted behavior |
| IP expansion | Activity expanded to **1,802 valid IP-level observations** | High network diversity and rotation |
| Bank8 concentration | **199 identities** and **185 IPs** used only **5 devices** across 409 rows | Strong automation and device reuse |
| Bank4 concentration | **5 identities**, **43 IPs**, and **5 devices** across 48 rows | Smaller but linked suspicious cluster |
| Network linkage | Suspicious entities shared ASN, country, and fingerprint-suppression patterns | Common attacker infrastructure |

### What the Patterns Suggest

- A small number of devices and fingerprints control a disproportionately large amount of activity.
- Identities rotate through many IPs, while some IPs connect to multiple identities.
- Repeated device environments combined with IP rotation are consistent with proxy-driven automation.
- Shared infrastructure signals link suspicious entities even when direct identifiers differ.
- The overall behavior is more consistent with coordinated fraud than legitimate customer activity.

## Deliverables

| Deliverable | Purpose |
|---|---|
| [Technical Notebook](./Notebooks/1-Technical_Notebook.ipynb) | Data cleaning, normalization, IP expansion, GeoIP enrichment, and user-agent parsing |
| [Analysis Notebook](./Notebooks/2-%20Analysis_Notebook.ipynb) | Behavioral profiling, duplicate analysis, cross-feature integrity checks, and visual investigation |
| [Fraud Investigation Report](./fraud_Investigation_Report.pdf) | Executive-level findings, evidence, and recommendations |
| [Requirements](./Requirement.txt) | Python dependencies used by the project |

## Repository Structure

```text
Fraud_Behavior_Investigation_project/
├── Notebooks/
│   ├── 1-Technical_Notebook.ipynb
│   └── 2- Analysis_Notebook.ipynb
├── fraud_Investigation_Report.pdf
├── Requirement.txt
└── Readme.md
```

## Tools & Libraries

- **pandas / NumPy** — data preparation and behavioral aggregation
- **Matplotlib / Plotly** — static and interactive investigation visuals
- **NetworkX** — relationship mapping across identities, devices, and IPs
- **GeoIP2** — country, ASN, and network-provider enrichment

## Recommended Fraud Controls

1. Introduce velocity rules for rapid IP, device, and identity changes.
2. Escalate fingerprints shared across unusually large device populations.
3. Combine device, ASN, provider, country, and bank signals into risk scoring.
4. Flag identities with high IP diversity or repeated cross-device access.
5. Monitor shared network hubs connecting multiple identities and devices.
6. Add step-up authentication when device integrity and network behavior conflict.

## Reproducing the Analysis

```bash
git clone https://github.com/maha304/Fraud_Behavior_Investigation_project.git
cd Fraud_Behavior_Investigation_project
pip install -r Requirement.txt
jupyter notebook
```

Open the technical notebook first, followed by the analysis notebook. Some GeoIP enrichment steps require a local MaxMind GeoLite2 database, and the confidential source dataset is not distributed publicly.

---

<div align="center">

**Outcome:** a decision-ready fraud investigation that connects behavioral anomalies to shared attacker infrastructure.

</div>
