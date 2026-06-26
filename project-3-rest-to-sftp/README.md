# Project 3: REST API to SFTP Data Ingestion Pipeline

## Business Scenario
A retail enterprise requires automated nightly extractions of customer master records from a cloud-based CRM system via a secure REST API. This integration flow triggers on a schedule, extracts the data, converts the raw JSON payload into a structured XML format, processes metadata properties, and delivers the final dataset as a physical batch file to an on-premise billing server via SFTP.

## Core Technical Components Learned
* Timer Start Event: Programmed scheduler parameters using the On Deployment feature for manual test triggers.
* HTTP Receiver Adapter: Configured cloud-to-cloud API connections handling base URLs, Internet proxy pathways, and GET request methods.
* JSON to XML Converter: Automated conversion of raw REST JSON responses into valid XML payloads using root element mapping definitions.
* Content Modifier Property Extraction: Applied XPath processing rules to dynamic XML hierarchies to parse values into runtime exchange properties.
* Consolidated Receiver Architecture: Multi-protocol routing using a unified Receiver component block to isolate concurrent HTTP and SFTP channel credentials.

## Integration Flow Pipeline Sequence
1. Start Timer: Triggers the integration flow sequence instantly upon artifact deployment.
2. Request-Reply Step: Dispatches an HTTP GET request to the public user API endpoint using Internet routing.
3. JSON to XML Converter: Transforms the returned JSON structure into an XML format wrapped in a custom Root node.
4. Content Modifier: Executes an XPath search to extract data pages and save them as a string property variable.
5. End Step (SFTP Channel): Connects to the local target server via an ngrok tunnel to generate a dynamically named XML output file.
