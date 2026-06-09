# Introduction to NSE (Nmap Scripting Engine)

## Introduction

NSE stands for:

```text
Nmap Scripting Engine
```

It is one of the most powerful features of Nmap.

NSE allows users to automate various networking and security-related tasks using scripts.

Instead of only discovering hosts and open ports, NSE can:

* Gather information
* Detect vulnerabilities
* Enumerate services
* Audit configurations
* Perform advanced reconnaissance

NSE transforms Nmap from a simple port scanner into a powerful security assessment tool.

---

## Why Was NSE Created?

Basic Nmap scans can identify:

```text
Open Ports
Services
Operating Systems
```

However, security professionals often need additional information.

Examples:

* Is anonymous FTP enabled?
* What users exist on an SMB server?
* Is a service vulnerable?
* What web technologies are running?

NSE was created to automate these tasks.

---

## What is an NSE Script?

An NSE script is a small program written in:

```text
Lua Programming Language
```

These scripts extend Nmap's functionality.

Each script performs a specific task such as:

* Information Gathering
* Vulnerability Detection
* Service Enumeration
* Authentication Testing

---

## How NSE Works

### Step 1

Nmap identifies the target.

### Step 2

Nmap discovers open ports.

### Step 3

Selected NSE scripts are executed.

### Step 4

Scripts interact with services.

### Step 5

Results are displayed.

Example:

```bash
nmap --script=http-title 192.168.1.10
```

Nmap connects to the web server and retrieves the page title.

---

## NSE Script Categories

Nmap organizes scripts into categories.

---

### Safe

Scripts that do not affect the target.

Examples:

* Information gathering
* Basic enumeration

Example:

```bash
nmap --script=safe target
```

---

### Discovery

Used to collect information about the target.

Examples:

* Hostnames
* Shares
* Services

Example:

```bash
nmap --script=discovery target
```

---

### Version

Provides additional service information.

Example:

```bash
nmap --script=version target
```

---

### Auth

Used for authentication-related checks.

Examples:

* Login testing
* Authentication mechanisms

Example:

```bash
nmap --script=auth target
```

---

### Vulnerability

Checks for known vulnerabilities.

Example:

```bash
nmap --script=vuln target
```

---

### Malware

Looks for signs of malware infections.

Example:

```bash
nmap --script=malware target
```

---

### Exploit

Attempts exploitation-related checks.

Example:

```bash
nmap --script=exploit target
```

---

### Brute

Performs password brute-force testing.

Example:

```bash
nmap --script=brute target
```

---

## Viewing Available Scripts

Nmap contains hundreds of scripts.

Location in Linux:

```bash
ls /usr/share/nmap/scripts/
```

Count scripts:

```bash
ls /usr/share/nmap/scripts/ | wc -l
```

---

## Running a Specific Script

Syntax:

```bash
nmap --script=<script-name> target
```

Example:

```bash
nmap --script=http-title scanme.nmap.org
```

Output:

```text
http-title:
Go ahead and ScanMe!
```

---

## Running Multiple Scripts

Example:

```bash
nmap --script=http-title,http-headers target
```

Nmap executes both scripts.

---

## Running an Entire Category

Example:

```bash
nmap --script=vuln target
```

This executes all vulnerability-related scripts.

---

## Default Scripts

One of the most common NSE options:

```bash
nmap -sC target
```

The option:

```text
-sC
```

runs Nmap's default script set.

These scripts provide useful information without being too aggressive.

---

## Example NSE Scan

Command:

```bash
nmap -sC -sV scanme.nmap.org
```

Possible Output:

```text
22/tcp open ssh OpenSSH

ssh-hostkey:
2048 SHA256:xxxx

80/tcp open http Apache

http-title:
Go ahead and ScanMe!
```

---

## Advantages of NSE

### Automation

Automates repetitive security tasks.

### Time Saving

Collects large amounts of information quickly.

### Flexibility

Hundreds of scripts available.

### Extensibility

Users can create custom scripts.

### Powerful Reconnaissance

Provides deeper information than basic scans.

---

## Limitations

### Can Generate High Traffic

Some scripts are noisy.

### Detection Risk

IDS/IPS systems may detect NSE activity.

### False Positives

Some scripts may produce inaccurate results.

### Requires Careful Usage

Aggressive scripts can impact services.

---

## Real-World Usage

Cybersecurity professionals use NSE for:

* Service Enumeration
* Vulnerability Detection
* Security Audits
* Network Reconnaissance
* Compliance Checks
* Penetration Testing

---

## Common NSE Commands

Default Scripts

```bash
nmap -sC target
```

Specific Script

```bash
nmap --script=http-title target
```

Vulnerability Scripts

```bash
nmap --script=vuln target
```

SMB Enumeration

```bash
nmap --script=smb-enum-shares target
```

DNS Enumeration

```bash
nmap --script=dns-brute target
```

---

