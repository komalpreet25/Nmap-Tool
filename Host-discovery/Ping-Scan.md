# Ping Scan (-sn)

## Introduction

Ping Scan is a host discovery technique used to identify active devices on a network. It allows security professionals and network administrators to determine which hosts are online before performing detailed scans.

Unlike a traditional port scan, Ping Scan focuses only on host discovery and does not scan ports.

---

## Why Ping Scan is Important

Before performing enumeration or vulnerability assessment, it is important to know which systems are active.

Benefits:

* Reduces scan time
* Identifies live hosts
* Helps create a network inventory
* Minimizes unnecessary traffic
* Useful during reconnaissance

---

## Syntax

```bash
nmap -sn <target>
```

Example:

```bash
nmap -sn 192.168.1.0/24
```

---

## Understanding the Command

### nmap

The Network Mapper tool used for network discovery and security auditing.

### -sn

Host discovery only.

Functions:

* Discover active hosts
* Skip port scanning
* Generate a list of reachable systems

### Target

Can be:

Single Host:

```bash
nmap -sn 192.168.1.10
```

Multiple Hosts:

```bash
nmap -sn 192.168.1.10 192.168.1.20
```

Subnet:

```bash
nmap -sn 192.168.1.0/24
```

---

## How Ping Scan Works

Nmap does not always use the Linux ping command.

Depending on the environment, Nmap may use:

### ARP Requests

Common on local networks.

Example:

Who has 192.168.1.10?

If the device replies, Nmap marks it as online.

### ICMP Echo Request

Similar to the traditional ping command.

Example:

```bash
ping 8.8.8.8
```

The target returns an ICMP Echo Reply if reachable.

### TCP ACK Probe

Nmap may send TCP ACK packets to determine whether a host exists.

### TCP SYN Probe

Nmap may send SYN packets to commonly used ports.

A response indicates the system is alive.

---

## Sample Scan

```bash
nmap -sn 192.168.1.0/24
```

Output:

```text
Nmap scan report for 192.168.1.1
Host is up.

Nmap scan report for 192.168.1.5
Host is up.

Nmap done: 256 IP addresses (2 hosts up)
```

---

## Interpreting Results

### Host is up

The device responded to discovery probes.

### Host seems down

The device did not respond.

Possible reasons:

* Device offline
* Firewall blocking probes
* ICMP disabled
* Network connectivity issues

---

## Advantages

* Fast scanning
* Low network traffic
* Useful for reconnaissance
* Helps identify targets before detailed scanning

---

## Limitations

* Firewalls can block probes
* Some devices disable ICMP
* Hidden hosts may not respond
* Results may vary depending on network configuration

---

## Related Commands

ARP Discovery

```bash
nmap -PR 192.168.1.0/24
```

No Ping Scan

```bash
nmap -Pn 192.168.1.10
```

SYN Scan

```bash
nmap -sS 192.168.1.10
```

---

