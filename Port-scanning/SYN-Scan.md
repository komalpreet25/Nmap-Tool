# SYN Scan (-sS)

## Introduction

SYN Scan is the most popular and widely used port scanning technique in Nmap.

It is often called a **Half-Open Scan** because it does not complete the full TCP three-way handshake.

Instead of establishing a complete connection, Nmap sends a SYN packet, analyzes the response, and immediately terminates the connection.

Because the connection is never fully established, SYN Scan is faster and more stealthy than TCP Connect Scan.

---

## What is SYN?

SYN stands for **Synchronize**.

It is the first packet sent during the TCP three-way handshake.

Purpose:

```text id="u1nt79"
Request to establish a TCP connection.
```

---

## TCP Three-Way Handshake Review

Normal TCP communication:

### Step 1

Client sends:

```text id="t98p1n"
SYN
```

### Step 2

Server replies:

```text id="kp00jo"
SYN ACK
```

### Step 3

Client responds:

```text id="xlfq0e"
ACK
```

Connection established.

---

## How SYN Scan Works

Unlike TCP Connect Scan, Nmap stops before the final ACK.

### Open Port

Nmap sends:

```text id="i9m2ns"
SYN
```

Target responds:

```text id="mnkg9e"
SYN ACK
```

Nmap immediately sends:

```text id="bof2f2"
RST
```

Result:

```text id="o4xj0e"
Port Open
```

---

### Closed Port

Nmap sends:

```text id="ab5w88"
SYN
```

Target replies:

```text id="kxt9lq"
RST
```

Result:

```text id="vnmjlwm"
Port Closed
```

---

### Filtered Port

Nmap sends:

```text id="55j7q4"
SYN
```

No response or firewall interference.

Result:

```text id="d1r6qa"
Port Filtered
```

---

## Why Is It Called Half-Open Scan?

The TCP connection is never fully established.

Normal connection:

```text id="cnakb7"
SYN → SYN ACK → ACK
```

SYN Scan:

```text id="74i6l6"
SYN → SYN ACK → RST
```

Because the final ACK is never sent, the connection remains half-open.

---

## Syntax

```bash id="6kzsq5"
nmap -sS <target>
```

Example:

```bash id="s5v08i"
nmap -sS 192.168.1.10
```

---

## Sample Scan

```bash id="zj8j1v"
nmap -sS -p 22,80,443 192.168.1.10
```

Sample Output:

```text id="rjv23v"
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https
```

---

## Advantages

### Faster

No full TCP connection is created.

### More Stealthy

Many services do not log half-open connections.

### Efficient

Less network overhead.

### Widely Used

Default choice for many security professionals.

---

## Limitations

### Requires Privileges

Usually requires root or administrator privileges.

### Can Be Detected

Modern IDS and IPS solutions can identify SYN scans.

### Firewall Interference

Filtering devices may affect results.

---

## SYN Scan vs TCP Connect Scan

| Feature        | SYN Scan    | TCP Connect Scan |
| -------------- | ----------- | ---------------- |
| Option         | -sS         | -sT              |
| Full Handshake | No          | Yes              |
| Speed          | Faster      | Slower           |
| Stealth        | Higher      | Lower            |
| Detection      | Harder      | Easier           |
| Root Required  | Usually Yes | No               |

---

## Real-World Usage

Security professionals use SYN Scan for:

* Network reconnaissance
* Port discovery
* Penetration testing
* Security assessments
* Service identification preparation

---

## Common Port States

### Open

Application is listening.

### Closed

No service is listening.

### Filtered

Firewall prevents determination.

---

## Related Commands

TCP Connect Scan

```bash id="1vjlwm"
nmap -sT 192.168.1.10
```

UDP Scan

```bash id="7w77oj"
nmap -sU 192.168.1.10
```

Service Detection

```bash id="a5d7eu"
nmap -sS -sV 192.168.1.10
```

Aggressive Scan

```bash id="4fjlwm"
nmap -A 192.168.1.10
```


