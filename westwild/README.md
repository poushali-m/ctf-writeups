# WestWild — SMB Enumeration & Privilege Escalation

## Overview

Full compromise of the WestWild CTF machine through network scanning,
SMB enumeration, Base64 credential extraction, SSH access, lateral
movement via hidden script discovery, and privilege escalation to root.

## Attack Chain

| Step | Action | Tool |
|------|--------|------|
| 1 | Network scan — identified SSH(22), HTTP(80), SMB(139/445) | Nmap |
| 2 | SMB enumeration — discovered users aveng and wavex, share named wave | enum4linux |
| 3 | Connected to SMB share wave — downloaded FLAG1.txt and message_from_aveng.txt | smbclient |
| 4 | Base64 decoded FLAG1.txt — obtained SSH credentials for wavex | base64 |
| 5 | SSH login as wavex | SSH |
| 6 | Filesystem enumeration — found /usr/share/av/westsidesecret/ififoregt.sh | find |
| 7 | Script contained credentials for user aveng | cat |
| 8 | Switched to aveng — checked sudo privileges — allowed ALL commands | su, sudo -l |
| 9 | Escalated to root via sudo su | sudo |
| 10 | Retrieved FLAG2.txt from /root | cat |

## Key Findings

- SMB share accessible with guessable password (exam date)
- Sensitive credentials stored in Base64-encoded file on SMB share
- Hidden script in non-standard directory contained plaintext credentials
- User aveng had unrestricted sudo access — full root compromise
- Two flags retrieved: FLAG1 from SMB share, FLAG2 from /root

## Credentials Discovered

| User | Password | Source |
|------|----------|--------|
| wavex | door+open | Base64 decoded FLAG1.txt |
| aveng | kaizen+80 | Hidden script ififoregt.sh |

## Techniques — MITRE ATT&CK Mapping

- T1046 — Network Service Scanning
- T1021.002 — Remote Services: SMB
- T1083 — File and Directory Discovery
- T1140 — Deobfuscate/Decode Files or Information
- T1078 — Valid Accounts
- T1548.003 — Abuse Elevation Control Mechanism: Sudo

## Tools Used

- Nmap, enum4linux, smbclient, Metasploit, SSH, base64

## Lessons Learned

- SMB shares should never be accessible with guessable or date-based passwords
- Credentials must never be stored in plaintext scripts on the filesystem
- Base64 provides zero security — never use it to protect sensitive data
- Sudo ALL permissions should never be granted to regular users
