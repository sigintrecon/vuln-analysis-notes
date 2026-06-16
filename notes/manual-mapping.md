# Manual Vulnerability Mapping Techniques

Automated vulnerability scanners (such as Nessus or OpenVAS) often generate excessive noise, produce false positives, and may miss critical logic flaws. Professional penetration testers and red teamers frequently rely on **manual vulnerability mapping** to perform targeted, stealthy, and accurate assessments.

Manual mapping involves extracting information from the target infrastructure, analyzing service banners, correlating versions with known CVEs, and locating verified proof-of-concept (PoC) exploits without triggering noisy automated scans.

---

# 1. The Manual Mapping Methodology

Manual vulnerability mapping follows a structured three-stage process:

1. **Information Pull (Banner Grabbing)** – Connect to exposed services and extract software signatures and version information.
2. **Signature Analysis & Cross-Referencing** – Compare extracted versions against public vulnerability databases such as CVE and NVD.
3. **Exploit Availability Verification** – Search local exploit archives and open-source repositories for publicly available proof-of-concept code.

---

# 2. Banner Grabbing & Service Identification

Banner grabbing is the first and one of the most important steps in manual vulnerability mapping. Many services reveal their software name, version, or operating system when a client establishes a connection.

## A. Netcat (`nc`) Implementation

Netcat is often called the **Swiss Army Knife of Cybersecurity** because it allows raw TCP and UDP connections.

### General Syntax

```bash
nc -nv <Target-IP> <Port>
```

### Example: FTP Banner Grabbing

```bash
nc -nv 192.168.1.10 21
```

**Expected Output**

```text
(UNKNOWN) [192.168.1.10] 21 (ftp) open
220 (vsFTPd 2.3.4)
```

### Analysis

The banner reveals:

* Software: `vsFTPd`
* Version: `2.3.4`

This information is obtained without performing an aggressive automated vulnerability scan.

---

## B. Telnet Banner Grabbing

If Netcat is unavailable or blocked, Telnet can also be used to retrieve service banners.

### Example

```bash
telnet 192.168.1.10 80
HEAD / HTTP/1.0
```

**Expected Output**

```text
HTTP/1.1 200 OK
Server: Apache/2.2.8 (Ubuntu) DAV/2
Content-Type: text/html; charset=UTF-8
```

### Analysis

The server discloses:

* Web Server: `Apache`
* Version: `2.2.8`
* Platform: `Ubuntu Linux`

---

## C. Lightweight Nmap Version Detection

Instead of using aggressive scans (`-A`), a safer approach is to perform targeted service detection.

```bash
nmap -sS -sV -sC -p 21,22,80,445 <Target-IP>
```

Where:

* `-sS` → SYN scan
* `-sV` → Service/version detection
* `-sC` → Default safe scripts
* `-p` → Scan only specified ports

---

# 3. Vulnerability Cross-Referencing (CVE/NVD Mapping)

Once an exact software version is identified (for example `Apache 2.4.49` or `Samba 3.0.20`), it can be manually correlated with public vulnerability databases.

```text
Extracted Signature (Samba 3.0.20)
         │
         ▼
MITRE CVE Database
         │
         ▼
Identifies CVE-2007-2447
         │
         ▼
NVD (NIST)
         │
         ▼
Severity Analysis (e.g. CVSS Score)
```

## Manual Search Queries

```text
site:cve.mitre.org "Samba 3.0.20"

intitle:"vulnerability" "Tomcat 5.5"

"vsftpd 2.3.4" site:nvd.nist.gov
```

These searches help locate vendor advisories and vulnerability records for identified software versions.

---

# 4. Exploit Verification with Searchsploit

Kali Linux ships with an offline copy of Exploit-DB that can be queried using `searchsploit`.

## Common Commands

| Task                 | Command                          |
| -------------------- | -------------------------------- |
| Basic search         | `searchsploit vsftpd 2.3.4`      |
| Exact match          | `searchsploit -e "Samba 3.0.20"` |
| View exploit source  | `searchsploit -x 16320`          |
| Copy exploit locally | `searchsploit -m 16320`          |
| Search by CVE        | `searchsploit --cve 2017-7494`   |

---

## Practical Example

Suppose enumeration identifies `Samba 3.0.20`.

```bash
searchsploit samba 3.0.20
```

**Example Output**

```text
-------------------------------------------------- ---------------------------------
 Exploit Title                                    | Path
-------------------------------------------------- ---------------------------------
 Samba 3.0.20 < 3.0.25rc3 - 'Username' Remote Co  | linux/remote/16320.rb
-------------------------------------------------- ---------------------------------
```

To inspect the exploit source:

```bash
searchsploit -x linux/remote/16320.rb
```

### Insight

Reviewing exploit source code helps analysts understand implementation details, affected versions, and execution flow before deciding whether additional investigation or testing is appropriate within an authorized environment.

---

# 5. Manual vs Automated Mapping

| Scenario              | Automated Scanner                                           | Manual Mapping                                                  |
| --------------------- | ----------------------------------------------------------- | --------------------------------------------------------------- |
| Network Noise         | High; may generate many requests and trigger IDS/WAF alerts | Low; typically involves focused interactions                    |
| False Positives       | Can occur due to version-based assumptions                  | Reduced through manual verification                             |
| Business Logic Issues | Often misses authorization flaws or workflow issues         | Better suited for identifying logic and access-control problems |
| Speed                 | Fast across large environments                              | Slower but often more precise for individual targets            |

---

# Best Practices

* Verify version information using multiple sources when possible.
* Do not rely solely on service banners, as they may be altered or hidden.
* Cross-reference findings with trusted vulnerability databases.
* Review exploit code carefully before drawing conclusions.
* Document evidence and validation steps throughout the assessment.

---

# Disclaimer

These techniques should only be used on systems that you own or for which you have explicit authorization to assess. Unauthorized scanning, enumeration, or exploitation attempts against third-party infrastructure may violate laws, contracts, or acceptable-use policies.
