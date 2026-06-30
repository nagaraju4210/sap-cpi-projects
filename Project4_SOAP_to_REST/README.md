# Project 4 – SOAP to REST Transformation using SAP CPI

## Business Scenario

A legacy ERP system exposes a SOAP web service to send customer information. A modern cloud application accepts only REST APIs with JSON payloads.

SAP Cloud Integration (CPI) acts as the middleware to transform SOAP XML into REST JSON, invoke the REST service, process the response, and return a SOAP acknowledgment back to the ERP system.

---

## Architecture

ERP (SOAP)
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
HTTP Receiver (REST API)
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
ERP

---

## Technologies Used

- SAP Integration Suite (Cloud Integration)
- SOAP Sender Adapter
- HTTP Receiver Adapter
- Message Mapping
- XML to JSON Converter
- JSON to XML Converter
- Request Reply
- Content Modifier
- WSDL
- XSD
- Postman

---

## Source SOAP Request

CustomerRequest

Fields:

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

## Target REST JSON

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

## REST Response

```json
{
  "customerId":"CUST1001",
  "firstName":"John",
  "lastName":"Doe",
  "email":"john.doe@gmail.com",
  "phone":"9876543210",
  "city":"Hyderabad",
  "country":"India",
  "customerType":"Premium",
  "status":"Active",
  "createdDate":"2026-06-30",
  "id":101
}
```

---

## Final SOAP Response

```xml
<CustomerResponse>
    <Status>SUCCESS</Status>
    <SystemMessage>
        Customer CUST1001 created successfully. REST ID: 101
    </SystemMessage>
</CustomerResponse>
```

---

## Skills Demonstrated

- SOAP Web Service Integration
- REST API Integration
- XML Transformation
- JSON Transformation
- WSDL Usage
- XSD Design
- Message Mapping
- Request Reply Pattern
- Synchronous Integration
- SAP CPI Monitoring
- End-to-End Interface Testing

---

## Tools Used

- SAP Integration Suite (Cloud Integration)
- Postman
- GitHub
