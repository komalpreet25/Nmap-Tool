# Version Detection (-sV)

## Introduction

Version Detection is an Nmap feature used to identify the exact services and software versions running on open ports.

A normal port scan only tells us:

```text
22/tcp open ssh
80/tcp open http
```

But Version Detection tells us:

```text
22/tcp open ssh OpenSSH 9.0
80/tcp open http Apache 2.4.57
```

This provides much more useful information for system administrators and security professionals.

---

## Why is Version Detection Important?

Knowing that a port is open is helpful, but knowing the exact software and version is even more valuable.

Version Detection helps us:

* Identify services
* Identify software versions
* Detect outdated applications
* Find potential vulnerabilities
* Improve security assessments

---

## How Version Detection Works

After discovering open ports, Nmap sends specially crafted probes to the target service.

The service responds with information.

Nmap compares the response with its service fingerprint database and identifies:

* Service Name
* Product Name
* Version Number
* Additional Details

---

## Syntax

Basic Version Detection:

```bash
nmap -sV <target>
```

Example:

```bash
nmap -sV 192.168.1.10
```

---

## Example Scan

Command:

```bash
nmap -sV 192.168.1.10
```

Output:

```text
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 9.0
80/tcp   open  http    Apache httpd 2.4.57
3306/tcp open  mysql   MySQL 8.0
```

---

## Understanding the Output

Example:

```text
22/tcp open ssh OpenSSH 9.0
```

Breakdown:

| Field       | Meaning          |
| ----------- | ---------------- |
| 22          | Port Number      |
| tcp         | Protocol         |
| open        | Port State       |
| ssh         | Service          |
| OpenSSH 9.0 | Software Version |

---

## Version Intensity

Nmap uses different levels of probing intensity.

Syntax:

```bash
nmap -sV --version-intensity 5 target
```

Range:

```text
0 to 9
```

### Low Intensity

```bash
nmap -sV --version-intensity 2 target
```

Faster but less accurate.

### High Intensity

```bash
nmap -sV --version-intensity 9 target
```

Slower but more accurate.

---

## Light Version Scan

```bash
nmap -sV --version-light target
```

Uses fewer probes.

Advantages:

* Faster
* Less traffic

---

## Full Version Scan

```bash
nmap -sV --version-all target
```

Uses all available probes.

Advantages:

* More accurate
* Better identification

---

## Combining with SYN Scan

Very common command:

```bash
nmap -sS -sV target
```

Process:

1. Discover open ports
2. Identify services
3. Detect versions

---

## Combining with Aggressive Scan

```bash
nmap -A target
```

Aggressive Scan automatically includes:

```text
Version Detection
OS Detection
NSE Scripts
Traceroute
```

---

## Common Services Identified

### SSH

```text
OpenSSH 9.0
```

### HTTP

```text
Apache 2.4.57
```

### FTP

```text
vsFTPd 3.0.5
```

### MySQL

```text
MySQL 8.0
```

### SMTP

```text
Postfix SMTP
```

---

## Advantages

### Detailed Information

Provides exact software versions.

### Supports Vulnerability Assessment

Outdated software can be identified quickly.

### Better Enumeration

Helps understand the target environment.

### Improves Reconnaissance

Provides more information than a normal port scan.

---

## Limitations

### Slower Than Normal Scan

Additional probes increase scan time.

### Banner Hiding

Some administrators hide version information.

### False Positives

Occasionally a service may be identified incorrectly.

### Firewall Restrictions

Filtering devices may affect results.

---

## Real-World Usage

Version Detection is commonly used for:

* Penetration Testing
* Vulnerability Assessment
* Security Audits
* Asset Discovery
* Network Enumeration

---

## Related Commands

Basic Port Scan

```bash
nmap target
```

SYN Scan with Version Detection

```bash
nmap -sS -sV target
```

Aggressive Scan

```bash
nmap -A target
```

OS Detection

```bash
nmap -O target
```
