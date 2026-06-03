# No Ping Scan (-Pn)

## Introduction

A No Ping Scan is an Nmap scanning technique that skips the host discovery phase and assumes the target host is online.

Normally, Nmap first checks whether a host is alive before performing port scans. This process is known as host discovery.

However, some systems block ICMP Echo Requests and other discovery probes through firewalls. In such situations, Nmap may incorrectly report the host as down.

The `-Pn` option instructs Nmap to skip host discovery and scan the target directly.

---

## Why is No Ping Scan Needed?

Many organizations configure firewalls to block:

* ICMP Echo Requests
* ICMP Echo Replies
* TCP Discovery Probes
* UDP Discovery Probes

As a result, a live system may appear offline.

Using `-Pn` helps bypass this issue by treating the target as active.

---

## How Normal Scanning Works

Without `-Pn`:

```bash
nmap 192.168.1.10
```

### Step 1

Nmap performs host discovery.

### Step 2

Nmap determines whether the host is alive.

### Step 3

If the host responds, Nmap starts port scanning.

### Problem

If discovery probes are blocked, Nmap may report:

```text id="fd8q1v"
Host seems down.
```

Even when the system is actually online.

---

## How No Ping Scan Works

With `-Pn`:

```bash
nmap -Pn 192.168.1.10
```

### Step 1

Skip host discovery.

### Step 2

Assume the host is online.

### Step 3

Start scanning ports immediately.

---

## Syntax

```bash
nmap -Pn <target>
```

Example:

```bash
nmap -Pn 192.168.1.10
```

---

## Understanding the Command

### nmap

Network Mapper tool.

### -Pn

Treat all hosts as online.

Skip host discovery and proceed directly to scanning.

### Target

Single Host:

```bash
nmap -Pn 192.168.1.10
```

Multiple Hosts:

```bash
nmap -Pn 192.168.1.10 192.168.1.20
```

Subnet:

```bash
nmap -Pn 192.168.1.0/24
```

---

## Example Scan

```bash
nmap -Pn 192.168.1.10
```

Sample Output:

```text id="a4hr2l"
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https
```

Even if the host blocks ICMP requests, Nmap can still identify open ports.

---

## Real-World Scenario

Suppose a company's firewall blocks all ICMP traffic.

Normal scan:

```bash
nmap 192.168.1.10
```

Output:

```text id="94szdp"
Host seems down.
```

No Ping Scan:

```bash
nmap -Pn 192.168.1.10
```

Output:

```text id="m4e4p9"
22/tcp open ssh
80/tcp open http
```

The system was online, but host discovery was blocked.

---

## Advantages

### Bypass Host Discovery Restrictions

Useful when ICMP is blocked.

### Discover Hidden Hosts

Can identify systems that ignore discovery probes.

### Better for Firewall-Protected Targets

Works against many filtered environments.

### Useful During Security Assessments

Commonly used in penetration testing and reconnaissance.

---

## Limitations

### Slower Scans

Nmap scans every target because it assumes all hosts are online.

### Increased Network Traffic

More packets are sent compared to normal host discovery.

### Less Efficient for Large Networks

Scanning inactive hosts wastes time.

---

## When Should You Use -Pn?

Use `-Pn` when:

* ICMP is blocked
* Firewalls filter discovery probes
* Hosts appear down unexpectedly
* Conducting security assessments
* Scanning protected environments

---

## Related Commands

Host Discovery Only

```bash
nmap -sn 192.168.1.0/24
```

ARP Discovery

```bash
nmap -PR 192.168.1.0/24
```

SYN Scan

```bash
nmap -sS -Pn 192.168.1.10
```

Version Detection

```bash
nmap -sV -Pn 192.168.1.10
```

---

## Difference Between -sn and -Pn

| Option | Purpose                                       |
| ------ | --------------------------------------------- |
| `-sn`  | Host discovery only, no port scan             |
| `-Pn`  | Skip host discovery and assume host is online |

---

## Key Interview Questions

### What does -Pn do in Nmap?

It skips host discovery and treats the target as online.

### Why would you use -Pn?

When ICMP or other discovery probes are blocked by a firewall.

### Does -Pn guarantee that a host is online?

No. Nmap simply assumes the host is online and attempts to scan it.

### Is -Pn faster than normal scanning?

No. It is usually slower because Nmap scans targets without first verifying whether they are active.

### What is the difference between -sn and -Pn?

`-sn` performs only host discovery, while `-Pn` skips host discovery and proceeds directly to scanning.
