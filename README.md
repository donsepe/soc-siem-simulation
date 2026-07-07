# Multi-Platform Security Operations Center (SOC) & SIEM Lab

## 🔎 Project Overview
This repository documents the end-to-end design, implementation, and management of a hybrid Security Operations Center (SOC) home lab. The environment bridges on-premises virtualization with enterprise cloud architecture to simulate real-world enterprise infrastructure, defensive monitoring, adversary simulation, and automated incident response pipelines.

The primary objective of this lab is to achieve deep operational visibility across multiple operating systems, manage centralized enterprise identity structures, execute controlled attack simulations, and build automated defense mechanisms against modern threat vectors.

---

## 🛠️ Infrastructure & Lab Architecture

### 1. Centralized Logging & SIEM Layer
*   **Splunk Enterprise SIEM:** Deployed as the central analytics engine for log aggregation, custom event parsing, correlation, dashboarding, and threat hunting.
*   **Splunk Universal Forwarders (UF):** Endpoint agents deployed across target workstations, web servers, and domain controllers to securely parse and ship local event streams (Windows Event Logs, Linux Syslog, Apache Web Logs) over port 9997.

### 2. Enterprise Detection & XDR Layer
*   **Azure Cloud Wazuh Deployment:** Orchestrated a cloud-native Wazuh Manager instance hosted on Microsoft Azure to monitor distributed external assets, handling cloud network security groups (NSGs) and agent-manager routing.
*   **Local Wazuh Infrastructure:** Implemented an on-premises Wazuh stack paired with an integrated API framework to test local log parser rules, monitor system integrity (FIM), and track system performance.
*   **Automated Active Response:** Configured the Wazuh engine to dynamically trigger automated remediation scripts—such as firewall drops, connection drops, and IP banning—upon detecting high-severity alerts.

### 3. Identity & Target Network Layer
*   **Active Directory Domain Services (AD DS):** Built a Windows Server domain controller infrastructure managing domain-joined client workstations, organizational units (OUs), group policies (GPOs), and centralized authentication tracking.

---

## ⚔️ Implemented Security Exercises & Adversary Simulations

### 1. Automated Brute-Force Attacks (Hydra)
*   **Adversary Simulation:** Executed high-velocity password guessing attacks against target SSH and RDP endpoints using **Hydra** via a Kali Linux attack platform.
*   **SIEM Visibility & Detection:** Logged thousands of rapid authentication failures. Splunk Universal Forwarders ingested `/var/log/auth.log` and Windows Security Logs, feeding them into Splunk SIEM to build high-fidelity brute-force correlation alerts.
*   **Containment:** Validated both Splunk tracking alerts and Wazuh's automated Active Response mechanisms to drop the malicious attacker IP at the host firewall layer.

### 2. Cross-Site Scripting (XSS) Attacks
*   **Adversary Simulation:** Targeted a web application hosting an unauthenticated, poorly sanitized web form (e.g., Apache2/PHP test environment) to inject malicious JavaScript payloads.
*   **SIEM Visibility & Detection:** Ingested raw Apache web access and error logs (`access.log`) into Splunk. Built custom regex patterns within Splunk to flag common XSS indicators (e.g., `<script>`, `String.fromCharCode`, and encoded URI parameters) targeting the web application.

### 3. Centralized Identity Auditing
*   **Active Directory Monitoring:** Parsed critical Windows security event logs (such as Event ID 4624 for successful logons and Event ID 4625 for failed authentication) to detect credential stuffing or lateral movement.

---

## 🚀 Key Technical Skills Demonstrated
*   **SIEM Engineering:** Configuration of Splunk indexes, custom source typing, forwarding architectures, field extractions, and searching using Splunk Processing Language (SPL).
*   **XDR & EDR Administration:** Creating customized decoders and rulesets in Wazuh, configuring active response thresholds, and managing cloud security nodes.
*   **Adversary Emulation:** Utilizing penetration testing utilities (Hydra, custom XSS scripts) ethically to test and validate defensive security baselines.
*   **Identity Provider Management:** Configuring Active Directory architectures, enforcing security-focused GPOs, and auditing Kerberos/NTLM authentication loops.
*   **Cloud Architecture & Hardening:** Deploying cloud compute instances, designing secure Virtual Networks (VNets), and implementing restrictive Network Security Group (NSG) firewalls.
