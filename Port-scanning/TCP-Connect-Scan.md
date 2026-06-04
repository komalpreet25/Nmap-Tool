
TCP Connect Scan (-sT)

Introduction

TCP Connect Scan is one of the most basic and reliable scanning techniques in Nmap.

It uses the operating system's networking functions to establish a complete TCP connection with the target port. Because it completes the entire TCP three-way handshake, it is easy to detect in logs but highly accurate.

TCP Connect Scan is commonly used when the user does not have administrative or root privileges.

---

What is TCP?

TCP (Transmission Control Protocol) is a connection-oriented protocol used to provide reliable communication between devices.

Common TCP Services:

Port| Service
22| SSH
80| HTTP
443| HTTPS
21| FTP
25| SMTP

---

TCP Three-Way Handshake

Before communication begins, TCP establishes a connection using a three-step process.

Step 1: SYN

Client sends:

SYN

Meaning:

Can we communicate?

Step 2: SYN-ACK

Server responds:

SYN ACK

Meaning:

Yes, let's communicate.

Step 3: ACK

Client replies:

ACK

Meaning:

Connection established.

The connection is now fully established.

---

How TCP Connect Scan Works

Nmap attempts to complete the entire TCP handshake.

Open Port

Target:

SYN → SYN-ACK → ACK

Result:

Port Open

Closed Port

Target:

SYN → RST

Result:

Port Closed

Filtered Port

No response or firewall filtering.

Result:

Port Filtered

---

Syntax

nmap -sT <target>

Example:

nmap -sT 192.168.1.10

---

Understanding the Command

nmap

Network Mapper tool.

-sT

Perform a TCP Connect Scan.

Target

The system being scanned.

---

Example

Scan a single host:

nmap -sT 192.168.1.10

Scan specific ports:

nmap -sT -p 22,80,443 192.168.1.10

---

Sample Output

PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

Explanation:

- Port 22 is open
- Port 80 is open
- Port 443 is open

---

Advantages

Highly Accurate

Completes the full TCP connection.

No Root Privileges Required

Works without administrative access.

Reliable Results

Uses the operating system's networking stack.

Easy to Understand

Ideal for beginners learning port scanning.

---

Limitations

Easily Detected

The full TCP connection is visible in logs.

More Noise

Creates more network traffic than SYN scans.

Slower Than SYN Scan

Must complete the entire handshake.

---

When Should You Use TCP Connect Scan?

Use TCP Connect Scan when:

- You do not have root privileges
- Performing basic network enumeration
- Learning Nmap scanning techniques
- Reliability is more important than stealth

---

TCP Connect Scan vs SYN Scan

Feature| TCP Connect Scan| SYN Scan
Option| -sT| -sS
Full Handshake| Yes| No
Root Required| No| Usually Yes
Stealth| Low| High
Detection| Easy| Harder
Speed| Slower| Faster

---

Real-World Usage

Security professionals use TCP Connect Scan to:

- Identify open services
- Verify network exposure
- Enumerate systems
- Troubleshoot connectivity issues
