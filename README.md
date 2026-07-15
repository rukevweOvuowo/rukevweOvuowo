# Hybrid Microsoft Sentinel SOC Detection & Response Laboratory

![SOC Architecture](Architecture/soc-architecture.png)

## Overview

This project documents the design and implementation of a hybrid Security Operations Center (SOC) laboratory built around Microsoft Sentinel, Microsoft Defender XDR, endpoint telemetry, network monitoring, and security automation.

The purpose of this lab was to simulate an enterprise SOC environment where security analysts can:

- Collect and analyze security telemetry
- Monitor endpoint and network activity
- Detect adversary behavior
- Investigate security incidents
- Develop KQL-based detection rules
- Automate response workflows using SOAR capabilities

The environment combines Azure cloud services with VMware-based security monitoring infrastructure to replicate a hybrid enterprise security architecture.

---

# Architecture

![SOC Architecture](Architecture/soc-architecture.png)

## Environment Components

## SIEM Platform

### Microsoft Sentinel

Microsoft Sentinel is used as the central SIEM platform for:

- Security event collection
- Analytics rules
- Incident management
- Threat hunting
- Investigation workflows
- KQL-based detections

---

# Endpoint Security

## Microsoft Defender XDR

Provides centralized visibility and correlation across security data sources.

Capabilities:

- Endpoint threat detection
- Alert correlation
- Incident investigation
- Device timeline analysis


## Microsoft Defender for Endpoint

Deployed on Windows and Linux endpoints to provide:

- Endpoint Detection and Response (EDR)
- Security alerts
- Device investigation
- Threat visibility


## Sysmon

Sysmon is deployed on Windows endpoints to provide additional telemetry:

- Process creation events
- Network connections
- File creation activity
- Registry modifications
- System activity monitoring

---

# Network Security Monitoring

## Zeek

Zeek provides network visibility through analysis of:

- Network connections
- HTTP activity
- DNS queries
- Communication patterns


## Suricata

Suricata provides network intrusion detection through:

- Signature-based detection
- Suspicious traffic identification
- IDS alerts

---

# Lab Architecture

```
                         INTERNET
                            |
                            |
                    Microsoft Azure Cloud
                            |
        ------------------------------------------------
        |                                              |
 Microsoft Sentinel                         Microsoft Defender XDR
        |                                              |
 Log Analytics Workspace                         Endpoint Telemetry
        |
        |
 Azure Monitor Agent
        |
        |
 Data Collection Rules (DCR)
        |
        |
 -------------------------------------------------------
        |
        |
                VMware Environment
                      |
                Local Network
                      |
        --------------------------------
        |              |               |
        |              |               |

     Kali Linux    Ubuntu Sensor    Windows 10
     Attacker      Zeek/Suricata    Endpoint

                    |
                    |
             Network Telemetry

                    |
                    |
              Microsoft Sentinel
```

---

# Telemetry Collection Flow

## Azure Windows Endpoint

```
Azure Windows VM

        |

Microsoft Defender for Endpoint

        |

Microsoft Defender XDR

        |

Microsoft Sentinel
```


## Windows 10 Endpoint

```
Windows 10 VM

        |

Defender for Endpoint
        |
        |
Sysmon Telemetry

        |

Azure Monitor Agent

        |

Microsoft Sentinel
```


## Ubuntu Security Sensor

Network monitoring:

```
Network Traffic

        |

Zeek + Suricata

        |

Azure Monitor Agent

        |

Data Collection Rule

        |

Log Analytics Workspace

        |

Microsoft Sentinel
```

---

# Attack Simulation

The environment was tested using controlled adversary simulations to validate detection capabilities.

---

# 1. Network Reconnaissance

## Tool

- Nmap


## Activity

Performed network discovery and service enumeration against monitored endpoints.

Example:

```bash
nmap -sV <target-ip>
```


## Detection Sources

- Zeek connection logs
- Suricata alerts
- Microsoft Sentinel analytics rules


---

# 2. Web Application Attacks

## Target

OWASP Juice Shop


## Activities

- SQL injection testing
- HTTP attack simulation


