# Lab 4: NSE Scanning

## Objective

Learn how to use the Nmap Scripting Engine (NSE) to gather information, enumerate services, and identify potential vulnerabilities on a target system.

---

## Lab Setup

Attacker Machine:

* Kali Linux

Target:

* 192.168.1.10

---

## What is NSE?

NSE (Nmap Scripting Engine) allows Nmap to perform tasks beyond simple port scanning.

Using NSE, we can:

* Gather information
* Enumerate services
* Discover users and shares
* Check for vulnerabilities
* Perform security assessments

---

## Step 1: Run Default NSE Scripts

Command:

```bash
nmap -sC 192.168.1.10
```

### Explanation

`-sC` runs Nmap's default safe scripts.

Information gathered may include:

* HTTP Titles
* SSL Certificates
* SSH Host Keys
* SMB Details

---

## Step 2: Version Detection + Default Scripts

Command:

```bash
nmap -sC -sV 192.168.1.10
```

### Explanation

Combines:

* NSE Scripts
* Version Detection

This is one of the most commonly used enumeration commands.

---

## Step 3: Display Available Scripts

Command:

```bash
ls /usr/share/nmap/scripts/
```

### Explanation

Shows all NSE scripts installed on the system.

Thousands of scripts are available for different services.

---

## Step 4: Run a Specific Script

Example:

```bash
nmap --script=http-title 192.168.1.10
```

### Purpose

Retrieves the title of a web page.

Example Output:

```text
80/tcp open http

| http-title:
| Welcome to Apache Server
```

---

## Step 5: HTTP Enumeration

Command:

```bash
nmap --script=http-enum 192.168.1.10
```

### Purpose

Searches for common:

* Directories
* Admin Panels
* Login Pages
* Web Resources

---

## Step 6: Retrieve HTTP Headers

Command:

```bash
nmap --script=http-headers 192.168.1.10
```

### Purpose

Displays:

* Server Type
* Content Type
* Security Headers

Example:

```text
Server: Apache/2.4.57
```

---

## Step 7: SMB Enumeration

Command:

```bash
nmap --script=smb-os-discovery 192.168.1.10
```

### Purpose

Collects:

* OS Information
* Computer Name
* Domain Information

---

## Step 8: Enumerate SMB Shares

Command:

```bash
nmap --script=smb-enum-shares 192.168.1.10
```

### Purpose

Lists shared folders available through SMB.

---

## Step 9: Enumerate SMB Users

Command:

```bash
nmap --script=smb-enum-users 192.168.1.10
```

### Purpose

Attempts to identify SMB users.

---

## Step 10: DNS Enumeration

Command:

```bash
nmap --script=dns-brute target.com
```

### Purpose

Discovers subdomains through brute-force techniques.

---

## Step 11: SSL Certificate Enumeration

Command:

```bash
nmap --script=ssl-cert 192.168.1.10
```

### Purpose

Displays SSL certificate information.

Information may include:

* Issuer
* Subject
* Expiration Date

---

## Step 12: SSL Cipher Enumeration

Command:

```bash
nmap --script=ssl-enum-ciphers 192.168.1.10
```

### Purpose

Identifies supported SSL/TLS ciphers.

Useful for finding weak encryption.

---

## Step 13: Vulnerability Scanning

Command:

```bash
nmap --script=vuln 192.168.1.10
```

### Purpose

Runs scripts from the vulnerability category.

Checks for known weaknesses in services.

---

## Step 14: Heartbleed Check

Command:

```bash
nmap --script=ssl-heartbleed 192.168.1.10
```

### Purpose

Checks whether a server is vulnerable to Heartbleed.

---

## Step 15: Full NSE Enumeration

Command:

```bash
nmap -sC -sV --script=vuln 192.168.1.10
```

### Purpose

Performs:

* Service Detection
* Default Scripts
* Vulnerability Checks

Provides a detailed assessment of the target.

---

## NSE Workflow

```text
Port Scan
    ↓
Version Detection
    ↓
NSE Enumeration
    ↓
Service Information
    ↓
Vulnerability Assessment
```

---

## Real-World Usage

NSE is used for:

* Information Gathering
* Vulnerability Assessment
* Service Enumeration
* Security Audits
* Penetration Testing

---

## Important Notes

* Some NSE scripts generate significant traffic.
* Not every vulnerability result is accurate.
* Always validate findings manually.
* Only scan systems you are authorized to test.

