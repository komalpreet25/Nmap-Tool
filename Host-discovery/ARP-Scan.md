# ARP Scan (-PR)

## Introduction

ARP (Address Resolution Protocol) Scan is a host discovery technique used to identify active devices on a Local Area Network (LAN).

Nmap sends ARP Requests to target systems and listens for ARP Replies. If a device responds, Nmap marks the host as online.

ARP Scan is one of the fastest and most reliable host discovery methods on local networks.

---

## What is ARP?

ARP stands for Address Resolution Protocol.

Its purpose is to map an IPv4 address to a MAC address.

Example:

```text
IP Address  : 192.168.1.10
MAC Address : 08:00:27:AB:CD:EF
```

Before sending data inside a LAN, a device must know the destination MAC address.

ARP helps perform this mapping.

---

## Why Does Nmap Use ARP?

On local networks, ARP is more reliable than ICMP because:

* ARP cannot usually be blocked by local firewalls
* Most devices must respond to ARP requests
* Faster than traditional ICMP discovery
* Produces more accurate results

For this reason, Nmap automatically prefers ARP discovery on local Ethernet networks.

---

## ARP Communication Process

Suppose Nmap wants to discover:

```text
192.168.1.10
```

### Step 1: ARP Request

Nmap broadcasts:

```text
Who has 192.168.1.10?
Tell 192.168.1.5
```

### Step 2: ARP Reply

Target responds:

```text
192.168.1.10 is at 08:00:27:AB:CD:EF
```

### Step 3: Host Identified

Nmap marks the host as:

```text
Host is up
```

---

## Syntax

```bash
nmap -PR <target>
```

Example:

```bash
nmap -PR 192.168.1.0/24
```

---

## Understanding the Command

### nmap

Network Mapper tool.

### -PR

ARP Host Discovery.

Forces Nmap to use ARP Requests for host discovery.

### Target

Single Host:

```bash
nmap -PR 192.168.1.10
```

Multiple Hosts:

```bash
nmap -PR 192.168.1.10 192.168.1.20
```

Subnet:

```bash
nmap -PR 192.168.1.0/24
```

---

## Sample Scan

```bash
nmap -PR 192.168.1.0/24
```

Sample Output:

```text
Nmap scan report for 192.168.1.1
Host is up.

Nmap scan report for 192.168.1.10
Host is up.

Nmap scan report for 192.168.1.20
Host is up.

Nmap done: 256 IP addresses (3 hosts up)
```

---

## ARP Scan vs ICMP Ping

| Feature             | ARP Scan  | ICMP Ping      |
| ------------------- | --------- | -------------- |
| Network Type        | Local LAN | Local & Remote |
| Uses MAC Address    | Yes       | No             |
| Uses ICMP           | No        | Yes            |
| Firewall Resistance | High      | Lower          |
| Accuracy on LAN     | Very High | Moderate       |

---

## Advantages

### Fast Discovery

ARP requests are lightweight and fast.

### Reliable Results

Most active devices respond to ARP.

### Firewall Bypass

Even if ICMP is blocked, ARP often succeeds.

### Better LAN Visibility

Excellent for internal network mapping.

---

## Limitations

### Local Networks Only

ARP does not work across routers.

### Cannot Discover Internet Hosts

ARP is restricted to the local broadcast domain.

### Layer 2 Dependency

Works only within the same LAN segment.

---

## When Should You Use ARP Scan?

Use ARP Scan when:

* Scanning a local network
* Discovering active devices
* Mapping internal infrastructure
* Preparing for enumeration
* ICMP discovery is unreliable

---

## Related Commands

Standard Host Discovery

```bash
nmap -sn 192.168.1.0/24
```

No Ping Scan

```bash
nmap -Pn 192.168.1.10
```

SYN Scan

```bash
nmap -sS 192.168.1.10
```



### Why does Nmap prefer ARP on local networks?

ARP discovery is faster, more accurate, and less affected by firewall rules than ICMP-based discovery.
