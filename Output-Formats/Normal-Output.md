# Normal Output (-oN)

## Introduction

Normal Output is the standard human-readable output format provided by Nmap.

When Nmap scans a target, the results are displayed on the terminal screen by default.

Using the `-oN` option, these results can also be saved into a file for later analysis and reporting.

This is the most commonly used output format among beginners, system administrators, and security professionals.

---

## Why Save Scan Results?

Saving scan results helps:

* Keep records of scans
* Compare results over time
* Create reports
* Share findings with team members
* Document penetration testing activities

Without saving results, all information disappears when the terminal session ends.

---

## What is -oN?

The `-oN` option means:

```text
Output in Normal Format
```

Syntax:

```bash
nmap -oN <filename> <target>
```

Example:

```bash
nmap -oN scan.txt 192.168.1.10
```

---

## How It Works

### Without Saving

Command:

```bash
nmap 192.168.1.10
```

Result:

```text
Output displayed on screen only.
```

---

### With -oN

Command:

```bash
nmap -oN scan.txt 192.168.1.10
```

Result:

```text
Output displayed on screen
AND
Saved in scan.txt
```

---

## Example Scan

Command:

```bash
nmap -sS -oN result.txt 192.168.1.10
```

Output File:

```text
Starting Nmap

Nmap scan report for 192.168.1.10

PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https

Nmap done.
```

---

## Viewing Saved Results

Linux:

```bash
cat result.txt
```

or

```bash
less result.txt
```

or

```bash
nano result.txt
```

---

## Saving Version Detection Results

Command:

```bash
nmap -sV -oN services.txt target
```

Example Output:

```text
PORT   STATE SERVICE VERSION

22/tcp open ssh OpenSSH 9.0
80/tcp open http Apache 2.4.57
```

---

## Saving Aggressive Scan Results

Command:

```bash
nmap -A -oN aggressive.txt target
```

Saved Information:

* Open Ports
* Service Versions
* OS Detection
* NSE Results
* Traceroute

---

## Advantages of Normal Output

### Easy to Read

Human-readable format.

### Good for Reports

Simple and clean structure.

### Beginner Friendly

Easy to understand.

### Works Everywhere

Can be opened using any text editor.

---

## Limitations

### Not Machine Friendly

Difficult for automation tools to parse.

### Less Suitable for Scripting

XML is better for automation.

### Large Scans Create Large Files

May become lengthy.

---

## Real-World Usage

Normal Output is commonly used for:

* Security Audits
* Penetration Testing Reports
* Lab Documentation
* Learning and Practice
* Scan Record Keeping

---

## Related Output Formats

### XML Output

```bash
nmap -oX output.xml target
```

Used for automation and tools.

---

### Grepable Output

```bash
nmap -oG output.grep target
```

Used for filtering results.

---

### All Formats

```bash
nmap -oA output target
```

Saves results in multiple formats simultaneously.

---

## Key Points to Remember

* `-oN` = Normal Output
* Saves scan results into a text file
* Human-readable format
* Commonly used for reports
* Easy to view and share
* Default style of Nmap output
