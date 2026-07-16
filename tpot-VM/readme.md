## Honeypot deployed in Oracle Cloud with T-Pot Honeypot

Threat intelligence project using open-source project T-Pot Honeypot installed in an Ubuntu Platform hosted in Oracle Cloud. This projects simulates exposed enterprise systems to collect intelligence on real-world malicious actor's TTPs.

These information can be useful to analyze current security posture of systems.

## 🛠️ Infra and Tech
* **Cloud** Oracle Cloud Infrastructure provisioned in SG
* **Server OS** Ubuntu 22.04
* **Honeypot Tool** T-Pot, multi-honeypot architecture
* **Analysis Tools** Elastic Stack (Elasticsearch, Logstash & Kibana)
* **Exposed Sensors** Cowrie (SSH & Telnet), HOneyPHP (Web Apps), RDPhoneypot (RDP)

## 📐 Architecture & Connectivity
* **Exposed Ports** Ports 22,23, 80, 443, 3389 were intentionally left open for anyone (0.0.0.0/0)

* **SSH Administration Interface** After installing the honeypot, SSH was configured from port 22 to port 64295 for restricted admin access.
* **ELK Stack and other WebUI Tools** Bound to loopback address (127.0.0.1:64297)

## After Successful Setup attacks came in as seen in the Attack Map. A 'log from the Threat Actor with the most hits was analyzed

* **INCIDENT REPORT**
Triage Timestamp: 2026-07-15 14:33:55 PH TIME
Severity Rating: Low
Attack Vector: Automated Credential Stuffing / SSH Bruteforce

* **1. Attacker Information**
Source IP: 91.92.42.227
Geo Location: Eygelshoven, Limburg, The Netherlands
IP Reputation: Known Attacker

* **2. Chain of Events**
1. 14:33:55 UTC+8 - Threat actor established SSH connection through port 22 with Session ID: 846eba3f9b27
2. 14:33:57 UTC+8 - Credential Injection was attempted a login using username: 'trade' and password: '123456'
3. 14:33:59 UTC+8 - The attacker disconnected after the failed login attempt.

* **Total time of interaction: about 3.7 secs*

*  **3. Technical Analysis**
*  The quick duration of the session matches the behavior of botnet scanning activities. The credential-stuffing observed is simliar to scripts actively searching for vulnerable systems with weak/default passwords.

*  **4.Remediation & Recommendations**
1. System Hardening - Ensure that administration on devices and systems come from whitelisted sources.
2. Password Policies - Ensure that no common and default passwords are enforced on endpoints. MFA is also recommended to implemented across all system endpoints.
3. Rate Limiting - Implement tools that blocks IP addresses that match known bot signatures.
4. Block Attacker IP - Recommend to block IP address 91.92.42.227.
