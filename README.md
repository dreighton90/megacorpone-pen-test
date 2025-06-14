# 🛡️ MegaCorpOne Penetration Test

This project documents a simulated penetration test engagement performed against a fictional company, **MegaCorpOne**. The engagement followed a structured five-phase methodology commonly used by red teamers and offensive security professionals.

> ✅ **Goal:** Identify vulnerabilities, exploit weaknesses, and gain root access using real-world tools and tactics in a lab-based environment.

---

## 📌 Engagement Overview

- **Target Domain:** `megacorpone.com`
- **Scope:** External (Internet-facing)
- **Environment:** Lab-based (Kali Linux + Metasploitable)
- **Methodology:** Reconnaissance → Scanning → Enumeration → Exploitation → Privilege Escalation → Reporting

---

## 🔍 Phase 1: Reconnaissance

- Performed passive DNS recon using `nslookup` and `dig`
- Conducted subdomain and IP discovery
- Utilized `Google Dorking` to uncover sensitive directories and pages

📸 `Screenshots:`  
- DNS resolution and domain IP discovery  
- Open directory listing (`/assets/`)  
- Google search results using `site:megacorpone.com`

---

## 📡 Phase 2: Scanning & Enumeration

- Scanned target using `nmap` for open ports and services
- Investigated the IP `149.56.244.87` on Shodan to enumerate exposed services
- Identified Apache httpd vulnerabilities and OpenSSH fingerprints

📸 `Screenshots:`  
- Open ports: 22 (SSH), 80 (HTTP), 443 (HTTPS)  
- Apache CVEs and service versions  
- Bootstrap and jQuery JS libraries loaded in the web tech stack

---

## 🛠️ Phase 3: Exploitation

- Exploited vulnerable `vsFTPd 2.3.4` service (CVE-2011-2523) to gain shell access
- Used `Metasploit smb_login` module for brute-force authentication
- Captured SMB/NTLMv2 hashes using `Responder`

📸 `Screenshots:`  
- Metasploit configuration and module output  
- Responder poisoning output  
- Cracked credentials and valid SSH login

---

## 🚀 Phase 4: Post-Exploitation

- Logged in with `msfadmin:cybersecurity` over SSH  
- Confirmed root-level access using `sudo -i`
- Located sensitive files and credentials (e.g., `adminpassword.txt`)
- Identified various `tiki-admin` configuration files and CMS modules

📸 `Screenshots:`  
- Credential reuse from config files  
- Escalated privilege session  
- Directory traversal and information disclosure

---

## 📑 Final Report Summary

| Metric            | Value          |
|-------------------|----------------|
| Total Hosts       | 17             |
| Vulnerabilities   | 5+             |
| Credentials Found | 2              |
| Access Gained     | Root (SSH)     |

- Tools Used: `nmap`, `Shodan`, `Metasploit`, `Responder`, `Recon-ng`, `Google Dorks`
- Exploits Leveraged: `vsFTPd backdoor`, `SMB brute-force`, `Directory Traversal`
- Flags or Sensitive Data: `adminpassword.txt`, `NTLMv2 hashes`, root shell

---

## 🧠 Lessons Learned

- Importance of basic misconfigurations in initial access
- How weak credentials and exposed services lead to full compromise
- Real-world relevance of chaining multiple low-severity issues

---

## 📁 Repo Structure

```bash
├── /screenshots/          # Full image documentation
├── /notes/                # Optional markdown files for each phase
├── README.md              # This file
└── pentest-report.pdf     # (Optional) Final summary or template
