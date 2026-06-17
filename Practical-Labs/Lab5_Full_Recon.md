# Lab 5: Full Reconnaissance Workflow

## Objective

Perform a complete Nmap reconnaissance process from host discovery to service enumeration and result reporting.

This lab combines everything learned throughout the repository into a single professional workflow.

---

## Lab Setup

Attacker Machine:

* Kali Linux

Target:

* 192.168.1.10

Network:

* 192.168.1.0/24

---

# Reconnaissance Workflow

```text id="ghc2tw"
Host Discovery
      ↓
Port Scanning
      ↓
Service Enumeration
      ↓
NSE Scanning
      ↓
OS Detection
      ↓
Report Generation
```

---

## Phase 1: Host Discovery

### Discover Live Hosts

Command:

```bash id="n0f9kw"
nmap -sn 192.168.1.0/24
```

### Purpose

Identify active systems before performing detailed scans.

### Example Output

```text id="4clc6s"
Nmap scan report for 192.168.1.5
Host is up

Nmap scan report for 192.168.1.10
Host is up
```

### Result

Target selected:

```text id="uy4c94"
192.168.1.10
```

---

## Phase 2: Initial Port Scan

### Scan Top Ports

Command:

```bash id="pfrksw"
nmap 192.168.1.10
```

### Purpose

Identify open ports.

### Example Output

```text id="2xll8m"
22/tcp open ssh
80/tcp open http
443/tcp open https
```

---

## Phase 3: Full Port Scan

### Scan All Ports

Command:

```bash id="n09r0v"
nmap -p- 192.168.1.10
```

### Purpose

Discover services running on non-standard ports.

### Example Output

```text id="65hlgm"
22/tcp open ssh
80/tcp open http
443/tcp open https
8080/tcp open http-proxy
```

---

## Phase 4: Service Enumeration

### Detect Service Versions

Command:

```bash id="ofx6n4"
nmap -sV 192.168.1.10
```

### Example Output

```text id="kxjlwm"
22/tcp open ssh OpenSSH 9.0

80/tcp open http Apache 2.4.57
```

### Purpose

Identify:

* Service Names
* Software Versions
* Potential Targets for Further Analysis

---

## Phase 5: Banner Grabbing

### Retrieve Service Information

Command:

```bash id="r8ry4r"
nmap -sV 192.168.1.10
```

### Information Obtained

* Product Name
* Version Number
* Vendor Information

Example:

```text id="6ih2yd"
Apache/2.4.57
OpenSSH_9.0
```

---

## Phase 6: Default NSE Scripts

### Run Safe Enumeration Scripts

Command:

```bash id="oqx86k"
nmap -sC 192.168.1.10
```

### Information Gathered

* HTTP Titles
* SSL Information
* SSH Keys
* SMB Information

---

## Phase 7: OS Detection

### Identify Operating System

Command:

```bash id="mmy0tz"
sudo nmap -O 192.168.1.10
```

### Example Output

```text id="e8o78u"
Linux 6.x
```

### Purpose

Determine:

* Operating System
* Device Type
* Network Characteristics

---

## Phase 8: Aggressive Enumeration

### Comprehensive Scan

Command:

```bash id="5x8zv6"
sudo nmap -A 192.168.1.10
```

### Includes

* Version Detection
* OS Detection
* NSE Scripts
* Traceroute

---

## Phase 9: Vulnerability Assessment

### Run Vulnerability Scripts

Command:

```bash id="0nr6jr"
nmap --script=vuln 192.168.1.10
```

### Purpose

Check services for known vulnerabilities.

### Example Findings

```text id="ewj17k"
Potential Vulnerability Detected
Further Verification Required
```

### Important

NSE findings should always be validated manually.

---

## Phase 10: Save Results

### Save in Normal Format

```bash id="b39s6e"
nmap -A -oN report.nmap 192.168.1.10
```

---

### Save in XML Format

```bash id="x4x17y"
nmap -A -oX report.xml 192.168.1.10
```

---

### Save in All Formats

```bash id="gnmbb2"
nmap -A -oA final_report 192.168.1.10
```

Generated Files:

```text id="f7n1x4"
final_report.nmap
final_report.xml
final_report.gnmap
```

---

# Final Assessment Example

## Open Ports

```text id="efgkxt"
22/tcp
80/tcp
443/tcp
8080/tcp
```

---

## Services

```text id="y1gvc6"
SSH
HTTP
HTTPS
HTTP Proxy
```

---

## Software Versions

```text id="4w2z6s"
OpenSSH 9.0
Apache 2.4.57
```

---

## Operating System

```text id="76c52x"
Linux
```

---

## NSE Findings

```text id="pdcl0h"
HTTP Title Identified
SSL Certificate Enumerated
```

---

# Professional Recon Workflow

Many penetration testers use a workflow similar to:

```text id="zv1trh"
Host Discovery
        ↓
Port Scan
        ↓
Version Detection
        ↓
NSE Enumeration
        ↓
OS Detection
        ↓
Documentation
```

This ensures systematic information gathering.

---

## Real-World Usage

Used during:

* Penetration Testing
* Vulnerability Assessments
* Internal Security Audits
* Asset Discovery
* Network Mapping

---

## Important Notes

* Always obtain authorization before scanning.
* Validate automated findings manually.
* Save scan results for reporting.
* Large scans may take significant time.

