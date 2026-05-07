````markdown
# SENTINEL — SOC Operations Platform

> AI-powered SOC analyst platform designed to simulate real-world security operations workflows including alert triage, threat intelligence analysis, incident investigation, and response execution. :contentReference[oaicite:0]{index=0}

![Version](https://img.shields.io/badge/version-3.0-blue?style=flat-square)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)

---

# Overview

SENTINEL is a browser-based Security Operations Center (SOC) platform built to simulate enterprise-level security workflows used during active investigations.

The platform enables analysts to:
- Triage and prioritize alerts
- Investigate indicators of compromise (IOCs)
- Review threat intelligence
- Map MITRE ATT&CK techniques
- Execute response workflows
- Document incidents
- Simulate SIEM-driven investigations

Anthropic Claude powers AI-assisted investigation summaries and analyst support throughout the alert lifecycle.

---

# Features

## Alert Management
- Real-time alert queue
- Severity-based prioritization
- Risk scoring visualization
- Alert escalation and closure workflows

---

## AI-Assisted Investigations
- AI-generated investigation summaries
- Attacker intent analysis
- Recommended response actions
- Context-aware analyst chat
- MITRE ATT&CK-aware analysis

---

## Threat Intelligence
- VirusTotal integration
- AbuseIPDB integration
- IOC reputation analysis
- IP, domain, URL, and hash investigation
- Bulk IOC analysis support

---

## Investigation Workspace

Each investigation includes:
- Overview
- Threat Intelligence
- Timeline
- Raw Logs
- AI Chat

Additional capabilities:
- Timeline reconstruction
- Playbook execution tracking
- MITRE ATT&CK tagging

---

## SIEM Integration

Supports integration concepts for:
- Splunk
- Elastic SIEM
- Microsoft Sentinel
- IBM QRadar
- Google Chronicle
- Generic JSON webhooks

---

# Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| AI Analysis | Anthropic Claude Sonnet |
| Threat Intelligence | VirusTotal API, AbuseIPDB API |
| Backend | Node.js / Express |
| Deployment | GitHub Pages |

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

Backend proxy responsibilities:
- API key protection
- CORS handling
- External API communication
- AI request routing

---

# Getting Started

## Requirements

- Node.js 18+

---

## Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/sentinel-soc-platform.git
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
ANTHROPIC_API_KEY=YOUR_API_KEY
VIRUSTOTAL_API_KEY=YOUR_API_KEY
ABUSEIPDB_API_KEY=YOUR_API_KEY
PORT=3000
```

---

## Start Backend Proxy

```bash
npm start
```

---

## Open Dashboard

```text
http://localhost:3000
```

---

# SIEM Webhook Example

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
6. Execute Response Workflow
7. Document Findings
8. Escalate or Close Incident
```

---

# MITRE ATT&CK Coverage

| Technique | ID |
|---|---|
| Credential Stuffing | T1110.004 |
| Valid Accounts | T1078 |
| Pass the Hash | T1550.002 |
| Data Encrypted for Impact | T1486 |
| DNS Command and Control | T1071.004 |

---

# Roadmap

- [ ] Campaign correlation engine
- [ ] Sigma/KQL rule generation
- [ ] Analyst performance tracking
- [ ] PDF incident report exports
- [ ] Dark mode support

---

# Security Notes

Never upload:
- `.env` files
- API keys
- Real customer logs
- Sensitive IOC datasets

Recommended `.gitignore`:

```gitignore
.env
node_modules/
.DS_Store
dist/
*.log
```

---

# License

MIT License

---

# Contact

**Jarius Glover**  
SOC Operations | Threat Analysis | Incident Response

- LinkedIn: linkedin.com/in/jariusglover1
- GitHub: github.com/YOUR_USERNAME

---

> *“The best analysts don’t just close alerts — they understand attacks.”*
````
