# Lab 2: Port Scanning

## Objective

Understand different types of port scanning techniques in Nmap and learn how to identify open ports on a target system.

---

## Lab Setup

Attacker Machine:

* Kali Linux / Linux terminal

Target:

* 192.168.1.10 (or any lab VM)

---

## What is Port Scanning?

Port scanning is the process of checking which ports are:

* Open
* Closed
* Filtered

Open ports indicate running services on the system.

---

## Step 1: Basic Scan

Command:

```bash id="p1k8qz"
nmap 192.168.1.10
```

### Explanation:

* Default scan
* Scans top 1000 ports
* Shows open ports only

---

## Step 2: TCP Connect Scan (-sT)

Command:

```bash id="m8v2lt"
nmap -sT 192.168.1.10
```

### Explanation:

* Full TCP connection is established
* Easy to detect by firewall/IDS
* Used when SYN scan is not allowed

---

## Step 3: SYN Scan (-sS)

Command:

```bash id="x7q9nv"
sudo nmap -sS 192.168.1.10
```

### Explanation:

* Half-open scan (stealth scan)
* Does not complete full TCP handshake
* Faster and more stealthy

---

## Step 4: UDP Scan (-sU)

Command:

```bash id="u4m8sd"
sudo nmap -sU 192.168.1.10
```

### Explanation:

* Scans UDP ports
* Slower than TCP scan
* Used for services like DNS, DHCP

---

## Step 5: Specific Port Scan

Command:

```bash id="c2k9rp"
nmap -p 22,80,443 192.168.1.10
```

### Explanation:

* Scans only selected ports
* Faster and focused

---

## Step 6: All Ports Scan

Command:

```bash id="f8n3qa"
nmap -p- 192.168.1.10
```

### Explanation:

* Scans all 65535 ports
* Takes more time
* Gives complete visibility

---

## Step 7: Service Version with Ports

Command:

```bash id="z9k2lm"
nmap -sS -sV 192.168.1.10
```

### Explanation:

* Detects open ports
* Identifies service versions

---

## Step 8: Fast Scan

Command:

```bash id="v1x8qp"
nmap -F 192.168.1.10
```

### Explanation:

* Scans only top common ports
* Very fast scan

---

## Comparison Table

| Scan Type      | Command | Speed     | Stealth |
| -------------- | ------- | --------- | ------- |
| TCP Connect    | -sT     | Medium    | Low     |
| SYN Scan       | -sS     | Fast      | High    |
| UDP Scan       | -sU     | Slow      | Medium  |
| Full Port Scan | -p-     | Slow      | High    |
| Fast Scan      | -F      | Very Fast | Low     |

---

## Real-World Usage

Port scanning is used for:

* Network reconnaissance
* Vulnerability assessment
* Security auditing
* Penetration testing

