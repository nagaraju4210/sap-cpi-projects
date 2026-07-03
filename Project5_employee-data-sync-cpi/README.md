# Project 5: Employee Data Synchronization using SAP CPI

## Overview

This project demonstrates an end-to-end employee data synchronization scenario using SAP Cloud Platform Integration (SAP CPI). Employee records are retrieved from a source HR system (simulated using the Northwind OData service), transformed using Message Mapping, and sent to a target ERP system (simulated using MockAPI) through REST APIs.

The project showcases a common enterprise integration pattern where employee master data is synchronized between two business systems.

---

## Business Scenario

Organizations maintain employee information in Human Resource (HR) systems such as SAP SuccessFactors. Other enterprise applications like SAP S/4HANA require the same employee data for business processes such as procurement, workflow approvals, reporting, and finance.

This integration retrieves employee information from the HR system, transforms the payload into the required target format, and synchronizes it with the ERP system.

---

## Project Objectives

- Retrieve employee data using the SAP CPI OData V2 Adapter.
- Transform XML payloads using Message Mapping.
- Convert XML payloads into JSON format.
- Send transformed employee data to a REST endpoint.
- Monitor and validate message execution using SAP CPI monitoring tools.

---

## System Landscape

Source System (Northwind OData Service)
↓
SAP Cloud Platform Integration (SAP CPI)
↓
Target System (MockAPI - Simulated SAP S/4HANA)

---

## Technologies Used

- SAP Integration Suite – Cloud Integration (SAP CPI)
- OData V2 Adapter
- HTTP Receiver Adapter
- Request Reply
- Message Mapping
- XML to JSON Converter
- Content Modifier
- Timer Start Event
- MockAPI
- Northwind OData Service

---

## Integration Flow

Timer
↓
Request Reply
↓
OData V2 Receiver Adapter
↓
Message Mapping
↓
XML to JSON Converter
↓
Request Reply
↓
HTTP Receiver Adapter (MockAPI)

---

## Project Features

- Employee master data synchronization
- OData data extraction
- XML payload transformation
- XML to JSON conversion
- REST API integration
- End-to-end message monitoring
- Public demo systems for learning purposes

---

## Repository Structure

employee-data-sync-cpi/
│
├── iFlow/
├── MessageMappings/
├── XSD/
├── SamplePayloads/
├── Screenshots/
├── Documentation/
└── README.md

---

## Sample Source

Northwind OData Service

Returns employee information in XML format.

---

## Sample Target

MockAPI

Receives employee information in JSON format.

---

## Learning Outcomes

This project helped in understanding:

- SAP CPI integration flow development
- OData V2 Adapter configuration
- HTTP Receiver configuration
- Message Mapping
- XML and JSON transformations
- End-to-end integration testing
- Monitoring and troubleshooting

---

## Future Enhancements

- General Splitter for processing one employee at a time
- Exception Subprocess for error handling
- Data filtering using OData query options
- Logging improvements
- Secure credential management
- Integration with real SAP SuccessFactors and SAP S/4HANA systems

---

## Author

Nagaraju Chakrapani

SAP CPI | Integration Suite | SAP BTP
