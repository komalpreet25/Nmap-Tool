# Default Scripts (-sC)

## Introduction

Default Scripts in Nmap are a set of safe and commonly used NSE (Nmap Scripting Engine) scripts that run automatically when using the `-sC` option.

These scripts are designed to provide useful information without being too aggressive or disruptive to the target system.

The `-sC` option is one of the most commonly used NSE features in real-world scanning and penetration testing.

---

## What is -sC?

```text id="a1kq7p"
-sC = Run Default Scripts
```

It is equivalent to:

```bash id="b8xq3d"
--script=default
```

So this command:

```bash id="c9m2lw"
nmap -sC target
```

runs a predefined set of safe scripts.

---

## Why Use Default Scripts?

Default scripts are useful because they:

* Provide extra information beyond port scanning
* Are safe to run on most systems
* Do not perform aggressive actions
* Help in quick reconnaissance
* Require minimal configuration

---

## How Default Scripts Work

### Step 1

Nmap scans for open ports.

### Step 2

It identifies available services.

### Step 3

Default NSE scripts are executed on discovered services.

### Step 4

Results are collected and displayed.

---

## Common Information Gathered by Default Scripts

Default scripts can extract:

* Service banners
* HTTP page titles
* SSL certificates
* SSH host keys
* SMB shares (basic info)
* FTP server details
* DNS information

---

## Syntax

Basic usage:

```bash
nmap -sC <target>
```

Example:

```bash
nmap -sC 192.168.1.10
```

---

## Example Output

Command:

```bash id="x2kq7n"
nmap -sC 192.168.1.10
```

Output:

```text id="y7m3pd"
22/tcp open ssh
| ssh-hostkey:
|   2048 SHA256:abcd1234

80/tcp open http
| http-title:
|   Apache Default Page

443/tcp open https
| ssl-cert:
|   Subject: example.com
```

---

## Understanding the Output

### ssh-hostkey

Displays SSH public key information.

### http-title

Shows the title of the web page.

### ssl-cert

Displays SSL certificate details.

---

## Default Scripts Categories

Default scripts are selected from safe NSE categories such as:

* Safe scripts
* Discovery scripts
* Basic enumeration scripts

They avoid destructive actions.

---

## Combining -sC with Other Options

### With Version Detection

```bash id="c1m9qk"
nmap -sC -sV 192.168.1.10
```

Provides:

* Default script output
* Service versions

---

### With SYN Scan

```bash id="v4n8ps"
nmap -sS -sC 192.168.1.10
```

Provides:

* Fast port scanning
* Basic script enumeration

---

### With Aggressive Scan

```bash id="k7q1wx"
nmap -A 192.168.1.10
```

Includes:

* Default scripts
* OS detection
* Version detection
* Traceroute

---

## Advantages

### Safe to Use

Does not harm or modify target systems.

### Quick Information Gathering

Provides useful details instantly.

### Easy for Beginners

No advanced configuration required.

### Widely Used

Common in real-world penetration testing.

---

## Limitations

### Limited Depth

Only runs basic scripts.

### No Vulnerability Exploitation

Does not perform deep security testing.

### May Miss Advanced Information

Advanced NSE scripts provide more detail.

---

## Real-World Usage

Default scripts are used for:

* Initial reconnaissance
* Network discovery
* Service identification
* Security audits
* Penetration testing preparation

---

## Difference Between -sC and --script

| Feature    | -sC                  | --script       |
| ---------- | -------------------- | -------------- |
| Purpose    | Default safe scripts | Custom scripts |
| Complexity | Simple               | Advanced       |
| Control    | Low                  | High           |
| Usage      | Beginners            | Professionals  |

---

## Example Use Cases

### Web Server Analysis

```bash id="h8k2lm"
nmap -sC -sV target
```

Helps identify:

* Web server type
* Page titles
* SSL certificates

---

### SSH Enumeration

```bash id="n9q3dr"
nmap -sC -p 22 target
```

Collects:

* SSH host keys
* Authentication info

---

### Network Reconnaissance

```bash id="p3m7vx"
nmap -sC 192.168.1.0/24
```

Used to gather basic network information.

