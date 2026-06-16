# Vulnerability Analysis

> **Part of my Cybersecurity Learning Path** — Documenting my journey toward eJPT → OSCP → Red Teaming  
> **Identity:** [SigintRecon](https://github.com/SigintRecon) | Aspiring Penetration Tester & Red Teamer

---

## About Me

I'm **Muhammad Umar**, a 19-year-old cybersecurity enthusiast from Faisalabad, Pakistan, actively building my skills in **web hacking, penetration testing, and red teaming** under the identity **"I learn web hacking."**

- **Goal:** eJPT → OSCP → Red Team Operations
- **Lab:** Kali Linux + Metasploitable2 + Windows 7 (VirtualBox)
- **Focus:** Manual exploitation, stealth techniques, professional reporting
- **GitHub:** [SigintRecon](https://github.com/SigintRecon)

---

## What's in This Repo

```
vuln-analysis-notes/
├── README.md                  ← You are here
├── notes/
│   ├── 01-va-vs-pentest.md    ← VA vs Penetration Testing
│   ├── 02-vuln-databases.md   ← CVE, NVD, Exploit-DB
│   ├── 03-cvss-scoring.md     ← CVSS v3.1 Deep Dive
│   ├── 04-tools-overview.md   ← Nessus, OpenVAS, Nikto, Nexpose
│   └── 05-manual-mapping.md   ← Manual Vulnerability Mapping
├── cheatsheets/
│   ├── nikto-cheatsheet.md    ← Nikto quick reference
│   ├── searchsploit-cheatsheet.md ← Searchsploit & Exploit-DB
│   └── cvss-calculator.md     ← CVSS scoring quick guide
├── report-template/
│   └── vulnerability-report-template.md ← Professional VA Report Template
└── assets/
    └── (diagrams)
```

---

## Module Topics Covered

| # | Topic | Status |
|---|-------|--------|
| 01 | Vulnerability Assessment vs Penetration Testing | ✅ Complete |
| 02 | Vulnerability Scanning Workflow | ✅ Complete |
| 03 | Vulnerability Databases (CVE, NVD, Exploit-DB) | ✅ Complete |
| 04 | Tools Overview: Nessus, OpenVAS, Nikto, Nexpose | ✅ Complete |
| 05 | Manual Vulnerability Mapping Techniques | ✅ Complete |
| 06 | CVSS Scoring System | ✅ Complete |
| 07 | Professional Vulnerability Report Writing | ✅ Complete |
| 08 | Practical Lab (Metasploitable2) | 🔄 In Progress |

---

## Tools Covered

| Tool | Type | Use Case |
|------|------|----------|
| **Nessus Essentials** | Automated Scanner | Full VA scans, compliance |
| **OpenVAS** | Open Source Scanner | Network vulnerability scanning |
| **Nikto** | Web Scanner | Web server misconfiguration detection |
| **Searchsploit** | CLI Tool | Offline Exploit-DB search on Kali |
| **Nmap NSE** | Scripted Scanner | Targeted vulnerability detection |

---

## Key Concepts

### VA vs Penetration Testing
- **VA** = Find and report vulnerabilities (no exploitation)
- **Pentest** = Find, exploit, and prove impact (full attack chain)

### CVE → NVD → Exploit-DB Workflow
```
Target service identified (e.g., vsftpd 2.3.4)
        ↓
Search CVE → CVE-2011-2523 found
        ↓
Check NVD → CVSS 10.0 Critical, backdoor exists
        ↓
Exploit-DB / Searchsploit → Working exploit found
        ↓
Manual exploitation
```

### CVSS Score Ranges
| Score | Severity |
|-------|----------|
| 9.0 – 10.0 | 🔴 Critical |
| 7.0 – 8.9 | 🟠 High |
| 4.0 – 6.9 | 🟡 Medium |
| 0.1 – 3.9 | 🟢 Low |

---

## Related Repositories

| Repo | Description |
|------|-------------|
| [sigintrecon](https://github.com/SigintRecon/sigintrecon) | Nmap cheatsheet for beginners |
| vuln-analysis-notes | This repo — Module 05 notes |

---

## Disclaimer

> All techniques documented here were practiced in a **controlled lab environment** (VirtualBox VMs) for **educational purposes only**. Never perform security testing on systems without **explicit written authorization**.

---

## Connect

- GitHub: [SigintRecon](https://github.com/SigintRecon)
- Open to collaborations and learning together

---

*"The quieter you become, the more you are able to hear."* — Kali Linux motto
