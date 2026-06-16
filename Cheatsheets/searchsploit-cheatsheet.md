# Searchsploit & Exploit-DB Cheatsheet

> Searchsploit is Kali Linux's offline command-line tool to search the Exploit-DB database.

---

## Basic Commands

```bash
# Search for exploits
searchsploit <keyword>

# Examples
searchsploit vsftpd 2.3.4
searchsploit apache 2.4.49
searchsploit windows 7 smb
searchsploit php 5.3
```

---

## Common Options

```bash
# Copy exploit to current directory
searchsploit -m <exploit-id>
searchsploit -m 17491

# Show full path of exploit
searchsploit -p <exploit-id>

# Open exploit in browser (Exploit-DB website)
searchsploit -w vsftpd 2.3.4

# Exact match only (no fuzzy search)
searchsploit --exact vsftpd 2.3.4

# Search by CVE ID
searchsploit cve-2017-0144

# Update local exploit database
searchsploit -u

# Exclude results containing keyword
searchsploit apache --exclude="(PoC)"
```

---

## Output Format

```
------------------------------------------------
 Exploit Title                    |  Path
------------------------------------------------
vsftpd 2.3.4 - Backdoor Command  | unix/remote/17491.rb
                                  | unix/remote/49757.py
------------------------------------------------
```

- **Left column:** Exploit name and type
- **Right column:** Path in `/usr/share/exploitdb/exploits/`

---

## Exploit Categories

```
/exploits/
    linux/
    windows/
    unix/
    webapps/
    multiple/
    hardware/
```

---

## Workflow: Nmap to Exploit

```bash
# Step 1: Discover services
nmap -sV 192.168.1.100

# Output: vsftpd 2.3.4 on port 21

# Step 2: Search exploits
searchsploit vsftpd 2.3.4

# Step 3: Copy exploit
searchsploit -m unix/remote/17491.rb

# Step 4: Read exploit for instructions
cat 17491.rb | head -30

# Step 5: Execute (after understanding it)
ruby 17491.rb 192.168.1.100
```

---

## Metasploitable2 Common Findings

| Service | Version | Searchsploit Query |
|---------|---------|-------------------|
| vsftpd | 2.3.4 | `searchsploit vsftpd 2.3.4` |
| Samba | 3.x | `searchsploit samba 3` |
| Apache | 2.2.8 | `searchsploit apache 2.2` |
| PHP | 5.2 | `searchsploit php 5.2` |
| MySQL | 5.0 | `searchsploit mysql 5.0` |

---

## Key Notes

- Always **read the exploit** before running it
- Verify **target version** matches exploit requirements
- Check for **false positives** — not every result applies
- Prefer **manual exploitation** over automated scripts for learning
