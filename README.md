# Hybrid Microsoft Sentinel SOC Detection & Response Laboratory

## Project Structure

The repository is organized around security domains, detection engineering, incident investigations, and response activities.

```
Hybrid-SOC-Microsoft-Sentinel-Lab
│
├── README.md
│
├── Architecture
│   │
│   ├── SOC-Lab-Architecture.md
│   ├── Network-Diagram.png
│   └── Data-Flow-Diagram.png
│
├── Investigation-Reports
│   │
│   ├── Phishing
│   │   │
│   │   └── 01-Phishing-Email-Investigation.md
│   │
│   ├── Authentication-Attacks
│   │   │
│   │   └── 02-Brute-Force-Attack-Investigation.md
│   │
│   ├── Web-Attacks
│   │   │
│   │   ├── 03-SQL-Injection-Investigation.md
│   │   ├── 04-Cross-Site-Scripting-XSS-Investigation.md
│   │   ├── 05-Command-Injection-Investigation.md
│   │   ├── 06-Suspicious-File-Upload-Investigation.md
│   │   ├── 07-Path-Traversal-Investigation.md
│   │   ├── 08-Directory-Enumeration-Investigation.md
│   │   └── 09-SSRF-Investigation.md
│   │
│   ├── Endpoint-Attacks
│   │   │
│   │   ├── 10-Malware-Execution-Investigation.md
│   │   ├── 11-PowerShell-Abuse-Investigation.md
│   │   ├── 12-Process-Injection-Investigation.md
│   │   └── 13-Persistence-Investigation.md
│   │
│   ├── Network-Attacks
│   │   │
│   │   ├── Port-Scanning-Investigation.md
│   │   ├── Suspicious-Network-Connection.md
│   │   └── Command-and-Control-Investigation.md
│   │
│   └── Cloud-Attacks
│       │
│       ├── Azure-Identity-Attack-Investigation.md
│       └── Suspicious-Cloud-Activity-Investigation.md
│
├── Detection-Rules
│   │
│   ├── Web-Attacks
│   │   │
│   │   ├── SQL-Injection.kql
│   │   ├── XSS.kql
│   │   ├── Command-Injection.kql
│   │   ├── File-Upload-Abuse.kql
│   │   ├── Path-Traversal.kql
│   │   ├── Directory-Enumeration.kql
│   │   └── SSRF.kql
│   │
│   ├── Authentication-Attacks
│   │   │
│   │   ├── Brute-Force.kql
│   │   ├── Failed-Login-Spike.kql
│   │   └── Suspicious-Authentication.kql
│   │
│   ├── Endpoint-Detection
│   │   │
│   │   ├── Malware-Execution.kql
│   │   ├── PowerShell-Abuse.kql
│   │   ├── Process-Creation.kql
│   │   └── Persistence-Detection.kql
│   │
│   ├── Windows-Detection
│   │   │
│   │   ├── Suspicious-Logon.kql
│   │   ├── PowerShell-Execution.kql
│   │   ├── Registry-Persistence.kql
│   │   └── Credential-Dumping.kql
│   │
│   └── Linux-Detection
│       │
│       ├── SSH-Brute-Force.kql
│       ├── Privilege-Escalation.kql
│       └── Suspicious-Command-Execution.kql
│
├── Images
│   │
│   ├── 01-Phishing
│   │   ├── email-analysis.png
│   │   ├── defender-alert.png
│   │   └── process-tree.png
│   │
│   ├── 02-Brute-Force
│   │   ├── incident.png
│   │   ├── failed-login.png
│   │   ├── successful-login.png
│   │   └── threat-intelligence.png
│   │
│   ├── 03-SQL-Injection
│   │   ├── sentinel-alert.png
│   │   ├── nginx-evidence.png
│   │   ├── zeek-evidence.png
│   │   └── suricata-evidence.png
│   │
│   ├── 04-XSS
│   │   ├── sentinel-alert.png
│   │   ├── nginx-evidence.png
│   │   ├── zeek-evidence.png
│   │   └── suricata-evidence.png
│   │
│   ├── 05-Command-Injection
│   │   ├── sentinel-alert.png
│   │   ├── nginx-evidence.png
│   │   ├── zeek-evidence.png
│   │   └── suricata-evidence.png
│   │
│   └── 06-File-Upload
│       ├── sentinel-alert.png
│       ├── nginx-evidence.png
│       ├── zeek-evidence.png
│       └── suricata-evidence.png
│
├── SOAR-Playbooks
│   │
│   ├── IP-Blocking.md
│   ├── Malware-Isolation.md
│   ├── Phishing-Response.md
│   └── Incident-Response-Workflow.md
│
├── Threat-Hunting
│   │
│   ├── IOC-Hunting.md
│   ├── MITRE-Technique-Hunting.md
│   └── Threat-Hunting-Queries.md
│
└── Documentation
```



## Platform & Tools

The SOC laboratory was built using:
- Microsoft Sentinel – SIEM platform for log ingestion, detection engineering, alerting, and investigation.
- Microsoft Defender XDR – Endpoint detection, incident correlation, and threat investigation.
- Azure Log Analytics Workspace – Centralized security telemetry storage.
- Kusto Query Language (KQL) – Detection rules and threat hunting queries.
- Microsoft Defender for Endpoint – Endpoint telemetry and malware investigation.
- Zeek – Network security monitoring and HTTP/DNS/connection telemetry.
- Suricata IDS – Network intrusion detection and threat signatures.
- Nginx Logs – Web application access monitoring.
- OWASP Juice Shop – Vulnerable web application used for attack simulation.
- Kali Linux – Security testing and attack simulation environment.
- Ubuntu Linux – Web server and security monitoring sensor.
