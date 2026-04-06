# Mission Pumpkin — CTF Full Compromise

## Overview

Full compromise of the Mission Pumpkin CTF machine through 
network discovery, FTP enumeration, Base64 credential extraction, 
SSH access, lateral movement, and privilege escalation via sudo misconfiguration.

## Attack Chain

| Step | Action | Tool |
|------|--------|------|
| 1 | Network scan — identified FTP(21), HTTP(1515), SSH(3535) | Nmap |
| 2 | Anonymous FTP login — retrieved note.txt hinting at hidden web content | ftp |
| 3 | Directory brute-force — discovered /img/hidden_secret/clue.txt | gobuster |
| 4 | Base64 decoded clue.txt — obtained SSH credentials for scarecrow | base64 |
| 5 | SSH login as scarecrow on custom port 3535 | SSH |
| 6 | Found passphrase in note.txt — switched to goblin user | su |
| 7 | Checked sudo privileges — goblin allowed ALL except /bin/su | sudo -l |
| 8 | Escalated to root via sudo -i | sudo |
| 9 | Retrieved and decoded final flag from /root/PumpkinGarden_Key | base64 |

## Key Findings

- FTP anonymous login enabled — exposed internal notes and hints
- Credentials hidden in Base64-encoded file in publicly accessible web directory
- SSH running on non-standard port 3535
- Overly permissive sudo configuration allowed full root access
- Final flag retrieved from /root/PumpkinGarden_Key

## Techniques — MITRE ATT&CK Mapping

- T1046 — Network Service Scanning
- T1021.001 — Remote Services: FTP
- T1083 — File and Directory Discovery
- T1140 — Deobfuscate/Decode Files or Information
- T1548.003 — Abuse Elevation Control Mechanism: Sudo

## Tools Used

- Nmap, ftp, gobuster, SSH, base64

## Lessons Learned

- Anonymous FTP access should always be disabled in production
- Sensitive credentials must never be stored in publicly accessible directories
- Base64 is encoding not encryption — never use it to protect credentials
- Sudo rules must follow least privilege — ALL permissions are extremely dangerous
