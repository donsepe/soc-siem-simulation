```mermaid
flowchart LR
    A[Kali VM - Attacker] -->|Injects XSS payload| B[Kali VM - Vulnerable Web Server]
    B -->|Response with injected script| A
    B -->|Web server logs| C[SIEM Server]