## Detection Sources

- Zeek HTTP logs
- Suricata IDS alerts
- Sentinel investigations


---

# 3. Authentication Attacks

## Activities

- Brute-force authentication attempts
- Failed login simulations


## Detection Sources

- Windows Security Events
- Microsoft Defender telemetry
- Sentinel analytics rules


---

# 4. Endpoint Security Testing

## Activities

- Suspicious PowerShell execution
- Malicious process simulation


## Detection Sources

- Sysmon events
- Defender XDR alerts
- Sentinel incidents


---

# Detection Engineering

Custom Microsoft Sentinel analytics rules were developed using KQL to identify suspicious activities across endpoint, authentication, and network telemetry.

Detection examples:

---

## Network Reconnaissance Detection

Detects:

- Port scanning activity
- Suspicious connection patterns


Data Sources:

- Zeek
- Suricata


---

## Brute Force Detection

Detects:

- Multiple failed authentication attempts
- Potential credential attacks


Data Sources:

- Windows Security Events
- Microsoft Sentinel


---

## Suspicious PowerShell Detection

Detects:

- Suspicious PowerShell execution
- Encoded commands
- Abnormal command-line activity


Data Sources:

- Sysmon
- Defender XDR


---

# SOAR Automation

Microsoft Sentinel automation workflows were developed using Azure Logic Apps.

Automation workflows include:

- Incident notification
- Alert enrichment
- Investigation support
- Response workflow automation


Workflow:

```
Sentinel Alert

      |

Analytics Rule Trigger

      |

Automation Rule

      |

Logic App Playbook

      |

Notification / Enrichment

      |

Investigation Workflow
```

---

# Incident Investigation Workflow

Security incidents were investigated using a structured SOC workflow:

```
Alert Generated

        |

Alert Validation

        |

Evidence Collection

        |

Telemetry Correlation

        |

Attack Timeline Reconstruction

        |

MITRE ATT&CK Mapping

        |

Response Actions

        |

Incident Documentation
```


Investigation sources:

- Microsoft Sentinel incidents
- Microsoft Defender XDR
- Sysmon events
- Zeek logs
- Suricata alerts
- Authentication logs

---

# MITRE ATT&CK Coverage

| Technique | Activity |
|---|---|
| T1046 | Network Service Scanning |
| T1110 | Brute Force |
| T1059.001 | PowerShell |
| T1190 | Exploit Public-Facing Application |
| T1071 | Application Layer Protocol |

---

# Repository Structure

```
Hybrid-SOC-Microsoft-Sentinel-Lab

│
├── README.md
│
├── Architecture
│   ├── soc-architecture.png
│   └── telemetry-flow.png
│
├── Attack-Simulation
│   ├── reconnaissance.md
│   ├── brute-force.md
│   ├── sql-injection.md
│   └── powershell.md
│
├── Detection-Rules
│   ├── nmap-detection.kql
│   ├── brute-force-detection.kql
│   ├── powershell-detection.kql
│   └── sysmon-detection.kql
│
├── SOAR-Playbooks
│   ├── alert-enrichment.md
│   └── notification-workflow.md
│
├── Investigation-Reports
│   ├── incident-001.md
│   └── incident-002.md
│
├── MITRE-Mapping
│   └── techniques.md
│
└── Screenshots
    ├── sentinel-dashboard.png
    ├── defender-alerts.png
    ├── zeek-logs.png
    └── suricata-alerts.png
```

---

# Skills Demonstrated

- Microsoft Sentinel Administration
- Microsoft Defender XDR Investigation
- Microsoft Defender for Endpoint
- KQL Detection Engineering
- SOC Alert Triage
- Incident Investigation
- Threat Hunting
- Sysmon Analysis
- Zeek Network Monitoring
- Suricata IDS Analysis
- SOAR Automation with Azure Logic Apps
- MITRE ATT&CK Mapping


---

# Author

**Ovuowo Rukevwe**

Cybersecurity | SOC Analyst | Detection Engineering


LinkedIn:

https://linkedin.com/in/rukevwe-ovuowo
