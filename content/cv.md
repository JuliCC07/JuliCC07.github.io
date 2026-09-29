---
title: "Curriculum Vitae"
layout: "cv"
---

## JULIÁN COLLADOS CORBALÁN
**Junior Systems Administrator & Security Enthusiast**

📧 juliancolladosc@gmail.com | 🔗 [linkedin.com/in/julicc07](https://linkedin.com/in/julicc07) | 🐙 [github.com/JuliCC07](https://github.com/JuliCC07) | 🌐 [JuliCC07.github.io](https://JuliCC07.github.io)

### PROFILE
Second-year ASIR student (Network Systems Administration) with a strong foundation in Linux systems, network infrastructure, and cybersecurity. I specialize in designing virtualized environments, automating system deployments, and conducting vulnerability assessments. Through continuous hands-on projects, I have developed practical skills in routing, server administration, and defensive security. I am currently seeking an Erasmus+ internship (March–June 2027) to apply my technical capabilities in a real-world enterprise environment while working toward the OSCP certification.

### SKILLS
* **Systems Administration:** Linux (Debian, Ubuntu, Fedora, CachyOS), Windows Server, Systemd, Bash Scripting, Automation
* **Networking:** TCP/IP, Routing, NAT/iptables, DNS (Bind9, dnsmasq), DHCP, VLANs, Firewalls (pfSense)
* **Virtualization & Storage:** KVM/QEMU, libvirt, LVM, XFS, ext4, LUKS Encryption
* **Security:** Penetration Testing Methodology, Vulnerability Assessment, Nmap, Burp Suite, Privilege Escalation

### FEATURED PROJECTS
**Virtualized Network Infrastructure (KVM Home Lab)**
* Designed and deployed a multi-subnet corporate network simulation using Linux KVM.
* Configured a Debian core router with IP forwarding, iptables NAT, and internal DNS (dnsmasq).
* Implemented secure remote access via an SSH Bastion Host with ProxyJump.
* Automated VM orchestration and scheduled shutdowns using Bash, tmux, and systemd timers.

**Custom Kernel Build Automation**
* Developed a Bash wrapper ([cachyos-tsc-wrapper](https://github.com/JuliCC07/cachyos-tsc-wrapper)) to dynamically inject custom TSC patches into the CachyOS kernel.
* Automated the entire pipeline: repository cloning, `PKGBUILD` manipulation via `sed`, checksum updates, and compilation.

**Penetration Testing Practice (HackTheBox)**
* Documented exploitation paths for retired machines, emphasizing vulnerability analysis and remediation.
* Exploited logical flaws (IDOR, SQLi) and public CVEs (e.g., Cacti RCE, MotionEye RCE).
* Escaped Docker containers via unauthenticated Docker APIs (CVE-2025-9074) and abused misconfigured Linux capabilities and `incrontab` jobs for privilege escalation.

**Linux Server Administration Lab**
* Migrated live `/home` directories to new virtual disks using `rsync` while preserving ACLs and extended attributes.
* Configured historical performance monitoring (`sysstat`) and real-time telemetry (`NetData`) secured via SSH tunnels.
* Implemented full disk encryption (`LUKS`), granular file permissions (`setfacl`), and shared departmental directories using SGID.

### EDUCATION
**ASIR (Network Systems Administration) - Higher Vocational Degree**
*IES Ingeniero de la Cierva, Spain* | Expected Graduation: 2027

### CERTIFICATIONS & TRAINING
* **Cambridge C1 Advanced** - Obtained June 2025
* **eJPT (INE Security)** - In Progress (HTB Academy Pentesting Path)
* **OSCP (OffSec)** - Long-term goal

### LANGUAGES
* **Spanish:** Native
* **English:** C1 Advanced
* **German:** A2 (Self-studying)
