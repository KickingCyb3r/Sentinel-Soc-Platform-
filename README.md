# Sentinel-Soc-Platform-
# SENTINEL ‚Äî Tier 1 SOC Analyst Platform

> An AI-powered Security Operations Center dashboard built for Tier 1 analysts. Covers the full alert investigation lifecycle ‚Äî from triage and threat intelligence to containment and documentation.

![Platform Version](https://img.shields.io/badge/version-3.0-blue?style=flat-square)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)
![AI Powered](https://img.shields.io/badge/AI-Claude%20Sonnet-purple?style=flat-square)

---

## Overview

SENTINEL is a fully functional Tier 1 SOC analyst workstation built as a single-file web application. It simulates the core workflows of an enterprise Security Operations Center ‚Äî alert triage, threat intelligence lookups, incident investigation, and response playbook execution ‚Äî powered by the Anthropic Claude API for real-time AI analysis.

Built as a portfolio project during a cybersecurity career transition, it demonstrates hands-on understanding of SOC operations, SIEM workflows, MITRE ATT&CK mapping, and incident response procedures.

---

## Live Demo

**[View Live Dashboard ‚Üí](https://yourusername.github.io/sentinel-soc-platform/soc-analyst-v3.html)**

> Note: AI analysis features require an Anthropic API key routed through a backend proxy. All other features ‚Äî alert queue, IOC display, playbook tracking, timeline, and SIEM simulation ‚Äî are fully functional without an API key.

---

## Features

### Alert Console
- Real-time alert queue with severity-based triage (Critical / High / Medium / Low)
- Color-coded severity strips, risk score bars, and new alert indicators
- Five-metric dashboard bar: active critical/high counts, mean time to respond, closed today, false positive rate
- Alert lifecycle management: Dismiss (false positive), Escalate (Tier 2), Close (resolved)

### AI-Powered Investigation
- Automated triage analysis using Claude Sonnet ‚Äî summarizes what is happening, likely attacker intent, and recommended action
- Context-aware AI chat for free-form analyst queries during active investigations
- Generates analysis scoped to the specific alert context including MITRE techniques, risk score, and host/user data

### Auto-Triage Scoring Engine
- Multi-factor AI scoring across 6 dimensions: Threat Intel, Kill Chain Stage, Asset Criticality, Velocity, IOC Confidence, MITRE Coverage
- Ranked card grid with per-factor score bars and recommended actions
- Priority scores persist in the alert queue as visual score bars
- Click any triage card to jump directly into investigation

### Threat Intelligence Integration
- Per-IOC lookup against VirusTotal and AbuseIPDB (real API keys optional ‚Äî AI simulation used otherwise)
- Returns verdict, threat score, detection count, geo/ASN data, threat families, and tags
- Bulk IOC lookup runs all indicators in the current alert simultaneously
- Standalone indicator lookup for arbitrary IPs, domains, hashes, and URLs

### SIEM / Webhook Integration
- Connect Splunk, Elastic SIEM, Microsoft Sentinel, IBM QRadar, Google Chronicle, or any generic JSON webhook
- Live alert feed simulation with automatic queue injection
- Configurable webhook payload schema for real SIEM integration
- Connection status indicators per source

### Investigation Workflow
- Five-tab investigation workspace per alert: Overview, Threat Intel, Timeline, Raw Log, AI Chat
- MITRE ATT&CK technique tagging with kill chain stage awareness
- Event timeline with severity-classified entries and dwell time visibility
- Raw log viewer with syntax-highlighted output
- Interactive response playbook with step-by-step completion tracking

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML / CSS / JavaScript ‚Äî zero dependencies |
| AI Analysis | Anthropic Claude Sonnet (`claude-sonnet-4-20250514`) |
| Threat Intel | VirusTotal API v3, AbuseIPDB API v2 |
| Typography | Syne (display), DM Mono (monospace), DM Sans (body) |
| Fonts | Google Fonts CDN |
| Deployment | GitHub Pages (static) |

---

## Architecture

```
Browser (Dashboard)
‚îÇ
‚îú‚îÄ‚îÄ Alert Queue ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ Static alert data (SIEM-injected in production)
‚îÇ
‚îú‚îÄ‚îÄ AI Analysis Module ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ POST /v1/messages ‚Üí Anthropic API
‚îÇ   ‚îú‚îÄ‚îÄ Triage Analysis                    (requires backend proxy in production)
‚îÇ   ‚îú‚îÄ‚îÄ Auto-Triage Scoring Engine
‚îÇ   ‚îî‚îÄ‚îÄ AI Chat
‚îÇ
‚îú‚îÄ‚îÄ Threat Intel Module ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ GET ‚Üí VirusTotal API v3
‚îÇ   ‚îú‚îÄ‚îÄ Single IOC Lookup                  GET ‚Üí AbuseIPDB API v2
‚îÇ   ‚îî‚îÄ‚îÄ Bulk IOC Lookup                    (AI simulation fallback)
‚îÇ
‚îî‚îÄ‚îÄ SIEM Integration ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ‚îÄ POST ‚Üí Configured webhook endpoints
    ‚îú‚îÄ‚îÄ Live feed simulation
    ‚îî‚îÄ‚îÄ Alert queue injection
```

> **Production Note:** The Anthropic API and third-party threat intel APIs require a backend proxy to handle CORS restrictions and keep API keys server-side. See the Backend Proxy section below for a Node.js implementation.

---

## Getting Started

### Option 1 ‚Äî Open directly (no AI features)

Download `soc-analyst-v3.html` and open it in any modern browser. All UI features, alert simulation, playbook tracking, and SIEM feed simulation work immediately. AI features return a connectivity error without a proxy.

### Option 2 ‚Äî Run with backend proxy (full features)

**Prerequisites:** Node.js 18+

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/sentinel-soc-platform.git
cd sentinel-soc-platform
```

**2. Install proxy dependencies**
```bash
cd proxy
npm install
```

**3. Create your environment file**
```bash
cp .env.example .env
```

Edit `.env` and add your API keys:
```
ANTHROPIC_API_KEY=your_key_here
VIRUSTOTAL_API_KEY=your_key_here
ABUSEIPDB_API_KEY=your_key_here
PORT=3000
```

**4. Start the proxy server**
```bash
npm start
```

**5. Open the dashboard**

Navigate to `http://localhost:3000` in your browser. All AI and threat intel features are now fully functional.

---

## Backend Proxy (Node.js)

The proxy server handles API key security and CORS resolution. A minimal implementation:

```javascript
// proxy/server.js
const express = require('express');
const cors    = require('cors');
const fetch   = require('node-fetch');
require('dotenv').config();

const app = express();
app.use(cors({ origin: '*' }));
app.use(express.json());
app.use(express.static('../'));

// Anthropic proxy
app.post('/api/anthropic', async (req, res) => {
  try {
    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: {
        'Content-Type':         'application/json',
        'x-api-key':            process.env.ANTHROPIC_API_KEY,
        'anthropic-version':    '2023-06-01'
      },
      body: JSON.stringify(req.body)
    });
    const data = await response.json();
    res.json(data);
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

// VirusTotal proxy
app.get('/api/virustotal/:indicator', async (req, res) => {
  try {
    const response = await fetch(
      `https://www.virustotal.com/api/v3/ip_addresses/${req.params.indicator}`,
      { headers: { 'x-apikey': process.env.VIRUSTOTAL_API_KEY } }
    );
    res.json(await response.json());
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

// AbuseIPDB proxy
app.get('/api/abuseipdb/:ip', async (req, res) => {
  try {
    const response = await fetch(
      `https://api.abuseipdb.com/api/v2/check?ipAddress=${req.params.ip}&maxAgeInDays=90`,
      { headers: { 'Key': process.env.ABUSEIPDB_API_KEY, 'Accept': 'application/json' } }
    );
    res.json(await response.json());
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

app.listen(process.env.PORT || 3000, () => {
  console.log(`Proxy running on port ${process.env.PORT || 3000}`);
});
```

---

## SIEM Webhook Integration

SENTINEL accepts incoming alerts via webhook in the following JSON format:

```json
{
  "alert_id":  "ALT-2024-XXX",
  "name":      "Alert display name",
  "severity":  "CRITICAL | HIGH | MEDIUM | LOW",
  "source":    "Splunk | Elastic | Sentinel | QRadar",
  "host":      "affected-hostname",
  "src_ip":    "source IP address",
  "dest_ip":   "destination IP address",
  "user":      "affected username",
  "action":    "BLOCKED | DETECTED | CONTAINED | MONITORING",
  "mitre":     ["T1190", "T1078"],
  "raw_log":   "raw log string from source system"
}
```

Supported SIEM platforms: Splunk Enterprise/Cloud, Elastic SIEM, Microsoft Sentinel, IBM QRadar, Google Chronicle, generic JSON webhook.

---

## Alert Investigation Workflow

The platform follows the standard Tier 1 SOC investigation lifecycle:

```
1. Orient        ‚Üí  Read metric bar ‚Äî threat level, active critical/high counts, mean TTR
2. Triage        ‚Üí  Scan alert queue ‚Äî severity, score bars, new alert indicators
3. Auto-Score    ‚Üí  Run Triage Engine ‚Äî AI ranks all alerts by multi-factor risk score
4. Investigate   ‚Üí  Open alert ‚Äî read AI analysis, risk gauge, MITRE techniques
5. Threat Intel  ‚Üí  Lookup IOCs ‚Äî verdict, threat score, geo, families, tags
6. Timeline      ‚Üí  Walk event chain ‚Äî establish kill chain and dwell time
7. Raw Log       ‚Üí  Verify ground truth ‚Äî read log fields directly
8. Playbook      ‚Üí  Execute response steps ‚Äî track completion
9. AI Chat       ‚Üí  Query analyst AI ‚Äî blast radius, escalation decision, case notes
10. Disposition  ‚Üí  Dismiss / Escalate / Close ‚Äî with documented reasoning
```

---

## MITRE ATT&CK Coverage

Alerts in this platform map to the following ATT&CK techniques:

| Technique | ID | Tactic |
|---|---|---|
| Credential Stuffing | T1110.004 | Credential Access |
| Valid Accounts | T1078 | Initial Access / Persistence |
| Exploit Public-Facing Application | T1190 | Initial Access |
| Data Encrypted for Impact | T1486 | Impact |
| Inhibit System Recovery | T1490 | Impact |
| Impair Defenses | T1562.001 | Defense Evasion |
| Pass the Hash | T1550.002 | Lateral Movement |
| Remote Services: SMB | T1021.002 | Lateral Movement |
| Exfiltration Over Alternative Protocol | T1048 | Exfiltration |
| Application Layer Protocol: DNS | T1071.004 | Command and Control |
| Abuse Elevation Control: Sudo | T1548.003 | Privilege Escalation |
| Data from Cloud Storage | T1530 | Collection |
| Transfer Data to Cloud Account | T1537 | Exfiltration |

---

## Project Background

This platform was built as part of **Operation Breakthrough 2026** ‚Äî a structured cybersecurity career transition program targeting SOC Analyst, IAM Analyst, and GRC Analyst roles. It demonstrates practical Tier 1 SOC competencies including:

- Alert triage and prioritization methodology
- MITRE ATT&CK framework application
- Threat intelligence analysis and IOC investigation
- Incident response playbook execution
- SIEM integration architecture
- AI-assisted security analysis workflows

---

## Roadmap

- [ ] Backend proxy server with full API integration
- [ ] Campaign correlation engine ‚Äî link related alerts into incidents
- [ ] Detection rule builder ‚Äî generate Sigma/KQL from investigation findings
- [ ] Analyst performance metrics ‚Äî personal TTR tracking and false positive rate
- [ ] Export to PDF ‚Äî generate formal incident reports
- [ ] Dark/light theme toggle

---

## License

MIT License ‚Äî free to use, modify, and distribute with attribution.

---

## Contact

Built by **Jarius** ‚Äî cybersecurity professional in transition targeting SOC and security operations roles.

- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)

---

*"The best analysts don't just close alerts ‚Äî they understand attacks."*

