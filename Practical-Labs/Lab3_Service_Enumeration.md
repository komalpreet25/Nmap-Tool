# Lab 3: Service Enumeration

## Objective

Learn how to identify running services, software versions, banners, and operating system information using Nmap.

Service Enumeration helps security professionals understand what services are running on a target and whether they may contain vulnerabilities.

---

## Lab Setup

Attacker Machine:

* Kali Linux

Target:

* 192.168.1.10 (Lab Machine)

---

## What is Service Enumeration?

After discovering open ports, the next step is determining:

* Which service is running
* Service version
* Software details
* Operating system information
* Additional host information

This process is called Service Enumeration.

---

## Step 1: Version Detection

Command:

```bash
nmap -sV 192.168.1.10
```

### Explanation

* `-sV` enables version detection.
* Nmap sends probes to identify software versions.

### Sample Output

```text
PORT     STATE SERVICE VERSION

22/tcp   open  ssh     OpenSSH 9.0
80/tcp   open  http    Apache 2.4.57
```

### Information Gathered

* Open ports
* Service names
* Software versions

---

## Step 2: Service Enumeration with SYN Scan

Command:

```bash
sudo nmap -sS -sV 192.168.1.10
```

### Explanation

Combines:

* SYN Scan
* Version Detection

This is one of the most commonly used reconnaissance commands.

---

## Step 3: Banner Grabbing

Command:

```bash
nmap -sV 192.168.1.10
```

### Explanation

Nmap attempts to retrieve service banners.

Example Banner:

```text
Apache/2.4.57
OpenSSH_9.0
```

Banners often reveal:

* Software name
* Version number
* Service details

---

## Step 4: Default NSE Scripts

Command:

```bash
nmap -sC 192.168.1.10
```

### Explanation

Runs default NSE scripts.

These scripts collect additional information such as:

* HTTP titles
* SSL certificates
* SSH host keys
* SMB information

---

## Step 5: Version Detection + Default Scripts

Command:

```bash
nmap -sC -sV 192.168.1.10
```

### Explanation

One of the most popular enumeration commands.

Provides:

* Service versions
* Banner information
* NSE results

---

## Step 6: OS Detection

Command:

```bash
sudo nmap -O 192.168.1.10
```

### Explanation

Attempts to identify:

* Operating System
* Device type
* Network characteristics

### Sample Output

```text
OS details:
Linux 6.x
```

---

## Step 7: Full Enumeration Scan

Command:

```bash
sudo nmap -sS -sV -sC -O 192.168.1.10
```

### Explanation

Performs:

* Port Discovery
* Version Detection
* NSE Enumeration
* OS Detection

This provides a strong reconnaissance profile of the target.

---

## Step 8: Aggressive Scan

Command:

```bash
sudo nmap -A 192.168.1.10
```

### Explanation

Enables:

* Version Detection
* OS Detection
* NSE Scripts
* Traceroute

### Why Use It?

Fast way to gather extensive information from a target.

---

## Enumeration Workflow

Typical workflow:

```text
Host Discovery
      ↓
Port Scanning
      ↓
Version Detection
      ↓
Banner Grabbing
      ↓
NSE Scripts
      ↓
OS Detection
```

---

## Real-World Usage

Service Enumeration is used for:

* Vulnerability Assessment
* Penetration Testing
* Asset Discovery
* Security Audits
* Reconnaissance

---

## Important Notes

* Enumeration generates more traffic than basic scanning.
* Firewalls may block some probes.
* Version information may not always be accurate.
* Always verify findings manually.

