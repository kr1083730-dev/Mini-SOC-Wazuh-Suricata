# Mini-SOC Implementation (Wazuh + Suricata)

## Overview
This repository contains the implementation details, configuration files, and proof-of-work for my Undergraduate Research Experience (URE) project: **"Implementing a Mini-SOC Using Wazuh and Suricata for Early Detection and Analysis of Network Security Incidents."**

## Architecture
- **SOC Server:** Ubuntu Server 26.04 LTS (Wazuh Manager, Wazuh Indexer, Wazuh Dashboard, Suricata)
- **Attacker Node:** Kali Linux (Simulating network reconnaissance)

## How it Works
1. **Suricata** monitors the network interface (`ens33`) for malicious traffic using 69,000+ ET Open rules.
2. **Wazuh Manager** ingests the `eve.json` logs from Suricata using a custom decoder.
3. **Filebeat** securely ships the alerts to the **Wazuh Indexer** using SSL/TLS certificates.
4. **Wazuh Dashboard** visualizes the alerts for the SOC Analyst in real-time.

## Test Results
A simulated Nmap scan (`nmap -sS -A`) was launched from the Kali machine. The system successfully detected the reconnaissance and logged hundreds of security events on the dashboard.

![Wazuh Dashboard](Screenshot%202026-10-19%20114234.png)

## Configuration Files Included
- `ossec.conf`: Wazuh Manager configuration for ingesting Suricata logs.
- `local_rules.xml`: Custom Wazuh rules for parsing Suricata alerts.
- `filebeat.yml`: Filebeat configuration for shipping logs securely to the Indexer.

## Author
**Anusha Ashok Goudar**  
B.Tech Cyber Security  
[Your University Name]
