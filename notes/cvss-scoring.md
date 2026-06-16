# CVSS — Common Vulnerability Scoring System

## What is CVSS?

CVSS is a standardized framework to rate the **severity** of vulnerabilities on a scale of **0 to 10**.

Used by: NVD, Nessus, OpenVAS, security reports worldwide.

---

## Severity Ratings

| Score Range | Severity | Color |
|------------|----------|-------|
| 9.0 – 10.0 | Critical | 🔴 |
| 7.0 – 8.9 | High | 🟠 |
| 4.0 – 6.9 | Medium | 🟡 |
| 0.1 – 3.9 | Low | 🟢 |
| 0.0 | None | ⚪ |

---

## Three Score Types

### 1. Base Score
The **intrinsic nature** of the vulnerability — never changes.

Factors considered:
- Attack Vector (Network / Adjacent / Local / Physical)
- Attack Complexity (Low / High)
- Privileges Required (None / Low / High)
- User Interaction (None / Required)
- Impact on Confidentiality, Integrity, Availability

**Example:** EternalBlue Base Score = 8.1 (network exploitable, no auth needed)

---

### 2. Temporal Score
Reflects the **current state** of the vulnerability — changes over time.

Factors:
- Is an exploit publicly available? (Exploit-DB pe hai?)
- Is a patch released?
- How mature is the exploit code?

**Example:** When EternalBlue exploit was first public → Temporal score HIGH.  
After Microsoft patch release → Temporal score drops slightly.

---

### 3. Environmental Score
Reflects impact in **your specific environment**.

Factors:
- How critical is the affected system?
- What data is at risk?
- What security controls are in place?

**Example:**  
Same CVE on a hospital patient database → **Critical (10.0)**  
Same CVE on an isolated test VM → **Low (2.0)**

---

## CVSS Base Score Calculation

```
Base Score = f(Impact, Exploitability)

Impact Sub-score:
  → Confidentiality Impact + Integrity Impact + Availability Impact

Exploitability Sub-score:
  → Attack Vector + Complexity + Privileges + User Interaction
```

### Common CVE Examples with Scores

| CVE | Vulnerability | CVSS Score |
|-----|--------------|------------|
| CVE-2017-0144 | EternalBlue | 8.1 High |
| CVE-2021-44228 | Log4Shell | 10.0 Critical |
| CVE-2011-2523 | vsftpd Backdoor | 10.0 Critical |
| CVE-2014-0160 | Heartbleed | 7.5 High |

---

## Pentester's Practical Use

As a pentester, you mostly focus on **Base Score** from NVD.

**In reports:**
- Base Score = show to client for severity
- Environmental Score = adjust based on client's environment
- Temporal Score = mention if patch is available

---

## Key Takeaway

> CVSS is your **priority system**. Always fix Critical first, then High, then Medium.  
> Never waste time on Low severity when Critical issues exist.
