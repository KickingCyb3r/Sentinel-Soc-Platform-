[soc-analyst-v3.html](https://github.com/user-attachments/files/27499687/soc-analyst-v3.html)
# Sentinel-Soc-Platform-
SENTINEL — Tier 1 SOC Analyst Platform
An AI-powered SOC dashboard built for Tier 1 analysts. SENTINEL simulates real-world alert investigation workflows including triage, threat intelligence analysis, containment, and incident documentation.

Overview
•	SENTINEL is a browser-based SOC analyst workstation designed to simulate enterprise security operations workflows.
•	The platform allows analysts to investigate alerts, review threat intelligence, map MITRE ATT&CK techniques, execute response playbooks, and document incidents from a centralized dashboard.
•	The project demonstrates practical SOC analyst skills including alert triage, threat intelligence analysis, incident investigation, MITRE ATT&CK mapping, SIEM integration concepts, and AI-assisted security operations.


Features
•	Real-time alert queue with severity-based prioritization
•	AI-generated alert summaries and attacker intent analysis
•	IOC lookups using VirusTotal and AbuseIPDB
•	Investigation workspace with timelines, logs, and AI chat
•	Response playbook tracking and analyst workflow simulation
•	SIEM integration concepts for Splunk, Elastic, Microsoft Sentinel, QRadar, and Chronicle


Tech Stack
•	Frontend: HTML, CSS, JavaScript
•	AI Analysis: Anthropic Claude Sonnet
•	Threat Intelligence: VirusTotal API, AbuseIPDB API
•	Backend Proxy: Node.js / Express
•	Deployment: GitHub Pages


Architecture
•	Browser Dashboard
•	Alert Queue
•	AI Analysis Module
•	Threat Intelligence Module
•	SIEM Integration Layer
Getting Started
•	Download the HTML file and open it in a browser for UI-only functionality.
•	Use a Node.js backend proxy with API keys for full AI and threat intelligence features.
•	Configure environment variables for Anthropic, VirusTotal, and AbuseIPDB integrations.

SOC Investigation Workflow
•	Review Alert Queue
•	Prioritize Risk
•	Investigate Alert
•	Analyze Threat Intelligence
•	Review Timeline and Logs
•	Execute Response Playbook
•	Document Findings
•	Escalate or Close Incident

MITRE ATT&CK Coverage
•	Credential Stuffing — T1110.004
•	Valid Accounts — T1078
•	Pass the Hash — T1550.002
•	Data Encrypted for Impact — T1486
•	DNS Command and Control — T1071.004

Roadmap
•	Campaign correlation engine
•	Sigma/KQL rule generation
•	Analyst performance tracking
•	PDF incident report exports
•	Dark mode support

Project Background
•	SENTINEL was built as part of a cybersecurity development initiative focused on SOC operations, threat analysis, and incident response workflows.
•	The platform demonstrates practical experience with alert triage, SIEM workflows, threat intelligence, and AI-assisted investigations.

Contact
•	Built by Jarius Glover
•	LinkedIn: linkedin.com/in/jariusglover1
“The best analysts don’t just close alerts — they understand attacks.”
