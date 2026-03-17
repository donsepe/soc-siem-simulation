 [Multiple failed authentication on 192.168.1.8] - [Medium]

1. Summary (Detected a Brute Force Password Attack on a Web Server)
- What happened: True Positive
- Severity: Medium

2. Evidence
- Attacker IP/Source:  192.168.1.5 tried to login about 500 times within 2 minutes which is a non-human activity.
- Raw Log Snippet: 2026-03-06T07:58:31.977883+00:00 ubuntuservetarget sshd[1812]: Failed password for ubuntutarget from 192.168.1.5 port 45518 ssh2
- Payload Analysis: Hydra9.6

3. Scope & Impact
- Affected Systems: Web Server (192.168.1.8) at port 22(SSH)
- Successful?: No successful login attempt was observed

4. Action Taken
- Immediate Action: 
-  Blocked the IP using SOAR according to the playbook

5. Recommendation:   
- Implement account lockout after multiple failed login attempts.  
- Enforce strong password policies and complexity requirements.
- Enable Multi-Factor Authentication (MFA) for privileged accounts.  
