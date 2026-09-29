---
title: "Penetration Testing Practice (HackTheBox)"
date: 2026-09-29T08:00:00+02:00
weight: 3
tags: ["Security", "Pentesting", "CVE", "Linux"]
description: "A portfolio of penetration testing write-ups demonstrating vulnerability analysis, exploitation, and privilege escalation."
---

## Context & Goal
To build a practical security mindset and prepare for the eJPT certification, I regularly practice penetration testing on HackTheBox. I document my exploitation paths in professional write-ups, focusing not just on gaining root access, but on understanding the underlying vulnerabilities and how to remediate them.

## Methodology
My testing workflow strictly follows a structured methodology:
1. **Reconnaissance:** Port scanning and service enumeration (Nmap), directory fuzzing (ffuf), and web application analysis (Burp Suite).
2. **Vulnerability Analysis:** Identifying misconfigurations, analyzing CVEs, and recognizing logical flaws (e.g., IDOR, SQLi).
3. **Exploitation:** Adapting public Proof of Concepts (PoCs) and executing initial access vectors (Reverse Shells).
4. **Privilege Escalation:** Enumerating internal systems, exploiting Linux capabilities, finding unquoted service paths, or abusing misconfigured automation services (like `incron`).
5. **Remediation:** Concluding with actionable steps to secure the system.

## Featured Compromises (Retired Machines)

### 1. Cacti (MonitorsFour)
* **Initial Access:** Discovered an Insecure Direct Object Reference (IDOR) on a hidden API endpoint, extracting MD5 password hashes. Cracked the hashes to access a Cacti monitoring dashboard.
* **Exploitation:** Exploited **CVE-2025-24367** (Cacti RCE via Graph Templates) to gain a shell as `www-data`. Discovered I was inside a Docker container.
* **Privilege Escalation:** Escaped the container by exploiting **CVE-2025-9074**, leveraging an unauthenticated Docker Engine API exposed on Docker Desktop's internal subnet to mount the host filesystem.

### 2. CCTV
* **Initial Access:** Identified an outdated ZoneMinder instance and exploited an unauthenticated SQL Injection (CVE-2024-51482) using a captured Burp request in `sqlmap`.
* **Exploitation:** Dumped the `Users` table, cracked a user's password with `hashcat`, and gained SSH access.
* **Privilege Escalation:** Found a locally bound MotionEye instance running as root. Set up an SSH local port forward and exploited an authenticated RCE in MotionEye to gain a root shell.

### 3. Archetype (Starting Point)
* **Initial Access:** Connected to an SMB share using an anonymous null session, discovering cleartext database credentials in a configuration file.
* **Exploitation:** Authenticated to Microsoft SQL Server using Impacket's `mssqlclient.py` and enabled `xp_cmdshell` to execute a PowerShell reverse shell.
* **Privilege Escalation:** Stole the Administrator's credentials from the `ConsoleHost_history.txt` PowerShell history file.

## Outcome
Through these exercises, I have developed a deep understanding of how system misconfigurations (like excessive Linux capabilities or exposed Docker sockets) are abused in the real world, heavily informing my approach to secure systems administration.
