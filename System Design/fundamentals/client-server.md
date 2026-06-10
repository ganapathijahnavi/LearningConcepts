# Client-Server Architecture

## What is Client-Server Architecture?

Client-Server Architecture is a computing model where a **client** requests services or resources and a **server** provides them.

Examples:

* Web Browser → Web Server
* Mobile App → Backend API
* ATM Machine → Banking Server

---

## Why Do We Need It?

Without a central server:

* Data would be difficult to manage
* Security would be harder to enforce
* Users could not share information efficiently

Benefits:

* Centralized data management
* Better security
* Easier maintenance
* Scalability

---

## How Does It Work?

1. Client sends a request.
2. Server processes the request.
3. Server sends a response.
4. Client displays the result.

### Example

User opens a website:

```text
Client (Browser)
       |
       | HTTP Request
       v
Server
       |
       | HTTP Response
       v
Client (Browser)
```

---

## Components

### Client

Responsible for:

* User Interface (UI)
* Sending requests
* Displaying responses

Examples:

* Chrome
* Firefox
* Mobile Apps

### Server

Responsible for:

* Business logic
* Database interaction
* Authentication
* Sending responses

Examples:

* Node.js Server
* Django Server
* Spring Boot Application

---

## Types of Client-Server Architecture

### Two-Tier Architecture

```text
Client <----> Database
```

Example:

* Desktop application connected directly to a database

---

### Three-Tier Architecture

```text
Client
   |
Application Server
   |
Database
```

Most modern web applications use this model.

---

## Advantages

* Centralized management
* Improved security
* Easy maintenance
* Better scalability
* Resource sharing

---

## Disadvantages

* Single point of failure
* Network dependency
* Server overload under heavy traffic

---

## Real-World Examples

* Gmail
* Instagram
* Netflix
* Amazon

---

## Interview Questions

### Q1. What is Client-Server Architecture?

A model where clients request resources and servers provide them.

### Q2. What is the role of a server?

Processing requests, executing business logic, and returning responses.

### Q3. Difference between Client and Server?

| Client                  | Server               |
| ----------------------- | -------------------- |
| Requests data           | Provides data        |
| User-facing             | Backend system       |
| Initiates communication | Responds to requests |

---

## Summary

Client-Server Architecture forms the foundation of modern web applications. Clients send requests, servers process them, and responses are returned to users.
