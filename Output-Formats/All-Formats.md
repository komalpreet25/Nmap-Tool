# All Formats Output (-oA)

## Introduction

When performing a scan, security professionals often need multiple output formats at the same time.

For example:

* Human-readable results for reports
* XML results for automation
* Grepable results for quick filtering

Instead of running Nmap multiple times with different output options, Nmap provides the `-oA` option.

`-oA` saves scan results in all major output formats simultaneously.

---

## What is -oA?

The `-oA` option stands for:

```text
Output All Formats
```

It automatically generates:

1. Normal Output (`.nmap`)
2. XML Output (`.xml`)
3. Grepable Output (`.gnmap`)

from a single scan.

---

## Syntax

```bash
nmap -oA <filename> <target>
```

Example:

```bash
nmap -oA scan_results 192.168.1.10
```

---

## Files Created

The above command creates:

```text
scan_results.nmap
scan_results.xml
scan_results.gnmap
```

---

## Understanding Each File

### 1. Normal Output (.nmap)

Example:

```text
scan_results.nmap
```

Used for:

* Reading scan results manually
* Reports
* Documentation

Human-friendly format.

---

### 2. XML Output (.xml)

Example:

```text
scan_results.xml
```

Used for:

* Automation
* Scripts
* Security Tools
* Report Generation

Machine-friendly format.

---

### 3. Grepable Output (.gnmap)

Example:

```text
scan_results.gnmap
```

Used for:

* grep
* awk
* sed
* Bash scripting

Quick filtering and extraction.

---

## Example Scan

Command:

```bash
nmap -sS -sV -oA full_scan 192.168.1.10
```

Generated files:

```text
full_scan.nmap
full_scan.xml
full_scan.gnmap
```

Nmap performs only one scan but saves results in three different formats.

---

## Viewing Generated Files

### Normal Output

```bash
cat full_scan.nmap
```

---

### XML Output

```bash
cat full_scan.xml
```

---

### Grepable Output

```bash
cat full_scan.gnmap
```

---

## Using -oA with Aggressive Scan

Example:

```bash
nmap -A -oA aggressive_scan target
```

This saves:

* Open Ports
* Service Versions
* OS Detection
* NSE Results
* Traceroute Information

in all three formats.

---

## Using -oA During Penetration Testing

Example:

```bash
nmap -sS -sV -O -oA client_network 192.168.1.0/24
```

Benefits:

* Report-ready output
* Automation-ready XML
* Grepable results for quick filtering

No need to repeat the scan.

---

## Why Security Professionals Use -oA

### Saves Time

One scan produces multiple outputs.

### Better Documentation

Keeps all formats together.

### Easier Automation

XML file is immediately available.

### Faster Analysis

Grepable output can be filtered quickly.

---

## Advantages

### One Command

Creates multiple output formats.

### Efficient

No need for repeated scans.

### Flexible

Supports reporting and automation simultaneously.

### Professional Workflow

Commonly used in penetration testing engagements.

---

## Limitations

### More Disk Space

Three files are created instead of one.

### Slightly More Management

Multiple files must be organized properly.

---

## Comparison of Output Options

| Option | Format      | Purpose                   |
| ------ | ----------- | ------------------------- |
| -oN    | Normal      | Human-readable reports    |
| -oX    | XML         | Automation and tools      |
| -oG    | Grepable    | Filtering and scripting   |
| -oA    | All Formats | Creates all three formats |

---

## Real-World Example

Command:

```bash
nmap -A -oA company_scan 10.10.10.0/24
```

Generated Files:

```text
company_scan.nmap
company_scan.xml
company_scan.gnmap
```

A penetration tester can:

* Read `.nmap` for analysis
* Import `.xml` into tools
* Use `.gnmap` with grep

without scanning again.

