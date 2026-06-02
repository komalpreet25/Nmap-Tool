# Basic Nmap Commands

## Scan a Single Host

```bash
nmap 192.168.1.1
```

## Scan Multiple Hosts

```bash
nmap 192.168.1.1 192.168.1.2
```

## Scan a Subnet

```bash
nmap 192.168.1.0/24
```

## Scan Specific Port

```bash
nmap -p 80 192.168.1.1
```

## Scan Multiple Ports

```bash
nmap -p 22,80,443 192.168.1.1
```
