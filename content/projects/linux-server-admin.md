---
title: "Linux Server Administration Lab"
date: 2026-09-29T07:00:00+02:00
weight: 4
tags: ["Ubuntu", "SysAdmin", "Storage", "Security"]
description: "A comprehensive Ubuntu Server laboratory covering performance monitoring, disk management, encryption, and secure file sharing."
---

## Context & Goal
To consolidate core systems administration skills, I engineered a comprehensive laboratory environment utilizing an Ubuntu Server virtual machine with multiple attached storage volumes. The goal was to practice advanced disk management, system monitoring, and secure user management in a simulated enterprise scenario.

## Key Implementations

### 1. Storage Management & Live Migration
* **Partitioning & Filesystems:** Configured complex partitioning schemes using `fdisk`, formatting volumes with `XFS` and `ext4`, and managing persistent mounts via UUIDs in `/etc/fstab`.
* **Disk Quotas:** Implemented `xfs_quota` to enforce strict storage limits on standard user accounts.
* **Live Directory Migration:** Successfully migrated the active `/home` directory to a new 200GB virtual disk using `rsync -avxHAX` to perfectly preserve permissions, ACLs, and extended attributes with zero data loss.

### 2. System Monitoring & Performance
* **Historical Data:** Configured `sysstat` (sar) for automated, long-term collection of CPU, memory, queue, and block I/O metrics.
* **Real-time Telemetry:** Deployed `NetData`, restricting its binding to `localhost` for security, and securely accessed the dashboard from a remote machine using an SSH local port forwarding tunnel.

### 3. Encryption & Forensic Imaging
* **Full Disk Encryption:** Implemented `LUKS` (Linux Unified Key Setup) for seamless block-level encryption, configuring automatic decryption at boot via `/etc/crypttab`.
* **Cross-Platform Encryption:** Utilized `VeraCrypt` with `exFAT` for secure, interoperable storage between Linux and Windows hosts.
* **Block Imaging:** Practiced exact sector-by-sector disk cloning and restoration using the `dd` utility.

### 4. Advanced Permissions & Collaboration
* **Access Control Lists (ACLs):** Deployed granular ACLs (`setfacl`) to configure default permission inheritance for new files in shared departmental directories.
* **SGID (Set-Group-ID):** Utilized the SGID bit on shared directories to ensure all newly created files automatically inherit the departmental group ownership, facilitating seamless collaboration without exposing files to unauthorized users.

## Outcome
This laboratory provided intensive, hands-on experience with the critical, day-to-day operations expected of a Linux Systems Administrator, from ensuring data confidentiality via encryption to safely expanding storage infrastructure.
