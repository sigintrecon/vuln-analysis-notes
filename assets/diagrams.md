# 1. VA vs Penetration Testing

```
                Vulnerability Assessment
                ------------------------
                Discover Assets
                       │
                       ▼
              Scan for Vulnerabilities
                       │
                       ▼
             Validate & Prioritize Findings
                       │
                       ▼
               Generate Security Report


                 Penetration Testing
                --------------------
                Reconnaissance
                       │
                       ▼
                 Enumeration
                       │
                       ▼
              Vulnerability Discovery
                       │
                       ▼
                  Exploitation
                       │
                       ▼
              Post-Exploitation
                       │
                       ▼
              Impact Demonstration
                       │
                       ▼
                Final Report
```

---

# 2. CVE → NVD → Exploit Workflow

```
      Service Enumeration
             │
             ▼
   Apache 2.4.49 Detected
             │
             ▼
      Search CVE Database
             │
             ▼
      Relevant CVE Found
             │
             ▼
     Review NVD Severity
             │
             ▼
     Check Exploit-DB or
       Searchsploit Entry
             │
             ▼
   Verify in Authorized Lab
             │
             ▼
     Document the Finding
```

---

# 3. Manual Vulnerability Mapping

```
        Open Port
            │
            ▼
     Banner Grabbing
            │
            ▼
  Identify Service Version
            │
            ▼
   Research Known Issues
            │
            ▼
     Cross-Reference CVEs
            │
            ▼
  Locate Public References
            │
            ▼
     Validate and Report
```

---

# 4. CVSS Base Metrics

```
              CVSS Base Score

      ┌─────────────────────────┐
      │ Attack Vector (AV)       │
      │ Attack Complexity (AC)   │
      │ Privileges Required (PR) │
      │ User Interaction (UI)    │
      │ Scope (S)                │
      │ Confidentiality (C)      │
      │ Integrity (I)            │
      │ Availability (A)         │
      └─────────────┬───────────┘
                    │
                    ▼
            Overall CVSS Score
                    │
                    ▼
        Low / Medium / High / Critical
```

---

# 5. Vulnerability Assessment Lifecycle

```
      Asset Discovery
             │
             ▼
       Service Enumeration
             │
             ▼
    Vulnerability Identification
             │
             ▼
      Risk Prioritization
             │
             ▼
         Validation
             │
             ▼
          Reporting
             │
             ▼
      Remediation Advice
```

---

# 6. Professional Report Workflow

```
      Information Gathering
                │
                ▼
      Technical Validation
                │
                ▼
       Risk Assessment
                │
                ▼
      Evidence Collection
                │
                ▼
      Remediation Guidance
                │
                ▼
       Executive Summary
                │
                ▼
      Final Client Report
```

---

## Tip

For a polished GitHub repository, create these diagrams as PNG or SVG files using tools like Draw.io, Excalidraw, or Mermaid, and reference them from your Markdown notes.
