# HTTP and HTTPS

## What is HTTP?

HTTP (HyperText Transfer Protocol) is the communication protocol used by web browsers and servers to exchange data over the internet.

Example:

```text
Browser ---- HTTP Request ----> Server
Browser <--- HTTP Response ---- Server
```

When you visit a website, your browser sends an HTTP request and receives an HTTP response.

---

## Why Do We Need HTTP?

HTTP provides a standard way for clients and servers to communicate.

Without HTTP:

* Browsers wouldn't know how to request web pages.
* Servers wouldn't know how to respond.
* Websites could not function consistently.

---

## How HTTP Works

### Step 1: User Requests a Website

```text
https://example.com
```

### Step 2: Browser Sends Request

```http
GET / HTTP/1.1
Host: example.com
```

### Step 3: Server Processes Request

The server:

* Receives the request
* Executes business logic
* Retrieves data if needed

### Step 4: Server Sends Response

```http
HTTP/1.1 200 OK
Content-Type: text/html
```

### Step 5: Browser Renders the Page

The user sees the webpage.

---

## HTTP Request Structure

### Request Line

```http
GET /products HTTP/1.1
```

Contains:

* Method
* Resource Path
* HTTP Version

### Headers

```http
Host: example.com
User-Agent: Chrome
```

Contain metadata about the request.

### Body (Optional)

Used in:

* POST
* PUT
* PATCH

Example:

```json
{
  "name": "John",
  "email": "john@example.com"
}
```

---

## HTTP Response Structure

### Status Line

```http
HTTP/1.1 200 OK
```

### Headers

```http
Content-Type: application/json
```

### Body

```json
{
  "message": "Success"
}
```

---

## Common HTTP Methods

| Method | Purpose                |
| ------ | ---------------------- |
| GET    | Retrieve data          |
| POST   | Create data            |
| PUT    | Update entire resource |
| PATCH  | Partial update         |
| DELETE | Remove resource        |

Example:

```text
GET    /users
POST   /users
PUT    /users/1
DELETE /users/1
```

---

## Important HTTP Status Codes

### Success

```text
200 OK
201 Created
204 No Content
```

### Client Errors

```text
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

### Server Errors

```text
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
```

---

# What is HTTPS?

HTTPS (HyperText Transfer Protocol Secure) is the secure version of HTTP.

HTTPS uses:

```text
HTTP + SSL/TLS Encryption
```

to protect communication between clients and servers.

---

## Why Do We Need HTTPS?

HTTP sends data in plain text.

An attacker can intercept:

```text
Username
Password
Credit Card Details
Cookies
```

HTTPS encrypts the data before transmission.

---

## HTTP vs HTTPS

| HTTP                  | HTTPS                   |
| --------------------- | ----------------------- |
| Not Secure            | Secure                  |
| No Encryption         | Encryption Enabled      |
| Port 80               | Port 443                |
| Faster Setup          | Slightly More Overhead  |
| Vulnerable to Attacks | Protected Communication |

---

## How HTTPS Works

### Step 1

Browser requests a secure connection.

### Step 2

Server sends its SSL/TLS Certificate.

### Step 3

Browser verifies the certificate.

### Step 4

A secure encrypted connection is established.

### Step 5

Data is exchanged securely.

---

## SSL/TLS Handshake (Simplified)

```text
Browser
   |
   | Request Secure Connection
   |
Server
   |
   | Sends Certificate
   |
Browser
   |
   | Verifies Certificate
   |
Encryption Keys Generated
   |
Secure Communication Begins
```

---

## Benefits of HTTPS

* Encrypts data
* Prevents eavesdropping
* Protects user credentials
* Improves trust
* Required for modern web features

---

## Real-World Example

Without HTTPS:

```text
User → Password → Internet → Server
```

Anyone monitoring the network may see the password.

With HTTPS:

```text
User → Encrypted Password → Internet → Server
```

Attackers cannot read the encrypted data.

---

## Interview Questions

### Q1. What is HTTP?

A protocol used for communication between clients and servers on the web.

### Q2. What is HTTPS?

A secure version of HTTP that uses SSL/TLS encryption.

### Q3. Why is HTTPS important?

It protects sensitive information from interception.

### Q4. What port does HTTPS use?

Port 443.

### Q5. What is the difference between HTTP and HTTPS?

HTTPS encrypts data while HTTP sends data in plain text.

---

## Summary

HTTP enables communication between clients and servers, while HTTPS adds SSL/TLS encryption to ensure secure and trustworthy communication over the internet.
