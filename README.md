<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1a1b27,100:E31837&height=180&section=header&text=CTF%20Write-ups%20%26%20Pen%20Test%20Labs&fontSize=36&fontColor=ffffff&fontAlignY=38&desc=Documented%20attack%20chains%20%7C%20Kali%20Linux%20%7C%20MITRE%20ATT%26CK%20mapped&descAlignY=58&descSize=16&animation=fadeIn" />

[![Machines Completed](https://img.shields.io/badge/Machines%20Completed-5-E31837?style=for-the-badge&logo=hackthebox&logoColor=white)]()
[![Platform](https://img.shields.io/badge/Platform-VulnHub%20%7C%20HTB-9FEF00?style=for-the-badge&logo=hackthebox&logoColor=black)]()
[![OS](https://img.shields.io/badge/OS-Kali%20Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)]()
[![Methodology](https://img.shields.io/badge/Methodology-MITRE%20ATT%26CK-E31837?style=for-the-badge)]()

</div>

---

## 📌 About This Repository

This repository documents my hands-on penetration testing practice across CTF challenges and vulnerable lab machines. Each write-up follows a structured methodology — from initial reconnaissance through to privilege escalation — and maps techniques to the **MITRE ATT&CK framework**.

> ⚠️ All activities were conducted in **isolated, controlled lab environments** against intentionally vulnerable machines. For educational purposes only.

---

## 🗂️ Write-up Index

| # | 🖥️ Machine | 🎯 Difficulty | 🔑 Key Techniques | 🛠️ Tools |
|---|---|---|---|---|
| 01 | [🦀 Corrosion](./corrosion/) | Medium | Tomcat exploitation · ZIP cracking · Python module hijacking | Metasploit · fcrackzip · John the Ripper |
| 02 | [🎃 Mission Pumpkin](./mission-pumpkin/) | Easy | FTP enumeration · Base64 decoding · sudo misconfiguration | Nmap · Gobuster · SSH |
| 03 | [🤠 WestWild](./westwild/) | Easy | SMB enumeration · Lateral movement · Privilege escalation | enum4linux · smbclient · Metasploit |
| 04 | [🔍 Footprinting & Recon](./footprinting-recon/) | Beginner | TCP/UDP scanning · OS fingerprinting · Service discovery | Nmap · arp-scan |
| 05 | [📡 Network Scanning](./network-scanning/) | Beginner | Null/FIN scan analysis · Firewall detection · Port enumeration | Nmap |

---

## 🧠 Methodology

Each write-up follows the standard penetration testing lifecycle:

```
1. RECONNAISSANCE     →  Passive & active information gathering
2. ENUMERATION        →  Service/version detection, directory brute-forcing
3. EXPLOITATION       →  Vulnerability identification & initial access
4. POST-EXPLOITATION  →  Privilege escalation & lateral movement
5. REPORTING          →  Findings, impact analysis & lessons learned
```

---

## ⚔️ MITRE ATT&CK Coverage

<div align="center">

| Tactic | Techniques Practiced |
|---|---|
| 🔎 Reconnaissance | T1595 · T1046 · T1592 |
| 🚪 Initial Access | T1190 · T1078 · T1133 |
| ⚙️ Execution | T1059 · T1203 |
| 🔐 Privilege Escalation | T1548 · T1055 · T1574 |
| 🔗 Lateral Movement | T1021 · T1550 |
| 📦 Collection | T1083 · T1005 |

</div>

---

## 🛠️ Tools & Skills Demonstrated

<div align="center">

![Nmap](https://img.shields.io/badge/Nmap-214478?style=flat-square&logoColor=white)
![Metasploit](https://img.shields.io/badge/Metasploit-2596CD?style=flat-square&logoColor=white)
![Gobuster](https://img.shields.io/badge/Gobuster-333333?style=flat-square&logoColor=white)
![John the Ripper](https://img.shields.io/badge/John_the_Ripper-8B0000?style=flat-square&logoColor=white)
![enum4linux](https://img.shields.io/badge/enum4linux-4B0082?style=flat-square&logoColor=white)
![smbclient](https://img.shields.io/badge/smbclient-0078D4?style=flat-square&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

</div>

**Core skills practised across these labs:**
- Network reconnaissance and service enumeration
- Web application enumeration and directory brute-forcing  
- Credential extraction and password cracking
- Linux privilege escalation techniques
- SMB enumeration and lateral movement
- Structured incident documentation and reporting

---

## 📁 Repository Structure

```
ctf-writeups/
├── corrosion/
│   └── writeup.md
├── footprinting-recon/
│   └── writeup.md
├── mission-pumpkin/
│   └── writeup.md
├── network-scanning/
│   └── writeup.md
├── westwild/
│   └── writeup.md
└── README.md
```

---

## 👩‍💻 About the Author

**Poushali Majumder** — First-Class BSc Cyber Security Graduate, University of West London  
Aspiring Cyber Security Analyst based in London 🇬🇧

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/poushali23)
[![Portfolio](https://img.shields.io/badge/Portfolio-50C8A0?style=flat-square&logoColor=white)](https://poushali-m.github.io)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/poushali-m)

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:E31837,100:0d1117&height=100&section=footer" />

</div>
