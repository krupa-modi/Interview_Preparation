# REST API - Interview Notes

## What is REST API?

REST (Representational State Transfer) is an architectural style used for communication between a client and a server over HTTP.

A REST API allows applications to send and receive data using standard HTTP methods.

Example:

* Client: React Application
* Server: Node.js / Java / .NET Backend
* Communication: REST API

---

## Interview Definition

> REST API is a way for different applications to communicate with each other using HTTP protocols. It follows REST principles and uses URLs, HTTP methods, and JSON data for communication between client and server.

---

## Common HTTP Methods

### GET

Used to fetch data from the server.

```http
GET /users
```

Example:

```js
fetch("/users")
```

---

### POST

Used to create new data.

```http
POST /users
```

Example:

```js
axios.post("/users", userData)
```

---

### PUT

Used to update an entire resource.

```http
PUT /users/1
```

---

### PATCH

Used to partially update a resource.

```http
PATCH /users/1
```

---

### DELETE

Used to delete data.

```http
DELETE /users/1
```

---

## Why REST API is Used?

* Client and server remain independent.
* Easy communication between applications.
* Supports multiple platforms.
* Uses standard HTTP methods.
* Data is usually exchanged in JSON format.

---

## What is JSON?

JSON (JavaScript Object Notation) is the most common format used in REST APIs.

Example:

```json
{
  "id": 1,
  "name": "John",
  "email": "john@example.com"
}
```

---

## REST API Principles

### 1. Client-Server Architecture

Frontend and backend are separate.

### 2. Stateless

Each request contains all required information.

The server does not remember previous requests.

### 3. Uniform Interface

Resources are accessed through URLs.

Example:

```http
/users
/users/1
/products
```

### 4. Cacheable

Responses can be cached to improve performance.

---

## REST API Response Codes

| Status Code | Meaning               |
| ----------- | --------------------- |
| 200         | Success               |
| 201         | Created               |
| 400         | Bad Request           |
| 401         | Unauthorized          |
| 403         | Forbidden             |
| 404         | Not Found             |
| 500         | Internal Server Error |

---

## REST API vs SOAP

| REST        | SOAP              |
| ----------- | ----------------- |
| Lightweight | Heavy             |
| Uses JSON   | Uses XML          |
| Faster      | Slower            |
| Easy to use | Complex           |
| Widely used | Less common today |

---

## Frequently Asked Interview Questions

### What is REST API?

REST API is a set of rules that allows client and server to communicate using HTTP methods and JSON data.

---

### What are HTTP methods in REST API?

GET, POST, PUT, PATCH, DELETE.

---

### What is the difference between PUT and PATCH?

PUT updates the entire resource.

PATCH updates only specific fields.

---

### What is Stateless in REST API?

The server does not store client state between requests. Every request must contain all required information.

---

### Which data format is commonly used in REST APIs?

JSON.

---

### What status code is returned when data is successfully fetched?

200 OK.

---

### What status code is returned when a resource is created?

201 Created.

---

### What status code is returned when a resource is not found?

404 Not Found.

---

## One-Line Interview Answer

> REST API is an architectural style that enables communication between client and server using HTTP methods such as GET, POST, PUT, PATCH, and DELETE, typically exchanging data in JSON format.
