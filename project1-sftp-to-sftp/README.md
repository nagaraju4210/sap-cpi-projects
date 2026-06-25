# Project 1: On-Premise to Cloud SFTP File Movement Pipeline

## Business Scenario
A third-party vendor drops multi-format files onto an on-premise SFTP server. SAP Cloud Integration (CPI) is configured to automatically ingest, validate, and route these files to a secure target delivery directory with dynamic timestamp formatting.

##  Technical Architecture
[Local Input Folder] ➔ [Rebex SFTP Server] ➔ [ngrok TCP Tunnel] ➔ [SAP CPI Cloud Runtime] ➔ [Target Output Folder]

##  Implementation Highlights
- **Hybrid Networking via Cloud Tunnelling:** Resolved local laptop firewall restrictions by deploying a secure ngrok TCP network bridge to safely expose on-premise Port 22 traffic to the SAP cloud tenant.
- **Enterprise Security Management:** Secured the endpoint endpoints by configuring User Credentials (`LOCAL_SFTP_CONN`) and hand-crafting a custom `known_hosts` (SSH Host Key Fingerprint) security material artifact to manage global handshakes.
- **Dynamic Expression Language parsing:** Implemented Apache Camel Expression Language (`${header.CamelFileNameExt}`) alongside broad file wildcards (`*.*`) to dynamically capture, process, and retain multi-format file extensions.
- **Pipeline Fault Tolerance:** Programmed fine-tuned connection timeouts (10,000 ms), polling frequency intervals, and post-processing automatic file deletion routines to mitigate endless loop hazards.

##  Repository Directory Contents
- `/artifacts/` — Hosts the deployable SAP CPI Integration Flow `.zip` archive package bundle.
- `/test-data/` — Contains clean mock sample dataset structures (`demofile.csv`) used to trigger and validate the end-to-end cloud pipeline execution.

