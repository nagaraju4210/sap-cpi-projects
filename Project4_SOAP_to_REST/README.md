# Project 4 – SOAP to REST Transformation using SAP Integration Suite (SAP CPI)

A real-world enterprise integration project demonstrating synchronous SOAP to REST transformation using SAP Integration Suite (Cloud Integration). This project exposes a SOAP web service using a WSDL, transforms XML requests into JSON, invokes a REST API, processes the response, and returns a WSDL-compliant SOAP acknowledgment to the calling ERP system.

---

# Business Scenario

A legacy ERP system exposes a SOAP web service to send customer information. However, the target cloud application only accepts REST APIs with JSON payloads.

SAP Integration Suite (Cloud Integration) acts as the middleware that:

- Receives SOAP requests from the ERP system.
- Removes the SOAP envelope and extracts the business payload.
- Transforms the XML payload into the JSON format expected by the REST API.
- Invokes the REST API using the HTTP Receiver Adapter.
- Processes the REST response.
- Converts the response back into the SOAP format defined by the WSDL.
- Returns a synchronous acknowledgment to the ERP system.

---

# Architecture

```text
ERP System (SOAP Client)
          │
          ▼
SOAP Sender Adapter
          │
          ▼
Request Message Mapping
          │
          ▼
XML → JSON Converter
          │
          ▼
Content Modifier
          │
          ▼
Request Reply
          │
          ▼
HTTP Receiver Adapter
          │
          ▼
REST API
          │
          ▼
JSON → XML Converter
          │
          ▼
Response Message Mapping
          │
          ▼
SOAP Response
          │
          ▼
ERP System
```

---

# Integration Flow

1. ERP sends a SOAP request.
2. SOAP Sender Adapter validates the request using the WSDL.
3. SAP CPI removes the SOAP Envelope and extracts the business payload.
4. Request Message Mapping converts the SOAP payload into the target REST structure.
5. XML is converted into JSON.
6. HTTP Receiver Adapter invokes the REST API.
7. REST API returns a JSON response.
8. JSON response is converted back to XML.
9. Response Message Mapping transforms the REST response into the WSDL-defined SOAP response.
10. SOAP Sender Adapter wraps the response inside a SOAP Envelope and returns it to the ERP system.

---

# Technologies Used

- SAP Integration Suite (Cloud Integration)
- SOAP Sender Adapter
- HTTP Receiver Adapter
- Request Reply
- Content Modifier
- Message Mapping
- XML to JSON Converter
- JSON to XML Converter
- WSDL
- XSD
- XML
- JSON
- SOAP
- REST API
- Postman
- Git
- GitHub

---

# WSDL Operations

### Request

```
CustomerRequest
```

Fields

- CustomerID
- FirstName
- LastName
- Email
- Phone
- City
- Country
- CustomerType
- Status
- CreatedDate

---

### Response

```
CustomerResponse
```

Fields

- Status
- SystemMessage

---

# Target REST Request

```json
{
  "customerId": "CUST1001",
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@gmail.com",
  "phone": "9876543210",
  "city": "Hyderabad",
  "country": "India",
  "customerType": "Premium",
  "status": "Active",
  "createdDate": "2026-06-30"
}
```

---

# REST API Used

For demonstration purposes, this project invokes the following public REST endpoint:

```
POST https://jsonplaceholder.typicode.com/posts
```

The API accepts a JSON request and returns a JSON response that simulates the creation of a resource.

---

# Sample REST Response

```json
{
  "customerId": "CUST1001",
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@gmail.com",
  "phone": "9876543210",
  "city": "Hyderabad",
  "country": "India",
  "customerType": "Premium",
  "status": "Active",
  "createdDate": "2026-06-30",
  "id": 101
}
```

---

# Final SOAP Response

```xml
<CustomerResponse xmlns="http://integration.com/customer">
    <Status>SUCCESS</Status>
    <SystemMessage>
        Customer CUST1001 created successfully. REST ID: 101
    </SystemMessage>
</CustomerResponse>
```

---

# SAP CPI Components Used

- SOAP Sender Adapter
- HTTP Receiver Adapter
- Request Reply
- Content Modifier
- XML to JSON Converter
- JSON to XML Converter
- Request Message Mapping
- Response Message Mapping
- WSDL
- XSD
- Monitoring
- Trace

---

# Skills Demonstrated

- SOAP Web Service Integration
- REST API Integration
- SOAP to REST Transformation
- XML to JSON Conversion
- JSON to XML Conversion
- WSDL-based Service Development
- XSD Schema Design
- Request Message Mapping
- Response Message Mapping
- Synchronous Integration Pattern
- HTTP Communication
- Enterprise Integration Design
- End-to-End Interface Testing
- SAP CPI Monitoring and Trace Analysis

---

# Project Outcome

✔ Successfully exposed a SOAP service using a WSDL.

✔ Transformed SOAP XML requests into REST JSON.

✔ Invoked a REST API using the HTTP Receiver Adapter.

✔ Processed the REST API response.

✔ Converted JSON responses back into XML.

✔ Returned a WSDL-compliant SOAP response to the calling ERP system.

✔ Successfully tested the complete integration using Postman.

---

# Repository Structure

```text
Project4_SOAP_to_REST
│
├── README.md
├── iFlow/
├── WSDL/
├── Schemas/
├── MessageMappings/
├── SampleRequests/
├── Screenshots/
└── Documents/
```

---

# Screenshots

This repository includes:

- SOAP to REST iFlow
- Request Message Mapping
- Response Message Mapping
- SOAP Request (Postman)
- SOAP Response (Postman)
- Successful Message Processing Log
- End-to-End Integration Flow

---

# Learning Objectives

This project demonstrates how SAP Integration Suite enables communication between legacy SOAP-based enterprise applications and modern REST-based cloud applications by performing message transformation, protocol conversion, and synchronous request-response processing.

---

# Author

**Nagaraju Chakrapani**

SAP CPI | SAP Integration Suite | SAP BTP | Integration Developer

GitHub: https://github.com/nagaraju4210
