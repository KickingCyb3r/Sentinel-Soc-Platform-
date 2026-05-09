[soc-analyst-v3.html](https://github.com/user-attachments/files/27500707/soc-analyst-v3.html)
# SENTINEL — Tier 1 SOC Analyst Platform

> AI-powered SOC analyst dashboard built to simulate real-world Tier 1 security operations workflows including alert triage, threat intelligence analysis, incident investigation, and response execution. 

![Version](https://img.shields.io/badge/version-3.0-blue?style=flat-square)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)
![AI](https://img.shields.io/badge/AI-Claude%20Sonnet-purple?style=flat-square)

---

# Overview

SENTINEL is a browser-based SOC analyst workstation designed to mirror enterprise Security Operations Center workflows.

The platform allows analysts to:

* Triage and prioritize alerts
* Investigate indicators of compromise (IOCs)
* Review threat intelligence
* Map MITRE ATT&CK techniques
* Execute response playbooks
* Document incidents
* Simulate SIEM-driven investigations

Anthropic Claude powers AI-assisted investigation summaries and analyst support throughout the alert lifecycle.

---

# Features

## Alert Console

* Real-time alert queue
* Severity-based prioritization
* Risk scoring visualization
* Alert lifecycle management
* False positive dismissal
* Escalation tracking

---

## AI-Assisted Investigation

* AI-generated investigation summaries
* Attacker intent analysis
* Recommended response actions
* Context-aware analyst chat
* MITRE ATT&CK-aware analysis

---

## Threat Intelligence

* VirusTotal integration
* AbuseIPDB integration
* IOC reputation analysis
* Threat scoring and detection visibility
* IP, domain, URL, and hash investigation
* Bulk IOC analysis

---

## Investigation Workspace

Each alert includes:

* Overview
* Threat Intel
* Timeline
* Raw Logs
* AI Chat

Additional capabilities:

* Timeline reconstruction
* Dwell time visibility
* Playbook execution tracking
* MITRE ATT&CK tagging

---

## SIEM Integration

Supports webhook integration concepts for:

* Splunk
* Elastic SIEM
* Microsoft Sentinel
* IBM QRadar
* Google Chronicle
* Generic JSON webhooks

---

# Tech Stack

| Layer               | Technology                    |
| ------------------- | ----------------------------- |
| Frontend            | HTML, CSS, JavaScript         |
| AI Analysis         | Anthropic Claude Sonnet       |
| Threat Intelligence | VirusTotal API, AbuseIPDB API |
| Backend             | Node.js / Express             |
| Deployment          | GitHub Pages                  |

---

# Architecture

```text
Browser Dashboard
│
├── Alert Queue
├── AI Analysis Module
├── Threat Intelligence Module
└── SIEM Integration Layer
```

The backend proxy handles:

* API key security
* CORS management
* External API communication
* AI request routing

---

# Getting Started

## Option 1 — UI Only

Download the HTML file and open it in your browser.

Available features:

* Alert queue
* Threat investigation workflows
* Timeline analysis
* Playbook tracking
* SIEM simulation

AI functionality requires backend API integration.

---

## Option 2 — Full Functionality

### Requirements

* Node.js 18+

---

## Clone Repository

```bash
git clone https://github.com/KickingCyb3r/Sentinel-Soc-Platform-.git
cd sentinel-soc-platform
```

---

## Install Dependencies

```bash
cd proxy
npm install
```

---

## Configure Environment Variables

```bash
cp .env.example .env
```

Example:

```env
ANTHROPIC_API_KEY=your_key_here
VIRUSTOTAL_API_KEY=your_key_here
ABUSEIPDB_API_KEY=your_key_here
PORT=3000
```

---

## Start Proxy Server

```bash
npm start
```

---

## Open Dashboard

```text
http://localhost:3000
```

---

# SIEM Webhook Format

Example webhook payload:

```json
{
  "alert_id": "ALT-2024-001",
  "severity": "HIGH",
  "source": "Splunk",
  "host": "finance-server-01",
  "src_ip": "192.168.1.50",
  "user": "jdoe",
  "action": "BLOCKED",
  "mitre": ["T1078"],
  "raw_log": "sample log data"
}
```

---

# Investigation Workflow

```text
1. Review Alert Queue
2. Prioritize Risk
3. Investigate Alert
4. Analyze Threat Intelligence
5. Review Timeline & Logs
6. Execute Response Playbook
7. Document Findings
8. Escalate or Close Incident
```

---

# MITRE ATT&CK Coverage

| Technique                 | ID        |
| ------------------------- | --------- |
| Credential Stuffing       | T1110.004 |
| Valid Accounts            | T1078     |
| Pass the Hash             | T1550.002 |
| Data Encrypted for Impact | T1486     |
| DNS Command and Control   | T1071.004 |

---

# Project Background

SENTINEL was built as a hands-on cybersecurity portfolio project focused on:

* SOC operations
* Threat analysis
* Incident response
* SIEM workflows
* AI-assisted investigations

The platform demonstrates practical Tier 1 SOC analyst capabilities and enterprise-style security operations workflows.

---

# Roadmap

* [ ] Campaign correlation engine
* [ ] Sigma/KQL rule generation
* [ ] Analyst performance tracking
* [ ] PDF incident report exports
* [ ] Dark mode support

---

# License

MIT License

Free to use, modify, and distribute with attribution.

---

# Contact

**Jarius Glover**
Cybersecurity | SOC Operations | Threat Analysis

* LinkedIn: `linkedin.com/in/jariusglover1`
* GitHub: `git clone https://github.com/KickingCyb3r/Sentinel-Soc-Platform-.git`

---

> *“The best analysts don’t just close alerts — they understand attacks.”*
