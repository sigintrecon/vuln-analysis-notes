# Vulnerability Scanners: Architecture & Tools

Automated vulnerability testing ke liye infrastructure scanners aur web applications mapping utility ka overview:

## Infrastructure & Enterprise Scanners

### 1. Tenable Nessus Essentials
*   **Core Feature:** Industry standard scanner jo vulnerabilities, configuration mistakes, aur asset discovery ke liye use hota hai.
*   **Use Case:** Full enterprise audits, network assets scanning, compliance tracking.
*   **Advantage:** Unke plugin database ke update hone ki frequency bohot high hai.

### 2. Greenbone OpenVAS
*   **Core Feature:** Open-source platform jo core Linux distros (jaise Kali) par local network vulnerabilities audit karne ke liye full functional database deta hai.
*   **Use Case:** Free automated host detection aur port vulnerabilities check karne ke liye background execution setup.

## Specialized Web Scanners

### 3. Nikto
*   **Core Feature:** CLI web server configuration validation tool.
*   **Use Case:** Web servers (Apache, Nginx) ke default documentation directories, insecure options (`TRACE`), aur server banners check karna.
*   **Execution Command:** `nikto -h <target-ip>`

### 4. Nmap NSE (Nmap Scripting Engine)
*   **Core Feature:** Nmap ke custom Lua scripts jo target infrastructure ko trace aur verify karte hain.
*   **Use Case:** Specific vulnerability signature tracking using script directories.
*   **Execution Command:** `nmap --script=vuln <target-ip>`
