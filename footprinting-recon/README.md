# Footprinting & Reconnaissance — Network Discovery Lab

## Overview

Structured reconnaissance exercise against multiple target systems
using TCP/UDP port scanning, service version detection, and OS
fingerprinting. Targets included Metasploitable, Windows 7, and Ubuntu VMs.

## Scope

| Machine | IP Address | OS |
|---------|-----------|-----|
| Metasploitable | 192.168.64.7 | Linux (Debian) |
| Windows 7 | 192.168.64.1 | Windows |

## Tasks Performed

### Task 1 — TCP Port Scanning
Identified open TCP ports and running services on both targets using Nmap top-ports scan.

### Task 2 — UDP Port Scanning
Identified open and filtered UDP ports including DNS, DHCP, NetBIOS, and TFTP services.

### Task 3 — OS Fingerprinting
Used Nmap OS detection to identify operating systems and confirm target environments.

## Key Findings

| Target | Open TCP Ports | OS Detected |
|--------|---------------|-------------|
| Metasploitable | 21,22,23,25,53,80,111,139,445,3306,5900 | Linux 2.6.x |
| Windows 7 | 53 | macOS (fingerprint anomaly) |

## Techniques Used

- TCP SYN scan (-sT) for port discovery
- UDP scan (-sU) for UDP service identification
- OS detection (-O) for fingerprinting
- Service version detection (-sV)

## Tools Used

- Nmap 7.95
- arp-scan

## Lessons Learned

- Metasploitable exposes a large attack surface with many unnecessary services
- UDP scanning is slower and less reliable than TCP but reveals additional services
- OS fingerprinting can produce anomalous results depending on network configuration
- Reconnaissance is the critical first step of any penetration test
