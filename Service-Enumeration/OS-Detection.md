# OS Detection (-O)

## Introduction

OS Detection is a feature in Nmap that attempts to identify the Operating System running on a target machine.

Knowing the target's operating system is extremely valuable during network reconnaissance, penetration testing, and security assessments.

Using OS Detection, Nmap can identify:

* Linux
* Windows
* macOS
* FreeBSD
* Solaris
* Embedded Devices
* Network Appliances

and many other operating systems.

---

## Why is OS Detection Important?

Different operating systems have different:

* Services
* Configurations
* Vulnerabilities
* Security Mechanisms

Example:

```text
Windows and Linux use different services and security settings.
```

Knowing the OS helps security professionals choose appropriate enumeration and testing techniques.

---

## Nmap OS Detection Option

Syntax:

```bash
nmap -O <target>
```

Example:

```bash
nmap -O 192.168.1.10
```

---

## How OS Detection Works

Nmap does not log in to the target to identify the operating system.

Instead, it performs a technique called:

```text
TCP/IP Fingerprinting
```

Nmap sends specially crafted packets and analyzes the responses.

Every operating system responds slightly differently.

These differences create a unique fingerprint.

---

## What is TCP/IP Fingerprinting?

TCP/IP Fingerprinting is the process of identifying an operating system by observing how it responds to network packets.

Nmap analyzes:

* TCP Responses
* ICMP Responses
* Window Sizes
* TTL Values
* Packet Flags
* Fragmentation Behavior

The collected information is compared against the Nmap OS fingerprint database.

---

## Example Scan

Command:

```bash
nmap -O 192.168.1.10
```

Output:

```text
OS details: Linux 5.x
Network Distance: 1 hop
```

Another Example:

```text
OS details: Microsoft Windows 10
```

---

## Understanding the Output

Example:

```text
OS details: Linux 5.x
```

Meaning:

* Target is running Linux
* Nmap estimates Kernel Version 5.x

Example:

```text
Network Distance: 1 hop
```

Meaning:

* Target is one router away

---

## OS Detection Process

### Step 1

Identify at least one open port.

### Step 2

Identify at least one closed port.

### Step 3

Send special fingerprinting packets.

### Step 4

Collect responses.

### Step 5

Compare results with the Nmap fingerprint database.

### Step 6

Predict the operating system.

---

## Why Open and Closed Ports Matter

OS Detection works best when Nmap finds:

```text
At least one open port
At least one closed port
```

These responses help Nmap create a more accurate fingerprint.

---

## Aggressive OS Detection

Command:

```bash
nmap -O --osscan-guess target
```

or

```bash
nmap --fuzzy target
```

Purpose:

```text
Makes educated guesses when exact matching is difficult.
```

---

## Combining OS Detection with SYN Scan

Very common command:

```bash
nmap -sS -O target
```

Benefits:

* Fast port discovery
* OS identification

---

## Combining OS Detection with Version Detection

```bash
nmap -O -sV target
```

Provides:

* Operating System
* Services
* Software Versions

---

## Aggressive Scan

```bash
nmap -A target
```

Includes:

* OS Detection
* Version Detection
* NSE Scripts
* Traceroute

---

## Example Output

```text
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http

OS details:
Linux 5.x

Network Distance:
1 hop
```

---

## Advantages

### Identifies Target OS

Helps understand the target environment.

### Useful During Reconnaissance

Provides valuable intelligence.

### Supports Vulnerability Research

Different operating systems have different vulnerabilities.

### Improves Penetration Testing

Allows more targeted testing.

---

## Limitations

### Not Always Accurate

Some operating systems have similar fingerprints.

### Firewalls Can Interfere

Packet filtering can reduce accuracy.

### Requires Open and Closed Ports

Detection quality decreases without them.

### IDS/IPS Detection

Fingerprinting traffic may be detected.

---

## Real-World Usage

OS Detection is used for:

* Network Reconnaissance
* Asset Identification
* Security Audits
* Penetration Testing
* Vulnerability Assessments

---

## Common Related Commands

Basic OS Detection

```bash
nmap -O target
```

Version Detection

```bash
nmap -sV target
```

SYN Scan

```bash
nmap -sS target
```

Aggressive Scan

```bash
nmap -A target
```

---

