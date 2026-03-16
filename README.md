# soc-siem-simulation
Home SOC Lab

🔐 Security Simulations: Brute Force & XSS

## 🔎 Overview
This repository documents my hands-on cybersecurity simulations.  
The following are some of the attacks I have practiced in my lab environment:
- **Brute Force Attack** against an Ubuntu VM via SSH
- **Cross-Site Scripting (XSS)** due to poor input sanitization on a vulnerable form.

The repo demonstrates not only the offensive techniques but also the defensive strategies and triaging reports that for each attack.

---
---

## 🖥️ Lab Setup
I built a three-machine environment:

### Brute Force Attack Setup
- **Victim VM**: Ubuntu CLI server (installed UF sending it to port 9997 of SIEM Server)
- **Attacker VM**: Kali Linux machine used to launch brute force attempts (installed UF sending it to port 9997 of SIEM Server)
- **SIEM Server**: My host M1 Mac, configured to collect logs for monitoring and triaging

### XSS Attack Setup
- **Victim VM**: A second Kali Linux VM, configured with **Apache2** to host a vulnerable web form  
- **Attacker VM**: Kali Linux machine used to inject malicious script hosted by the victim system
- **SIEM Server**: My host M1 Mac, again serving as the central log collector and analysis point  

This dual setup allowed me to:
- Launch attacks from Kali  
- Observe vulnerabilities on different victim environments (Ubuntu CLI for brute force, Apache2 web server for XSS)  
- Forward logs to the SIEM for structured triaging and reporting

---
---

## ⚔️ Attack Simulations

### 1. Brute Force Attack (SSH)
- **Scenario**: Multiple password attempts against the SSH service of the Ubuntu victim VM.  
- **Tool Used**: Hydra (on Kali Linux) to automate brute force attempts.  
- **Artifacts**: Hydra command used for the attack, Password text file (wordlist), Output logs showing failed/successful attempts, Triaging report 
- **Impact**: Thousands of logs linked to the guessing of credentials.
- **Defense**: Rate limiting, account lockout and MFA

### 2. Cross-Site Scripting (XSS)
- **Scenario**: Malicious script injection due to poor input sanitization in a web form hosted on Apache2 (second Kali VM).  
- **Artifacts**: Vulnerable form, diagram, triaging report.  
- **Impact**: Script execution in the user’s browser, potential session hijacking or data theft.  
- **Defense**: Input validation and output encoding

---
---

## 📊 Triaging Reports
- **Attack Vector**  
- **Summary**  
- **Evidence**  
- **Scope & Impact**
- **Recommendations**  
