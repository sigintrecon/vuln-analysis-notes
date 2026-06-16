# Vulnerability Databases: CVE, NVD, Exploit-DB

## The Three Pillars

```
CVE  →  Unique ID for every known vulnerability
NVD  →  Detailed profile of that vulnerability (CVSS, fix, references)
Exploit-DB → Actual exploit code for that vulnerability
```

---

## 1. CVE — Common Vulnerabilities and Exposures

- **Maintained by:** MITRE Corporation (US Government funded)
- **Purpose:** Assign a unique ID to every known vulnerability
- **Format:** `CVE-[YEAR]-[ID NUMBER]`

### Famous CVE Examples

| CVE ID | Vulnerability | Impact |
|--------|--------------|--------|
| CVE-2017-0144 | EternalBlue (MS17-010) | WannaCry ransomware |
| CVE-2021-44228 | Log4Shell | Remote Code Execution |
| CVE-2014-0160 | Heartbleed (OpenSSL) | Private key leakage |
| CVE-2011-2523 | vsftpd 2.3.4 backdoor | Root shell access |

> **Analogy:** CVE is like a vulnerability's **Aadhar Card** — unique ID, no details.

---

## 2. NVD — National Vulnerability Database

- **Maintained by:** NIST (US Government)
- **Website:** https://nvd.nist.gov
- **Purpose:** Full details for every CVE

### What NVD Gives You

- CVSS Base Score (severity rating)
- Affected software versions
- Patch/fix information
- Reference links
- CWE (weakness type)

> **Analogy:** NVD is the **full police record** — CVE is just the case number.

---

## 3. Exploit-DB

- **Maintained by:** Offensive Security (OSCP creators)
- **Website:** https://exploit-db.com
- **Purpose:** Working exploit code for known vulnerabilities

### What Exploit-DB Contains

- Working exploit scripts (Python, Ruby, C)
- Shellcodes
- Proof of Concept (PoC) code
- Paper writeups

> **Analogy:** CVE = FIR, NVD = FIR details, Exploit-DB = **how the crime was committed**

---

## Real Pentester Workflow

```bash
# Step 1: Found vsftpd 2.3.4 on target via Nmap
nmap -sV 192.168.1.100

# Step 2: Search Exploit-DB offline (Kali)
searchsploit vsftpd 2.3.4

# Step 3: Check CVE on NVD for CVSS score
# → CVE-2011-2523, CVSS 10.0 Critical

# Step 4: Copy exploit to working directory
searchsploit -m unix/remote/17491.rb

# Step 5: Exploit manually or via Metasploit
```

---

## Searchsploit Commands (Kali Linux)

```bash
# Basic search
searchsploit apache 2.4.49

# Search for specific OS
searchsploit windows 7 smb

# Copy exploit to current directory
searchsploit -m 17491.rb

# Show exploit path
searchsploit -p 17491

# Update exploit database
searchsploit -u
```

---

## Key Takeaway

> Never exploit blindly. Always:
> 1. Find CVE ID
> 2. Check NVD for CVSS + affected versions
> 3. Verify target version matches
> 4. Then look for exploit on Exploit-DB
