# Aggressive Scan (-A)

## Introduction

Aggressive Scan is one of the most powerful scanning techniques available in Nmap.

Instead of performing only port scanning, Aggressive Scan combines multiple advanced scanning features into a single command.

When using **-A**, Nmap automatically performs:

* OS Detection
* Version Detection
* NSE Script Scanning
* Traceroute

This provides detailed information about the target system.

---

## Why Use Aggressive Scan?

Normal port scanning only tells us:

```text
Which ports are open
```

Aggressive Scan tells us:

```text
Which operating system is running
Which services are running
Service versions
Additional information through scripts
Network path to target
```

This makes Aggressive Scan extremely useful during reconnaissance and penetration testing.

---

## Syntax

```bash
nmap -A <target>
```

Example:

```bash
nmap -A 192.168.1.10
```

---

## Components of Aggressive Scan

### 1. OS Detection (-O)

Nmap attempts to identify the operating system running on the target.

Example Output:

```text
OS Details:
Linux 5.x
```

or

```text
Windows 10
```

---

### How OS Detection Works

Nmap sends specially crafted packets.

Different operating systems respond differently.

Nmap compares responses with its fingerprint database and predicts the operating system.

---

## 2. Version Detection (-sV)

Version Detection identifies:

* Service Name
* Software Version

Example:

```text
22/tcp open ssh OpenSSH 9.0
80/tcp open http Apache 2.4.57
```

---

### Why Version Detection Matters

Older software may contain vulnerabilities.

Example:

```text
Apache 2.2
```

might contain known security issues.

Version detection helps security professionals identify outdated services.

---

## 3. NSE Script Scanning (-sC)

NSE stands for:

```text
Nmap Scripting Engine
```

Nmap contains hundreds of scripts for gathering information.

Examples:

* Detect vulnerabilities
* Gather service information
* Check configurations
* Enumerate users
* Collect banners

---

### Example NSE Output

```text
ssh-hostkey:
2048 SHA256:xxxx
```

or

```text
http-title:
Apache Default Page
```

---

## 4. Traceroute

Traceroute identifies the path packets take to reach the target.

Example:

```text
Router 1
Router 2
Router 3
Target
```

This helps understand network routing.

---

## What Happens Internally?

When you run:

```bash
nmap -A 192.168.1.10
```

Nmap performs:

### Step 1

Host Discovery

```text
Checks whether host is alive
```

### Step 2

Port Scanning

```text
Finds open ports
```

### Step 3

Version Detection

```text
Identifies services
```

### Step 4

OS Detection

```text
Attempts OS fingerprinting
```

### Step 5

NSE Scripts

```text
Collects additional information
```

### Step 6

Traceroute

```text
Maps route to target
```

---

## Example Scan

```bash
nmap -A scanme.nmap.org
```

Example Output:

```text
22/tcp open ssh OpenSSH
80/tcp open http Apache

OS Details:
Linux

Traceroute:
1 Router
2 Router
3 Target
```

---

## Aggressive Scan with Specific Ports

```bash
nmap -A -p 22,80,443 192.168.1.10
```

Only selected ports will be analyzed.

---

## Advantages

### Comprehensive Information

Provides detailed intelligence about the target.

### Saves Time

One command performs multiple tasks.

### Excellent for Reconnaissance

Useful during initial assessments.

### Identifies Software Versions

Helps detect vulnerable services.

---

## Limitations

### Slower

More features mean longer scan times.

### Generates More Traffic

Can be noisy on the network.

### Easier to Detect

IDS and IPS solutions can identify aggressive scans.

### Requires Permissions

Some features may need elevated privileges.

---

## Aggressive Scan vs Normal Scan

| Feature              | Normal Scan | Aggressive Scan |
| -------------------- | ----------- | --------------- |
| Open Ports           | Yes         | Yes             |
| OS Detection         | No          | Yes             |
| Version Detection    | No          | Yes             |
| NSE Scripts          | No          | Yes             |
| Traceroute           | No          | Yes             |
| Speed                | Faster      | Slower          |
| Information Gathered | Basic       | Detailed        |

---

## Real-World Usage

Security professionals use Aggressive Scan for:

* Network reconnaissance
* Penetration testing
* Security audits
* Asset discovery
* Vulnerability assessment preparation

---

## Common Related Commands

OS Detection Only

```bash
nmap -O 192.168.1.10
```

Version Detection Only

```bash
nmap -sV 192.168.1.10
```

Default Scripts

```bash
nmap -sC 192.168.1.10
```

SYN Scan

```bash
nmap -sS 192.168.1.10
```


