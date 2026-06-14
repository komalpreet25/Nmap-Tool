# Grepable Output (-oG)

## Introduction

Grepable Output is a special Nmap output format designed for filtering and processing scan results using command-line tools such as:

* grep
* awk
* sed
* cut

The name "Grepable" comes from the Linux command:

```bash
grep
```

which is used to search specific patterns inside files.

Before XML became widely used, Grepable Output was one of the most popular formats for automation and scripting.

---

## What is -oG?

The `-oG` option tells Nmap to save results in Grepable format.

Syntax:

```bash
nmap -oG <filename.grep> <target>
```

Example:

```bash
nmap -oG scan.grep 192.168.1.10
```

---

## Why Use Grepable Output?

Sometimes security professionals only need specific information such as:

* Open ports
* IP addresses
* Running services

Instead of reading a long report, Grepable Output allows quick filtering.

---

## Example Scan

Command:

```bash
nmap -sV -oG result.grep 192.168.1.10
```

Example Output:

```text
Host: 192.168.1.10 ()    Status: Up

Host: 192.168.1.10 ()    
Ports: 22/open/tcp//ssh///,
80/open/tcp//http///,
443/open/tcp//https///
```

---

## Understanding the Output

### Host Information

```text
Host: 192.168.1.10 () Status: Up
```

Meaning:

* Host IP = 192.168.1.10
* Host is reachable

---

### Port Information

```text
22/open/tcp//ssh///
```

Meaning:

| Field    | Value |
| -------- | ----- |
| Port     | 22    |
| State    | Open  |
| Protocol | TCP   |
| Service  | SSH   |

---

## Finding Open Ports

Command:

```bash
grep "open" result.grep
```

Output:

```text
22/open/tcp//ssh///
80/open/tcp//http///
443/open/tcp//https///
```

---

## Finding Only IP Addresses

Command:

```bash
grep "Host:" result.grep
```

Example Output:

```text
Host: 192.168.1.10
```

---

## Finding HTTP Services

Command:

```bash
grep "http" result.grep
```

Output:

```text
80/open/tcp//http///
443/open/tcp//https///
```

---

## Using awk with Grepable Output

Example:

```bash
awk '/open/ {print $2}' result.grep
```

Can be used to extract host information automatically.

---

## Combining with Large Scans

Example:

```bash
nmap 192.168.1.0/24 -oG network.grep
```

Then search for active hosts:

```bash
grep "Status: Up" network.grep
```

This quickly identifies live systems.

---

## Real-World Usage

Grepable Output was commonly used for:

* Network Audits
* Host Discovery
* Port Enumeration
* Bash Automation
* Security Reporting

---

## Important Note

Modern Nmap documentation recommends using XML Output instead of Grepable Output for advanced automation.

XML provides:

* More details
* Better structure
* Easier integration with tools

However, Grepable Output is still useful for quick command-line filtering.

---

## Advantages

### Easy Filtering

Works perfectly with grep.

### Lightweight

Smaller than XML files.

### Good for Bash Scripts

Simple structure.

### Fast Analysis

Quickly locate open ports and hosts.

---

## Limitations

### Limited Information

Contains less data than XML.

### Older Format

Not preferred for modern integrations.

### Less Structured

Difficult for complex parsing.

---

## Grepable Output vs XML Output

| Feature          | Grepable Output | XML Output |
| ---------------- | --------------- | ---------- |
| Human Readable   | Moderate        | Low        |
| grep Friendly    | Excellent       | Poor       |
| Automation       | Basic           | Advanced   |
| Tool Integration | Limited         | Excellent  |
| Structured Data  | No              | Yes        |

