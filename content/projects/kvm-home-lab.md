---
title: "Virtualized Network Infrastructure (KVM Home Lab)"
date: 2026-09-29T10:00:00+02:00
weight: 1
tags: ["KVM", "Linux", "Networking", "Bash", "Systemd"]
description: "A fully automated, multi-subnet corporate network simulation built on Linux KVM to practice routing, firewalling, DNS, and remote access."
---

## Context & Goal
To gain practical experience in infrastructure management, I designed and deployed a multi-subnet corporate network simulation using Linux KVM (Kernel-based Virtual Machine). The goal was to practice configuring complex routing, firewall rules, internal DNS, and secure remote access in a virtualized environment.

## Architecture
The infrastructure consists of several interconnected virtual machines:

* **Host Machine:** Provides virtualization via QEMU/KVM and Libvirt.
* **helldoor (Router/Firewall):** A Debian-based VM acting as the core router and firewall with 3 network interfaces (NAT, internal, and management).
* **Server Subnet (10.0.100.0/24):** Hosts critical infrastructure services.
* **Client Subnet (10.0.0.0/24):** Simulates a user network.
* **pfSense / Windows Server:** Additional nodes for firewalling and Active Directory practice.

## What I Built
* **Linux Router & NAT:** Configured IP forwarding and `iptables` NAT rules on the `helldoor` router to provide internet access to internal subnets.
* **Internal DNS:** Deployed `dnsmasq` for internal name resolution (`.juli.alt` domain) across the simulated corporate network.
* **Secure Remote Access:** Configured the `helldoor` router as an SSH Bastion Host (Jump Server), using `ProxyJump` and key-based authentication to securely access isolated internal VMs from the host machine.
* **Automation:** 
    * Developed a `bash` and `tmux` orchestration script to automate the sequential boot-up of the virtual lab and launch a multi-pane terminal session automatically connected to the key nodes.
    * Implemented `systemd` timers for automated, scheduled VM shutdowns.
    * Created reactive backup scripts triggered by `udev` rules and `systemd` when specific USB storage devices are attached.

## Challenges & Solutions
* **Routing Asymmetry:** Encountered initial connectivity issues between subnets due to missing return routes. Resolved by configuring static routes correctly on the `helldoor` core router.
* **DNS Resolution:** Client VMs were unable to resolve external domains. Fixed by properly configuring the `bind-interfaces` directive and upstream servers in `dnsmasq`.

## Outcome
A robust, automated 4-node virtualized network environment that can be spun up and accessed securely with a single command. This lab serves as my primary testing ground for new system administration and security configurations.
