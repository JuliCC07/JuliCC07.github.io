---
title: "Custom Kernel Build Automation (CachyOS)"
date: 2026-09-29T09:00:00+02:00
weight: 2
tags: ["Bash", "Linux Kernel", "Automation", "Git"]
description: "An automated bash wrapper to dynamically inject custom TSC patches into the CachyOS kernel during compilation."
---

## Context & Goal
My primary workstation experienced clock drift issues due to faulty Time Stamp Counter (TSC) firmware (specifically, the lack of the `IA32_TSC_ADJUST` MSR). To fix this, I needed to compile the custom `linux-cachyos-bore` kernel with specific patches to force direct TSC synchronization. Because the upstream kernel updates frequently, maintaining a manual fork was inefficient.

## What I Built
I developed a Bash wrapper script ([cachyos-tsc-wrapper](https://github.com/JuliCC07/cachyos-tsc-wrapper)) that automates the entire patching and compilation pipeline:
* **Dynamic Cloning:** Clones the official upstream CachyOS repository on-the-fly into a temporary build directory.
* **Patch Injection:** Automatically copies 6 custom TSC patches into the build environment.
* **PKGBUILD Modification:** Uses `sed` to dynamically modify the Arch Linux `PKGBUILD` source array, registering the new patches without manual intervention.
* **Checksum Management:** Updates the source integrity checksums using `updpkgsums`.
* **Compilation & Installation:** Triggers a clean compile and system installation (`makepkg -C -si`).

## Challenges & Solutions
* **Patch Context Conflicts:** As the upstream Linux kernel evolved (e.g., refactoring `tsc_as_watchdog` to `tsc_watchdog`), the surrounding code lines changed, causing `patch` to fail. I manually adapted the `.patch` files and wrote a guide in the repository's README for handling future conflicts.
* **Double-Application Bugs:** Initially, patches were being applied twice (once via the `source[]` array and once via a manual `patch -Np1` command in the `prepare()` function), which halted compilation. I refactored the script to rely entirely on the native `PKGBUILD` patching mechanism.

## Outcome
A robust, one-command kernel rebuild system that keeps my machine updated with the latest CachyOS performance improvements while maintaining stable hardware clock synchronization.
