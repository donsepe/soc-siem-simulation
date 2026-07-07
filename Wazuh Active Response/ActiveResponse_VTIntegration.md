# Automated Malware Remediation with Wazuh and VirusTotal API

This project demonstrates an automated **Active Response** pipeline built using an All-in-One Wazuh deployment.
By activating FIM in Wazuh Endpoint Security we have enabled real-time monitoring of file creation, modification and deletion.
The system tracks real-time file creation on an endpoint, analyzes payloads via the VirusTotal API, and immediately responds to threats by executing a script.
