# Fraud Behavior Analysis & Compromised Identity Investigation

## Executive Overview
This project delivers an in depth behavioral and network-based fraud investigation
aimed at identifying compromised identities and devices involved in coordinated
Account Takeover (ATO) attacks across multiple banking environments.

By combining behavioral analytics, network intelligence, and cross-feature integrity
checks, the analysis uncovers evidence of large scale automation, device emulation,
and shared attacker infrastructure.

The outcome is a decision-ready fraud assessment supported by clear evidence and
actionable security recommendations.

---

## Business Problem
Financial institutions face increasingly sophisticated fraud campaigns that bypass
traditional rule-based detection through:
- Rapid IP rotation
- Device fingerprint spoofing
- Emulator-driven automation
- Shared attack infrastructure across accounts and banks

This project addresses the challenge of **connecting the dots** between identities,
devices, IPs, and network attributes to expose coordinated fraud operations.

---

## Objectives
- Identify compromised identities and devices
- Detect non human behavioral patterns
- Uncover shared attacker infrastructure (IP, ASN, Country)
- Consolidate technical evidence into executive-level insights
- Provide actionable fraud mitigation recommendations

---

## Analytical Methodology
The investigation follows a structured, multi-layered approach:

1. **Data Quality & Consistency Checks**  
   Ensuring reliability before advanced analysis.

2. **Behavioral Analysis**  
   - Identity activity patterns  
   - Device reuse and fingerprint anomalies  
   - IP velocity and repetition behavior  

3. **Cross-Feature Integrity Checks**  
   Linking identities, devices, IPs, and banks to identify abnormal overlap.

4. **Network & Geographic Intelligence**  
   Enriching data with ASN, provider, and country-level attributes.

5. **Evidence Consolidation**  
   Translating technical findings into clear fraud indicators.

---

## Key Findings
- A compromised identity accessed multiple banks using **70+ unique IP addresses**
  within a short time frame.
- A single device fingerprint was cloned across **100+ unique device IDs**,
  indicating emulator based automation.
- Fraud activity was heavily concentrated within specific **ASNs and network providers**.
- Both compromised identity and device were traced to the **same country and ASN**,
  confirming shared attacker infrastructure.
- Behavioral patterns strongly indicate scripted, non-human account takeover activity.

---
## Data Availability
Due to data confidentiality and security restrictions, the original dataset
cannot be shared publicly. The provided notebooks focus on demonstrating
the analytical methodology, logic, and investigation process.


## Tools & Libraries
This project leverages specialized Python libraries beyond basic EDA tooling:

- **pandas / numpy** – Data manipulation and analysis  
- **matplotlib / plotly** – Advanced and interactive visualizations  
- **networkx** – Graph based relationship mapping between identities, devices, and IPs  
- **geoip2** – Network and geographic enrichment (Country, ASN, Provider)  

These tools enable deep behavioral correlation and infrastructure-level fraud detection.


