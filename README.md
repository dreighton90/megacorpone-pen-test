# 🛡️ MegaCorpOne Penetration Test

## 🧠 Executive Summary

This offensive security lab simulates a real-world penetration test against a fictional company, MegaCorpOne. The objective was to assess system vulnerabilities, exploit misconfigurations, and demonstrate post-exploitation techniques in a controlled lab environment. This project reflects a structured five-phase attack methodology and highlights hands-on skills in network scanning, credential harvesting, privilege escalation, and data exfiltration.

## ✅ Realism and Business Relevance

- Reflects tactics aligned with MITRE ATT&CK post-exploitation behavior  
- Simulates how real attackers move from initial access to full compromise  
- Demonstrates ability to identify misconfigurations, exploit them, and communicate impact clearly  

## 🚀 Scalability Beyond Bootcamp

This project can be extended by:

- Simulating Blue Team defense using ELK or Splunk log ingestion  
- Adding brute-force protection or access control hardening in a patched version  
- Integrating reporting pipelines with tools like Dradis or Markdown automation  

## 🔐 Vulnerability Summary

| Category              | Detail                                                                 |
|-----------------------|------------------------------------------------------------------------|
| Initial Access        | vsFTPd v2.3.4 backdoor (CVE-2011-2523)                                 |
| Exploitation Technique| Used Nmap to detect vsFTPd backdoor and gained shell access           |
| Privilege Escalation  | Harvested admin credentials from an exposed plaintext file            |
| Root Access           | Used `sudo -l` to confirm full sudo rights and gained root shell      |
| Post-Exploitation     | Accessed sensitive files, shadow password hash, and internal DNS data |
| Cleanup               | Used `history -c` to erase evidence                                   |

## 🔍 Phase Breakdown

### 1. Reconnaissance
- Google dorking and directory indexing revealed `/assets/`, `/about`, and `/jobs` pages  
- Used `nslookup` to discover MegaCorpOne's IP address  
- Used Shodan to identify exposed services and CVEs  
- Reviewed About Us and staff contact information to simulate open-source intel gathering  

### 2. Scanning & Enumeration
- Used HackerTarget for subdomain enumeration of `*.megacorpone.com`  
- Scanned target with Nmap to detect open ports and services  
- Discovered vsFTPd backdoor vulnerability on port 21  
- Identified HTTP file paths that contained credential leaks  

### 3. Exploitation
- Gained shell access via vsFTPd 2.3.4 backdoor  
- Located and dumped plaintext credentials from exposed `/tmp` file  
- Verified sudo rights for `msfadmin` user to prepare for privilege escalation  

### 4. Privilege Escalation
- Used harvested credentials to gain full shell access  
- Executed `sudo -l` to confirm unrestricted root access  
- Switched user to root and validated permissions  

### 5. Post-Exploitation
- Exfiltrated `/etc/shadow`, DNS data, and internal documentation  
- Ran internal enumeration commands to simulate lateral movement potential  
- Used `history -c` to clean terminal command logs  

## ⚠️ Legal Disclaimer

This project was conducted in a controlled lab environment. No systems, networks, or domains outside of the authorized lab scope were accessed. This content is for educational and professional development purposes only.
