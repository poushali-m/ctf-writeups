# Network Scanning — Null & FIN Scan Analysis

## Overview

Advanced network scanning exercise using Null and FIN scan techniques
against multiple target systems. Analysis of how different operating
systems respond to non-standard TCP probes, and what this reveals
about firewall configurations and OS behaviour.

## Scope

| Machine | IP Address | OS |
|---------|-----------|-----|
| Metasploitable | 192.168.64.7 | Linux (Debian) |
| Windows 7 | 192.168.64.8 | Windows |
| Ubuntu | 192.168.64.10 | Linux (Ubuntu) |

## Scans Performed

### Null Scan (-sN)
Sends TCP packets with no flags set. Systems that follow RFC 793
should respond with RST for closed ports and no response for open ports.

### FIN Scan (-sF)
Sends TCP packets with only the FIN flag set. Used to bypass
basic stateless firewalls that only block SYN packets.

## Results

| OS | Null Scan Result | FIN Scan Result | Observation |
|----|-----------------|-----------------|-------------|
| Metasploitable | Ports 22,80 open/filtered, 443 closed | Same | Linux follows RFC 793 — RST confirms closed port |
| Windows 7 | Ports 22,80,443 open/filtered | Same | Windows sends no RST — all ports appear open/filtered |
| Ubuntu | Ports 22,80,443 closed | Same | RST responses — well-configured, ports confirmed closed |

## Key Findings

- Windows systems do not follow RFC 793 strictly — respond identically
  to both open and closed ports, making Null/FIN scans unreliable against Windows
- Linux systems (Metasploitable) follow RFC 793 — RST confirms closed ports
- Ubuntu's closed port responses suggest firewall rules or hardened configuration
- Null and FIN scans can bypass simple stateless firewalls

## Techniques — MITRE ATT&CK Mapping

- T1046 — Network Service Scanning
- T1595.001 — Active Scanning: Scanning IP Blocks

## Tools Used

- Nmap 7.95 (-sN null scan, -sF FIN scan)

## Lessons Learned

- Null and FIN scans are unreliable against Windows targets
- Different OS TCP/IP implementations affect scan reliability
- Understanding RFC 793 behaviour is essential for accurate port scanning
- Firewalls can mask true port states — multiple scan techniques needed
