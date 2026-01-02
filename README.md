# 🛡️ SOC Automation Project: Web Application Defense Lab
![Wazuh](https://img.shields.io/badge/SIEM-Wazuh-blue?style=for-the-badge&logo=wazuh)
![ModSecurity](https://img.shields.io/badge/WAF-ModSecurity-green?style=for-the-badge&logo=apache)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

📄 **[Download Full Lab Report (PDF)](SOC_Lab_Report.pdf)**

---

## 📌 Executive Summary
This project demonstrates the design and implementation of a **Security Operations Center (SOC)** workflow to detect and mitigate web-based cyber threats. The objective was to secure a vulnerable web server against OWASP Top 10 attacks, specifically **SQL Injection (SQLi)**.

The architecture integrates **ModSecurity (WAF)** for network-level filtering and **Wazuh (SIEM)** for centralized log analysis. The project successfully demonstrates the "Attack-Detect-Defend" lifecycle, culminating in the automated blocking of malicious traffic without modifying the application code.

---

## 🏗️ Lab Architecture
The environment uses a Manager-Agent architecture deployed on virtualized infrastructure.

```mermaid
graph TD;
    Attacker[Windows 10 Attacker] -->|SQL Injection Payload| Victim[Ubuntu Server DVWA];
    Victim -->|Apache Logs| ModSec[ModSecurity WAF];
    ModSec -->|Alerts Log Analysis| WazuhAgent[Wazuh Agent];
    WazuhAgent -->|Forwarded Events| WazuhManager[Wazuh SIEM];
    WazuhManager -->|Level 12 Alert| Dashboard[Kibana Dashboard];
