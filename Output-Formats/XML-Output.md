# XML Output (-oX)

## Introduction

XML Output is a structured output format provided by Nmap.

Unlike Normal Output, which is designed for humans to read, XML Output is designed for programs, scripts, and security tools to process automatically.

XML stands for:

```text
Extensible Markup Language
```

It stores scan information using tags and attributes, making it easier for other applications to understand and analyze Nmap results.

---

## Why XML Output?

Large organizations often perform thousands of scans.

Reading every result manually is difficult.

XML allows:

* Automation
* Report Generation
* Integration with Security Tools
* Vulnerability Management
* Data Analysis

---

## What is -oX?

The `-oX` option tells Nmap to save results in XML format.

Syntax:

```bash
nmap -oX <filename.xml> <target>
```

Example:

```bash
nmap -oX scan.xml 192.168.1.10
```

---

## How It Works

Command:

```bash
nmap -sS -sV -oX result.xml 192.168.1.10
```

Nmap performs the scan and saves the results in XML format.

---

## Sample XML Output

Example:

```xml
<?xml version="1.0"?>

<nmaprun>
  <host>
    <address addr="192.168.1.10"/>

    <ports>
      <port protocol="tcp" portid="22">
        <state state="open"/>
        <service name="ssh"/>
      </port>

      <port protocol="tcp" portid="80">
        <state state="open"/>
        <service name="http"/>
      </port>
    </ports>

  </host>
</nmaprun>
```

---

## Understanding XML Tags

### nmaprun

Root tag containing the entire scan.

Example:

```xml
<nmaprun>
```

---

### host

Represents a scanned host.

Example:

```xml
<host>
```

---

### address

Stores target IP information.

Example:

```xml
<address addr="192.168.1.10"/>
```

---

### port

Represents a scanned port.

Example:

```xml
<port protocol="tcp" portid="80">
```

---

### state

Shows port status.

Example:

```xml
<state state="open"/>
```

Possible values:

* open
* closed
* filtered

---

### service

Displays detected service.

Example:

```xml
<service name="http"/>
```

---

## Viewing XML Files

Linux:

```bash
cat result.xml
```

or

```bash
less result.xml
```

or

```bash
nano result.xml
```

---

## Formatting XML Output

To make XML easier to read:

```bash
xmllint --format result.xml
```

Example:

```bash
xmllint --format result.xml > formatted.xml
```

---

## Combining with Other Scans

### SYN Scan

```bash
nmap -sS -oX syn.xml target
```

---

### Version Detection

```bash
nmap -sV -oX services.xml target
```

---

### Aggressive Scan

```bash
nmap -A -oX aggressive.xml target
```

---

## XML Output for Automation

XML output can be processed by:

* Python Scripts
* Bash Scripts
* Reporting Tools
* Vulnerability Management Platforms
* Security Dashboards

Instead of manually reading results, software can extract:

* Open Ports
* Services
* Versions
* Host Information
* OS Detection Data

---

## Real-World Usage

XML Output is commonly used for:

* Enterprise Security Assessments
* Automated Reporting
* Vulnerability Management
* Security Monitoring
* Penetration Testing Documentation

---

## Advantages

### Machine Readable

Easy for tools and scripts.

### Structured Data

Information stored in organized tags.

### Automation Friendly

Perfect for large-scale scanning.

### Easy Integration

Works with many security tools.

---

## Limitations

### Difficult for Beginners

Less readable than Normal Output.

### Larger Files

XML contains many tags and metadata.

### Requires Parsing

Usually needs software or scripts for analysis.

---

## XML vs Normal Output

| Feature             | Normal Output | XML Output |
| ------------------- | ------------- | ---------- |
| Human Readable      | Yes           | Limited    |
| Automation Friendly | No            | Yes        |
| Reporting           | Good          | Excellent  |
| Tool Integration    | Limited       | Excellent  |
| Scripting Support   | Limited       | High       |





ty tools
* Better than Normal Output for scripting
