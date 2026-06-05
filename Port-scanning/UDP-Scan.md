# UDP Scan (-sU)

## Introduction

UDP Scan is used to discover open UDP ports on a target system.

Unlike TCP, UDP does not use a three-way handshake. Because there is no connection establishment process, determining whether a UDP port is open can be more difficult and slower.

Nmap uses the **-sU** option to perform UDP scanning.

---

## What is UDP?

UDP stands for **User Datagram Protocol**.

It is a connectionless transport layer protocol.

Unlike TCP, UDP:

* Does not establish a connection
* Does not guarantee delivery
* Does not guarantee packet order
* Is faster than TCP

---

## TCP vs UDP

| Feature        | TCP                 | UDP             |
| -------------- | ------------------- | --------------- |
| Connection     | Connection-Oriented | Connectionless  |
| Reliability    | Reliable            | Unreliable      |
| Handshake      | Yes                 | No              |
| Speed          | Slower              | Faster          |
| Error Checking | Extensive           | Basic           |
| Common Usage   | Web, SSH, FTP       | DNS, DHCP, VoIP |

---

## Common UDP Ports

| Port | Service     |
| ---- | ----------- |
| 53   | DNS         |
| 67   | DHCP Server |
| 68   | DHCP Client |
| 69   | TFTP        |
| 123  | NTP         |
| 161  | SNMP        |
| 162  | SNMP Trap   |
| 514  | Syslog      |

---

## How UDP Scan Works

Since UDP has no handshake, Nmap determines port states based on responses.

### Open Port

Nmap sends a UDP packet.

Target may:

```text
Respond with application data
```

Result:

```text
Port Open
```

---

### Closed Port

Nmap sends a UDP packet.

Target replies with:

```text
ICMP Port Unreachable
```

Result:

```text
Port Closed
```

---

### Open|Filtered Port

Nmap sends a UDP packet.

Target gives:

```text
No Response
```

Result:

```text
Open|Filtered
```

This is the most common UDP result.

Nmap cannot determine whether:

* Port is open
* Firewall is dropping packets

Therefore it displays:

```text
open|filtered
```

---

## UDP Scan Syntax

Basic scan:

```bash
nmap -sU <target>
```

Example:

```bash
nmap -sU 192.168.1.10
```

---

## Scan Specific UDP Ports

```bash
nmap -sU -p 53,67,68,161 192.168.1.10
```

---

## Scan All UDP Ports

```bash
nmap -sU -p- 192.168.1.10
```

Note:

```text
Very Slow
```

Because UDP scanning requires waiting for responses or timeouts.

---

## Service Detection with UDP

```bash
nmap -sU -sV 192.168.1.10
```

Nmap attempts to identify:

* DNS
* SNMP
* DHCP
* NTP
* Other UDP services

---

## Sample Output

Command:

```bash
nmap -sU 192.168.1.10
```

Output:

```text
PORT     STATE         SERVICE
53/udp   open          domain
123/udp  open          ntp
161/udp  open          snmp
69/udp   open|filtered tftp
```

---

## Why UDP Scans Are Slow

TCP:

```text
Immediate response usually received.
```

UDP:

```text
May receive no response.
```

Nmap must wait for timeout periods before deciding the state.

This makes UDP scanning significantly slower than TCP scanning.

---

## Advantages

### Finds Hidden Services

Many important services use UDP.

Examples:

* DNS
* SNMP
* NTP
* DHCP

### Complements TCP Scans

A complete security assessment should include both TCP and UDP scanning.

### Useful for Network Audits

Identifies exposed UDP services.

---

## Limitations

### Slow

UDP scans take more time.

### Inaccurate Results

Many ports appear:

```text
open|filtered
```

### Firewall Restrictions

Firewalls often block UDP traffic.

### High Timeout Rates

No response does not always mean a closed port.

---

## Real-World Usage

Cybersecurity professionals use UDP scans for:

* DNS enumeration
* SNMP discovery
* VoIP assessments
* Firewall testing
* Network audits

---

## Common Port States

### Open

Application responds.

### Closed

ICMP Port Unreachable received.

### Filtered

Firewall blocks packets.

### Open|Filtered

No response received.

Most common UDP state.

---

## Related Commands

SYN Scan

```bash
nmap -sS 192.168.1.10
```

TCP Connect Scan

```bash
nmap -sT 192.168.1.10
```

UDP Service Detection

```bash
nmap -sU -sV 192.168.1.10
```

Aggressive Scan

```bash
nmap -A 192.168.1.10
```


