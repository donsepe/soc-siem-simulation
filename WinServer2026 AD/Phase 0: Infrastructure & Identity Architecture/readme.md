Phase 0: Infrastructure & Identity ArchitecturePhase 0: Infrastructure & Identity Architecture
1. Cloud Provisioning & Network Configuration (Azure)
Compute Provisioning: Deployed a Windows Server virtual machine instance within Microsoft Azure to serve as the enterprise root authority.

Network Isolation: Configured Azure Network Security Groups (NSGs) to restrict traffic, ensuring the lab network remains isolated while allowing secure administrative management access.

Static IP Mapping: Assigned a static internal private IP address to the server via the Azure Portal to prevent IP shifting and ensure stable Domain Name System (DNS) resolution.

2. Active Directory Domain Services (AD DS) Initialization
The root identity architecture was initialized and promoted using native Windows management tools with the following structural parameters:

Deployment Operation: Created a brand-new Active Directory Forest.

Root Domain Name: MYDOMAIN.local

NetBIOS Name: MYDOMAIN

Forest & Domain Functional Levels: Set to the latest functional levels to enable modern security features and enhanced cryptographic controls.

Global Catalog (GC): Initialized on the root Domain Controller to handle centralized authentication requests and object lookups.

3. Organizational Structure & Identity Management (IAM)
Using Active Directory Users and Computers (ADUC), a logical corporate hierarchy was established to segment identities and test privilege boundaries:

Organizational Units (OUs): Built custom containers (e.g., Employees, Privileged_Accounts) to separate standard operational personnel from highly privileged administration accounts.

Identity Objects:

donadmin: Provisioned as a high-privileged Domain Administrator account authorized to perform administrative overrides and enterprise-level modifications.

lingm: Provisioned as a standard, unprivileged domain user profile with highly restricted local permissions.

Departmental Accounts: Configured supplementary test accounts within specific OUs to simulate varied organizational access requirements.

4. Group Policy Object (GPO) Deployment
Using the Group Policy Management Console (GPMC), custom operational policies were engineered and linked to the OU structure to mandate structural security configurations:

Advanced Audit Policy GPO: link: Engineered and deployed a specific auditing policy to force target endpoints to generate granular local event logs for account logons, process creation, and object access. This GPO serves as the engine that generates the precise forensic telemetry (Event IDs 4624, 4648, 4776) often monitored in the SOC environments.

Security Baseline Enforcement: Enforced restrictions via GPO to block standard users from modifying critical local machine infrastructure or accessing unauthorized enterprise resources.

5. Client Endpoint Integration
DNS Realignment: Modified the client workstation's local network adapter settings, pointing its primary IPv4 DNS server directly to the static private IP address of the Azure Domain Controller.

Domain Handshake: Joined the client workstation to the MYDOMAIN.local domain by authenticating with authorized domain credentials, successfully onboarding the asset into the Active Directory tree.
