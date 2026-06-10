# DNS (Domain Name System)

## What is DNS?

DNS stands for **Domain Name System**.

It translates human-readable domain names into IP addresses.

Example:

```text
google.com
     ↓
142.250.183.206
```

Humans remember names, computers communicate using IP addresses.

---

## Why Do We Need DNS?

Imagine remembering IP addresses for every website:

```text
142.250.183.206
151.101.65.140
104.18.32.47
```

DNS allows us to use:

```text
google.com
github.com
openai.com
```

instead of IP addresses.

---

## How DNS Works

When a user enters:

```text
www.google.com
```

the following steps occur:

### Step 1

Browser checks local cache.

### Step 2

Operating System checks DNS cache.

### Step 3

Request reaches Recursive Resolver.

### Step 4

Resolver contacts Root DNS Server.

### Step 5

Root Server points to TLD Server.

### Step 6

TLD Server points to Authoritative DNS Server.

### Step 7

Authoritative Server returns the IP address.

### Step 8

Browser connects to the web server.

---

## DNS Resolution Flow

```text
User
 |
Browser Cache
 |
OS Cache
 |
Recursive Resolver
 |
Root DNS Server
 |
TLD DNS Server (.com)
 |
Authoritative DNS Server
 |
IP Address Returned
 |
Website Loaded
```

---

## Important DNS Components

### Recursive Resolver

Finds the IP address on behalf of the client.

### Root DNS Server

Knows where TLD servers are located.

### TLD Server

Manages domains like:

```text
.com
.org
.net
.in
```

### Authoritative DNS Server

Stores actual domain records.

---

## Common DNS Records

### A Record

Maps domain to IPv4 address.

```text
google.com → 142.250.183.206
```

### AAAA Record

Maps domain to IPv6 address.

### CNAME

Maps one domain to another.

```text
blog.example.com
      ↓
example.com
```

### MX Record

Used for email routing.

### TXT Record

Stores verification and configuration data.

---

## DNS Caching

DNS responses are cached to improve speed.

Benefits:

* Faster website loading
* Reduced DNS traffic
* Lower latency

---

## Advantages

* Easy-to-remember domain names
* Faster access through caching
* Scalable internet infrastructure

---

## Disadvantages

* DNS outages affect accessibility
* DNS attacks can disrupt services
* Initial lookup adds latency

---

## Real-World Example

Opening:

```text
https://www.google.com
```

DNS converts:

```text
www.google.com
      ↓
IP Address
```

Then the browser sends an HTTP request to that IP.

---

## Interview Questions

### Q1. What is DNS?

A system that converts domain names into IP addresses.

### Q2. What is DNS Resolution?

The process of finding the IP address associated with a domain name.

### Q3. What is an A Record?

A DNS record that maps a domain to an IPv4 address.

### Q4. What is DNS Caching?

Temporary storage of DNS results to improve lookup speed.

---

## Summary

DNS acts like the internet's phonebook. It converts domain names into IP addresses, enabling browsers to locate and communicate with servers efficiently.
