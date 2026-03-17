```mermaid
flowchart LR
    A[Kali VM - Attacker] -->|Injects XSS payload| B[Kali VM - Vulnerable Web Server]
    B -->|Reflected script execution| B
    B -->|Web server logs| C[SIEM Server]
