# Project 2: Schema-Driven CSV to XML Data Transformation Pipeline

## Project Overview
Designed and implemented an asynchronous integration pipeline using **SAP Cloud Integration (CPI)** to ingest flat-file CSV employee records from a legacy server, execute schema-driven validation, and structurally convert the data into valid XML payloads required by a target HR system.

## Architecture and Connectivity
* **Source Protocol**: Automated file polling from a local **Rebex Tiny SFTP Server** running on an internal machine.
* **Cloud Gateway**: Outbound and inbound routing tunneled securely using **ngrok** via a secure TCP bridge on Port 22.
* **Core Engine**: Bound execution to a strict **XSD Structural Validator** contract (`employee_schema.xsd`) to protect down-stream environments against malformed data injection.

![Integration Flow Architecture](./docs/iflow_architecture.png)

## Technical Design Specifications
* **Sender Adapter**: SFTP polling utilizing secure `User Name/Password` credential tokens (`LOCAL_SFTP_CONN`).
* **Conversion Pattern**: Native `CSV to XML Converter` block utilizing field validation against an uploaded XSD schema template.
* **Data Integrity**: Configured automated file deletions on the source directory upon a successful read cycle to eliminate infinite loop processing.
* **Target Delivery**: Time-stamped XML document routing to an outbound staging folder via a separate SFTP outbound channel.

## How to Import and Deploy
1. Download the zipped iFlow source bundle from the `artifacts/` folder.
2. Log into your **SAP Integration Suite / CPI Tenant**.
3. Under the **Design** tab, open your development package.
4. Click **Edit** -> **Import** -> **Integration Flow** and upload the `.zip` file.
5. Ensure your runtime tenant contains the `LOCAL_SFTP_CONN` credential bundle and an updated `known_hosts` file inside the **Security Material** pool.
