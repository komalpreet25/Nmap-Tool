# Useful NSE Scripts (Practical Collection)

## Introduction

Nmap Scripting Engine (NSE) provides hundreds of scripts for different security and networking tasks.

In real-world usage, security professionals do not remember all scripts — instead, they use a **set of commonly used useful scripts**.

This file contains the most practical and frequently used NSE scripts for:

* Information Gathering
* Service Enumeration
* Vulnerability Checks
* Network Reconnaissance

---

## 1. HTTP Information Gathering

### http-title

Fetches the title of a web page.

```bash id="h1x9kq"
nmap --script http-title target
```

Example output:

```text id="k2l8mp"
http-title: Apache Default Page
```

---

### http-headers

Displays HTTP response headers.

```bash id="x7m2np"
nmap --script http-headers target
```

Example:

```text id="p9q1rs"
Server: Apache/2.4.57
Content-Type: text/html
```

---

### http-enum

Enumerates hidden directories and files.

```bash id="a8n3bd"
nmap --script http-enum target
```

Used for:

* Finding admin panels
* Hidden directories
* Sensitive endpoints

---

## 2. SMB Enumeration (Windows Networks)

### smb-os-discovery

Detects Windows OS details.

```bash id="s3k7ld"
nmap --script smb-os-discovery target
```

---

### smb-enum-shares

Lists shared folders.

```bash id="m9v2qa"
nmap --script smb-enum-shares target
```

Example:

```text id="z1p8tw"
ADMIN$
C$
Users
```

---

### smb-enum-users

Lists user accounts on SMB.

```bash id="q5r8yd"
nmap --script smb-enum-users target
```

---

## 3. DNS Enumeration

### dns-brute

Performs DNS subdomain brute forcing.

```bash id="t8k1mn"
nmap --script dns-brute target
```

Used for:

* Subdomain discovery
* Infrastructure mapping

---

### dns-zone-transfer

Checks for misconfigured DNS zone transfers.

```bash id="c6x2pl"
nmap --script dns-zone-transfer target
```

---

## 4. FTP Enumeration

### ftp-anon

Checks if anonymous login is allowed.

```bash id="v4n7qk"
nmap --script ftp-anon target
```

Example:

```text id="r2m8sj"
Anonymous FTP login allowed
```

---

### ftp-syst

Retrieves system information from FTP server.

```bash id="d8q1zy"
nmap --script ftp-syst target
```

---

## 5. SSH Enumeration

### ssh-hostkey

Displays SSH host keys.

```bash id="k4n9pl"
nmap --script ssh-hostkey target
```

Used for:

* Fingerprinting SSH servers
* Security analysis

---

### ssh-auth-methods

Shows authentication methods supported.

```bash id="w7x3mn"
nmap --script ssh-auth-methods target
```

---

## 6. SSL/TLS Enumeration

### ssl-cert

Displays SSL certificate details.

```bash id="p3q9ld"
nmap --script ssl-cert -p 443 target
```

---

### ssl-enum-ciphers

Lists supported encryption ciphers.

```bash id="z8m2qa"
nmap --script ssl-enum-ciphers -p 443 target
```

Used for:

* Checking weak encryption
* Security auditing

---

## 7. Vulnerability Related Scripts

### http-vuln-cve2017-5638

Checks Apache Struts vulnerability.

```bash id="r9t1pl"
nmap --script http-vuln-cve2017-5638 target
```

---

### smb-vuln-ms17-010

Checks EternalBlue vulnerability.

```bash id="g5k8mn"
nmap --script smb-vuln-ms17-010 target
```

---

### ssl-heartbleed

Checks Heartbleed vulnerability.

```bash id="x2v9pl"
nmap --script ssl-heartbleed target
```

---

## 8. Default Useful Combination

Most commonly used real-world command:

```bash id="n7q2mp"
nmap -sS -sV -sC target
```

This provides:

* Open ports
* Service versions
* Default NSE scripts

---

## 9. Full Recon Command

For deep reconnaissance:

```bash id="m1k8ld"
nmap -A target
```

Includes:

* OS Detection
* Version Detection
* NSE Scripts
* Traceroute

---

## Advantages of Using NSE Scripts

### Automation

Reduces manual effort in enumeration.

### Deep Information

Provides more than simple port scanning.

### Wide Coverage

Covers HTTP, SMB, FTP, DNS, SSL, SSH, etc.

### Real-World Usage

Used in penetration testing and security audits.

---

## Limitations

### Large Output

Can generate heavy data.

### False Positives

Some scripts may not be fully accurate.

### Detection Risk

Can be detected by IDS/IPS systems.

### Requires Understanding

Results must be interpreted carefully.

---

## Best Practices

* Use `-sV` before running scripts
* Combine scripts based on target type
* Avoid running aggressive scripts on unknown systems
* Always ensure authorization before scanning

---

