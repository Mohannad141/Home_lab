# SOC Analyst Home Lab (SIEM Monitoring & Detection)

## Project Overview
This home lab is a dedicated environment for learning Security Operations Center (SOC) fundamentals, including SIEM administration, endpoint telemetry collection, and threat detection.

The project demonstrates the ability to deploy, configure, and monitor an enterprise-grade SIEM (Splunk Enterprise) to analyze Windows event logs and Sysmon telemetry for malicious activity.

## Technical Architecture
- **Host OS:** Fedora (Linux)
- **Hypervisor:** KVM/QEMU (via Virt-Manager)
- **SIEM Platform:** Splunk Enterprise (on Windows 11 Target)
- **Target Endpoint:** Windows 11 (Telemetry Source)
- **Attack Node:** Kali Linux
- **Log Collection:** Splunk Universal Forwarder, Sysmon, Windows Event Logs

## Lab Setup & Configuration
Detailed step-by-step documentation for each phase of the lab setup:

1. [Phase 1: Networking & Virtualization](./documentation/phase1-network.md) (Completed)
2. [Phase 2: Splunk Installation & Indexing](./documentation/phase2-splunk-install.md) (Completed)
3. [Phase 3: Sysmon & Telemetry Collection](./documentation/phase3-sysmon-config.md) (Completed)
4. [Phase 4: Threat Simulation & Alerting](./documentation/phase4-threat-simulation.md) (Planned)

## Configuration Artifacts
This repository contains the configuration files and scripts used to secure and monitor the lab:
- `/configs/splunk`: Inputs, Props, and Transforms configurations.
- `/configs/sysmon`: Customized Sysmon rule-sets.
- `/scripts`: PowerShell and Bash scripts for log parsing or attack simulation.

## Skills Demonstrated
- **SIEM Management:** Installing, configuring, and querying Splunk Enterprise.
- **Endpoint Monitoring:** Deploying and tuning Sysmon for high-fidelity telemetry.
- **Log Analysis:** Writing SPL (Splunk Processing Language) to identify suspicious patterns.
- **Linux Administration:** Managing KVM/QEMU and host networking on Fedora.
- **Threat Hunting:** Identifying artifacts from common attack vectors (e.g., encoded PowerShell, living-off-the-land binaries).

---
*Note: This project is part of my ongoing learning path in Cybersecurity and SOC Operations.*
