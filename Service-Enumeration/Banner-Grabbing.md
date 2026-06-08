# Banner Grabbing

## Introduction

Banner Grabbing is a technique used to collect information about services running on a target system.

When a client connects to a service, many servers automatically provide information such as:

* Service Name
* Software Version
* Operating System Information
* Configuration Details

This information is called a **Banner**.

Banner Grabbing is commonly used during reconnaissance and enumeration phases of penetration testing.

---

## What is a Banner?

A banner is a message returned by a service when a connection is established.

Example:

```text
SSH-2.0-OpenSSH_9.0
```

This banner tells us:

* Protocol: SSH
* Software: OpenSSH
* Version: 9.0

---

## Why is Banner Grabbing Important?

Banner Grabbing helps security professionals:

* Identify running services
* Detect software versions
* Discover outdated applications
* Prepare for vulnerability assessment
* Gather information about the target

---

## How Banner Grabbing Works

### Step 1

Identify an open port.

Example:

```text
22/tcp open ssh
```

### Step 2

Connect to the service.

### Step 3

Read the banner returned by the server.

### Step 4

Analyze the information.

---

## Banner Grabbing Using Nmap

Nmap can perform banner grabbing through Version Detection.

Command:

```bash
nmap -sV 192.168.1.10
```

Example Output:

```text
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 9.0
80/tcp open  http    Apache httpd 2.4.57
```

---

## Banner Grabbing Using Netcat

Connect manually:

```bash
nc 192.168.1.10 22
```

Possible Output:

```text
SSH-2.0-OpenSSH_9.0
```

---

## Banner Grabbing Using Telnet

Example:

```bash
telnet 192.168.1.10 80
```

Request:

```text
GET / HTTP/1.1
Host: target
```

Response may reveal:

```text
Server: Apache/2.4.57
```

---

## HTTP Banner Grabbing

Command:

```bash
curl -I http://192.168.1.10
```

Example Output:

```text
Server: Apache/2.4.57
```

---

## Common Services and Banners

### SSH

```text
SSH-2.0-OpenSSH_9.0
```

### FTP

```text
220 vsFTPd 3.0.5
```

### SMTP

```text
220 mail.example.com ESMTP
```

### HTTP

```text
Server: Apache/2.4.57
```

---

## Advantages

### Fast Information Gathering

Provides quick details about services.

### Helps Vulnerability Assessment

Software versions can be checked for known vulnerabilities.

### Supports Enumeration

Useful for identifying technologies used by the target.

---

## Limitations

### Banner Hiding

Administrators may disable banners.

### Banner Spoofing

Services can display fake information.

### Incomplete Information

Some services reveal little or no version data.

---

## Security Risks of Banner Disclosure

Exposed banners may reveal:

* Software versions
* Operating systems
* Service configurations

Attackers can use this information to search for known vulnerabilities.

Example:

```text
Apache 2.2
```

may indicate outdated software.

---

## Real-World Usage

Banner Grabbing is used for:

* Penetration Testing
* Network Enumeration
* Vulnerability Assessment
* Security Audits
* Asset Discovery

---

## Related Commands

Version Detection

```bash
nmap -sV 192.168.1.10
```

Aggressive Scan

```bash
nmap -A 192.168.1.10
```

Netcat

```bash
nc 192.168.1.10 22
```

HTTP Headers

```bash
curl -I http://192.168.1.10
```


