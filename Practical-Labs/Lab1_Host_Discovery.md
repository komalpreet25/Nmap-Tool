# Lab 1: Host Discovery

## Objective

Learn how to identify active hosts on a network using Nmap.

## Lab Setup

Attacker Machine:
- Kali Linux

Target Network:
- 192.168.1.0/24

## Step 1: Ping Scan

Command:

nmap -sn 192.168.1.0/24

### Explanation

- -sn = Host Discovery Only
- No Port Scanning
- Finds live hosts

### Sample Output

Nmap scan report for 192.168.1.1
Host is up

Nmap scan report for 192.168.1.5
Host is up

## Step 2: ARP Scan

Command:

sudo nmap -sn 192.168.1.0/24

### Explanation

On local networks Nmap uses ARP requests for faster host discovery.

### Why ARP?

- Faster than ICMP
- More reliable on LANs
- Works even when ping is blocked

## Step 3: No Ping Scan

Command:

nmap -Pn 192.168.1.10

### Explanation

- Skip host discovery
- Assume host is online
- Useful when ICMP is blocked

## Verification

Compare results of:

nmap -sn 192.168.1.0/24

and

nmap -Pn 192.168.1.10

Observe differences.

## Key Learning

- Host Discovery identifies live systems.
- ARP is preferred on local networks.
- -Pn bypasses host discovery.


### When should you use -Pn?

When ICMP or host discovery probes are blocked.
