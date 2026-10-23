# Configuration Matrix & Pipeline System Details

## 🌐 Endpoints & Communication Protocols
*   **Inbound Core Adapter:** HTTPS Protocol (SAP BTP Node Access Management secured)
*   **Target Destination Gateway:** Beeceptor API Virtualization Engine
*   **Target POST Resource URI:** `https://beeceptor.com`

---

## 🛠️ Key Pipeline Component Specifications

### 1. Inbound Ingestion Routing (Splitter Loop)
*   Uses a `Sequential Multicast` to achieve atomic guaranteed delivery.
*   **Route Path A:** Instantly pushes the message body to the internal JMS queue persistence layer (`Shopify_O2C_Orders`).
*   **Route Path B:** Bypasses blocking states, triggering a `Content Modifier` to overwrite headers with a clean HTTP `202 Accepted` confirmation string straight back to the client interface.

### 2. S/4HANA OData Core Transformation Mapping
*   **Field Combination Mapping:** Source nodes `customer/first_name` + `customer/last_name` are linked using a standard graphical `concat` text block containing a blank white-space literal constant. This points directly to the target enterprise buyer record field `/ns0:SalesOrder/SoldToParty`.
*   **Transactional Tracking Identifiers:** Source `order_id` values trace directly to the structural target field `/ns0:SalesOrder/PurchaseByCustomer`.
