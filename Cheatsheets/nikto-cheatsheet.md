# Nikto Cheatsheet

> Nikto is an open-source web server scanner that detects dangerous files, outdated software, and misconfigurations.

---

## Basic Syntax

```bash
nikto -h <target>
```

---

## Common Commands

```bash
# Basic scan against a host
nikto -h 192.168.1.100

# Scan specific port
nikto -h 192.168.1.100 -p 8080

# Scan HTTPS target
nikto -h https://192.168.1.100

# Save output to file
nikto -h 192.168.1.100 -o output.txt

# Save as HTML report
nikto -h 192.168.1.100 -o report.html -Format htm

# Scan with specific tuning (attack type)
nikto -h 192.168.1.100 -Tuning 1

# Scan with authentication
nikto -h 192.168.1.100 -id admin:password

# Scan through a proxy
nikto -h 192.168.1.100 -useproxy http://127.0.0.1:8080

# Scan multiple hosts from file
nikto -h targets.txt

# Verbose output
nikto -h 192.168.1.100 -Display V
```

---

## Tuning Options (-Tuning)

| Number | Type |
|--------|------|
| 0 | File Upload |
| 1 | Interesting File / Seen in logs |
| 2 | Misconfiguration / Default File |
| 3 | Information Disclosure |
| 4 | Injection (XSS/Script/HTML) |
| 5 | Remote File Retrieval — Inside Web Root |
| 6 | Denial of Service |
| 7 | Remote File Retrieval — Server Wide |
| 8 | Command Execution / Remote Shell |
| 9 | SQL Injection |
| a | Authentication Bypass |
| b | Software Identification |
| c | Remote Source Inclusion |

---

## Practical: Scan Metasploitable2

```bash
# Get Metasploitable2 IP first
# Then:
nikto -h 192.168.x.x -o metasploitable-scan.html -Format htm
```

**What Nikto will find on Metasploitable2:**
- Outdated Apache version
- PHP vulnerabilities
- Default credentials pages
- Directory listing enabled
- Dangerous HTTP methods (PUT, DELETE)

---

## Output Fields Explained

```
+ Server: Apache/2.2.8          ← Web server version (check for CVEs)
+ /phpMyAdmin/: phpMyAdmin      ← Interesting path found
+ OSVDB-877: ...                ← Old vulnerability DB reference
+ CVE-2011-xxxx: ...            ← Direct CVE reference
```

---

## Limitations of Nikto

- Very **noisy** — easily detected by IDS/WAF
- Can produce **false positives** — always verify manually
- Does not exploit, only identifies
- Not suitable for stealth scanning

---

## After Nikto Scan

1. Note all CVE IDs found
2. Check each on NVD for CVSS score
3. Search Exploit-DB: `searchsploit <service> <version>`
4. Verify manually before including in report
5. Document as findings with evidence
