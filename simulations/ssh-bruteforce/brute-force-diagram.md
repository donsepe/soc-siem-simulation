```mermaid
flowchart LR
    A[Kali VM - Attacker] -->|Hydra SSH attempts| B[Ubuntu Server - Victim]
    B -->|Authentication logs| C[SIEM - Mac Host]
    C -->|Alert: Multiple failed logins| C
