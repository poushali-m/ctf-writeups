# Corrosion — Tomcat Exploitation & Privilege Escalation

## Overview

Full penetration test against a Linux target running Apache Tomcat. 
Achieved root access through a chain of web enumeration, credential 
extraction, Metasploit exploitation, hash cracking, and Python 
module hijacking.

## Attack Chain

| Step | Action | Tool |
|------|--------|------|
| 1 | Network scan — identified SSH, HTTP, Tomcat on port 8080 | Nmap |
| 2 | Web enumeration — discovered backup.zip via directory brute-force | dirb |
| 3 | ZIP password cracking using Rockyou wordlist | fcrackzip |
| 4 | Extracted tomcat-users.xml — obtained Tomcat Manager credentials | unzip |
| 5 | Exploited Tomcat Manager upload vulnerability | Metasploit |
| 6 | Extracted /etc/shadow hash for user randy | Meterpreter shell |
| 7 | Cracked SHA-512 hash using Rockyou wordlist | John the Ripper |
| 8 | SSH access as randy — identified sudo misconfiguration | SSH |
| 9 | Python base64 module was world-writable — injected reverse shell code | nano |
| 10 | Triggered sudo command — spawned root shell | sudo |

## Key Findings

- Apache Tomcat 9.0.53 Manager exposed with weak credentials
- Password-protected ZIP containing sensitive configuration files
- SHA-512 password hash crackable via dictionary attack
- World-writable Python standard library module exploitable for privilege escalation
- Root flag captured at /root/root.txt

## Techniques — MITRE ATT&CK Mapping

- T1046 — Network Service Scanning
- T1083 — File and Directory Discovery
- T1110.001 — Brute Force: Password Guessing
- T1505.003 — Server Software Component: Web Shell
- T1548.003 — Abuse Elevation Control Mechanism: Sudo

## Tools Used

- Nmap, dirb, fcrackzip, Metasploit Framework
- John the Ripper, SSH, nano

## Lessons Learned

- Exposed Tomcat Manager with default or weak credentials is a critical risk
- Configuration backup files should never be accessible via web server
- File permissions on system libraries must be strictly controlled
- Password hashes in /etc/shadow are crackable if weak passwords are used
