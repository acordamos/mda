# MDA API Design Guidelines

These guidelines establish the standardized approach for designing, developing, and maintaining RESTful APIs under the Mozambican Digital Architecture (MDA) initiative. The aim is to ensure **interoperability**, **reusability**, and **composability** across public sector systems.

Although Mozambique is a Portuguese-speaking country, all **technical interfaces (URIs, JSON keys, headers)** must be implemented in **English** for alignment with global tooling and ecosystem standards.

---

## ✅ Core Principles

1. **RESTful and Resource-Oriented**

   * APIs must follow consistent RESTful patterns using nouns for resources and standard HTTP methods.

2. **Modular and Composable**

   * APIs must be self-contained, reusable, and capable of integration across different government domains.

3. **OpenAPI 3.0 Standard**

   * All APIs must be documented using OpenAPI 3.0 with live examples and contract definitions.

4. **Consistent Resource Modeling**

   * Leverage a domain-driven design approach with entity inheritance and relationships.

5. **Lifecycle and Governance**

   * Every API must support lifecycle states: draft, candidate, production, deprecated, retired.

6. **Versioning and Stability**

   * Major changes require a version bump. No breaking changes in patch or minor releases.

7. **Security by Design**

   * Authentication, authorization, auditing, and data privacy are non-negotiable.

---

## 🔗 Base Structure & Naming

### URL Format

```
https://api.mda.gov.mz/v1/{resource}
```

### Examples:

* `GET /v1/patients`
* `POST /v1/schools/{schoolId}/students`
* `GET /v1/identities/{id}`

### Naming Rules:

* Use **camelCase** for parameters
* Use **plural nouns** for collection resources
* Use nested structure only for strong ownership relationships

---

## ⚙️ HTTP Methods & Behavior

| Method | Usage                             |
| ------ | --------------------------------- |
| GET    | Retrieve single or multiple items |
| POST   | Create a new resource             |
| PUT    | Replace an entire resource        |
| PATCH  | Update partial resource fields    |
| DELETE | Remove a resource                 |

---

## 🔍 Pagination, Filtering & Sorting

### Pagination

Use HTTP headers to provide metadata:

```http
X-Total-Count: 300
X-Total-Pages: 6
X-Current-Page: 2
X-Page-Size: 50
```

Query parameters:

```http
GET /v1/hospitals?page=2&limit=50
```

### Filtering

```http
GET /v1/patients?gender=female&district=maputo
```

### Sorting

```http
GET /v1/schools?sort=createdAt&order=desc
```

---

## 📥 Standard API Response Structure

### Success:

* Use standard HTTP status codes (200 OK, 201 Created, etc.)
* Payload:

```json
{
  "data": {
    ... resource payload ...
  },
  "meta": {
    "timestamp": "ISO-8601"
  }
}
```

### Error:

* Use appropriate HTTP error codes (400, 401, 403, 404, 422, 500)
* Payload:

```json
{
  "errors": [
    {
      "code": "INVALID_INPUT",
      "message": "The 'firstName' field is required.",
      "field": "firstName"
    }
  ]
}
```

---

## 🔐 Authentication and Authorization

* OAuth2.0 with JWT access tokens is mandatory
* Authorization scopes should be granular and hierarchical (e.g., `health.read`, `health.write`)
* Include token via:

```http
Authorization: Bearer {token}
```

---

## 🌐 Internationalization

All APIs must support the `Accept-Language` header.

```http
Accept-Language: en
```

Supported: `en`, `pt`

---

## 🧩 Resource Model Structure

All resources must support:

* **id**: string UUID
* **href**: self-link
* **status**: draft | active | suspended | archived
* **validFor**: object with startDate and endDate (ISO 8601)
* **lastUpdate**: timestamp

Example:

```json
{
  "id": "a72e...",
  "href": "/v1/patients/a72e...",
  "status": "active",
  "validFor": {
    "startDate": "2024-01-01",
    "endDate": null
  },
  "lastUpdate": "2025-06-07T11:00:00Z"
}
```

---

## 📚 Documentation Requirements

* Must follow OpenAPI 3.0 with public access
* Must include: authentication model, request/response examples, error models, changelog

---

## 🔐 Security & Logging

* Every call must log: `traceId`, `userId`, `endpoint`, `latency`, and `status`
* `X-Trace-Id` must be included in the response headers for each request
* Enforce rate limiting and IP-based throttling on sensitive routes
* Sensitive fields must be redacted in logs

---

## 🧪 Testing and Sandbox

* Mock servers must be provided for integration testing
* Contract testing via tools like Pact or Dredd encouraged
* Postman collections or Swagger UI links are mandatory in all documentation

---

## 🕒 Lifecycle and Change Management

* APIs move through the following states:

  * `draft`, `candidate`, `production`, `deprecated`, `retired`
* Major changes must be deployed under a new version path: `/v2/...`
* Deprecation notices must include `Deprecation` headers and changelogs

---

## 💬 Feedback and Evolution

Raise issues, propose improvements or contribute directly via:
[https://github.com/acordamos](https://github.com/acordamos)

> *"Public APIs are public infrastructure. Versioned. Observable. Documented."*
