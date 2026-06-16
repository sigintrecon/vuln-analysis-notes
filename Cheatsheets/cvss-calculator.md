# CVSS Calculator Cheat Sheet

## What is CVSS?

**CVSS (Common Vulnerability Scoring System)** is an industry-standard framework used to measure the severity of security vulnerabilities. It provides a score from **0.0 to 10.0**, helping security teams prioritize remediation efforts.

---

# CVSS Severity Ratings

| Score      | Severity |
| ---------- | -------- |
| 0.0        | None     |
| 0.1 – 3.9  | Low      |
| 4.0 – 6.9  | Medium   |
| 7.0 – 8.9  | High     |
| 9.0 – 10.0 | Critical |

---

# CVSS Base Metrics

## Attack Vector (AV)

| Value        | Meaning                                   |
| ------------ | ----------------------------------------- |
| Network (N)  | Exploitable remotely over a network       |
| Adjacent (A) | Requires access to the same local network |
| Local (L)    | Requires local system access              |
| Physical (P) | Requires physical access                  |

---

## Attack Complexity (AC)

| Value    | Meaning                                     |
| -------- | ------------------------------------------- |
| Low (L)  | No special conditions required              |
| High (H) | Requires uncommon conditions or preparation |

---

## Privileges Required (PR)

| Value    | Meaning                                        |
| -------- | ---------------------------------------------- |
| None (N) | No authentication required                     |
| Low (L)  | Basic user privileges needed                   |
| High (H) | Administrative or elevated privileges required |

---

## User Interaction (UI)

| Value        | Meaning                       |
| ------------ | ----------------------------- |
| None (N)     | No user action required       |
| Required (R) | Victim must perform an action |

---

## Scope (S)

| Value         | Meaning                                        |
| ------------- | ---------------------------------------------- |
| Unchanged (U) | Impact remains within the vulnerable component |
| Changed (C)   | Impact extends beyond the vulnerable component |

---

## Confidentiality Impact (C)

| Value    | Meaning                            |
| -------- | ---------------------------------- |
| None (N) | No data disclosure                 |
| Low (L)  | Limited information disclosure     |
| High (H) | Complete or significant disclosure |

---

## Integrity Impact (I)

| Value    | Meaning                          |
| -------- | -------------------------------- |
| None (N) | No modification possible         |
| Low (L)  | Limited data modification        |
| High (H) | Complete compromise of integrity |

---

## Availability Impact (A)

| Value    | Meaning                              |
| -------- | ------------------------------------ |
| None (N) | No service disruption                |
| Low (L)  | Reduced performance or interruptions |
| High (H) | Complete service disruption          |

---

# Example Vector Strings

## Remote Code Execution

```text
CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
```

Characteristics:

* Exploitable over the network
* No authentication required
* No user interaction
* Full confidentiality, integrity, and availability impact

---

## Authenticated Local Privilege Escalation

```text
CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H
```

Characteristics:

* Local access required
* Low privileges needed
* No user interaction
* High overall impact

---

## Reflected XSS

```text
CVSS:3.1/AV:N/AC:L/PR:N/UI:R/S:C/C:L/I:L/A:N
```

Characteristics:

* Remote attack
* Requires victim interaction
* Can affect another security scope
* Limited confidentiality and integrity impact

---

# Common Severity Examples

| Vulnerability              | Typical Severity |
| -------------------------- | ---------------- |
| Information Disclosure     | Low or Medium    |
| Open Directory Listing     | Low              |
| Stored XSS                 | Medium or High   |
| SQL Injection              | High or Critical |
| Remote Code Execution      | Critical         |
| Authentication Bypass      | Critical         |
| Command Injection          | Critical         |
| Weak TLS Configuration     | Low or Medium    |
| Default Credentials        | High             |
| Local Privilege Escalation | High             |

---

# Reading a CVSS Vector

Example:

```text
CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
```

Breakdown:

* **AV:N** → Network attack
* **AC:L** → Low complexity
* **PR:N** → No privileges required
* **UI:N** → No user interaction
* **S:U** → Scope unchanged
* **C:H** → High confidentiality impact
* **I:H** → High integrity impact
* **A:H** → High availability impact

---

# Quick Assessment Checklist

* Is the vulnerability remotely exploitable?
* Does it require authentication?
* Does it require victim interaction?
* Can it expose sensitive data?
* Can it modify data or execute commands?
* Can it cause denial of service?
* Does it affect systems beyond the vulnerable component?

---

# Notes

* CVSS is a prioritization tool, not a replacement for human judgment.
* Environmental context, business impact, and exploit availability should also be considered when assessing risk.
* Two vulnerabilities with the same CVSS score may require different remediation priorities depending on the target environment.
