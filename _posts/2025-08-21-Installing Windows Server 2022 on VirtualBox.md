---
title: "Installing Windows Server 2022 on VirtualBox – Step by Step"
date: 2025-08-21
tags: [Windows Server, VirtualBox, Lab Setup]
image: https://uhf.microsoft.com/images/microsoft/RE1Mu3b.png
---

As part of my **learning lab**, I set up **Windows Server 2012** inside **Oracle VirtualBox**. This post documents the **installation process**, which will form the base for my upcoming Active Directory and security testing labs.

---

## 🖥️ Prerequisites
Before starting, ensure you have:
- **Oracle VirtualBox** (download: [virtualbox.org](https://www.virtualbox.org/))  
- **Windows Server 2022 ISO** (free trial at [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/))  
- At least **4GB RAM** and **60GB free disk space**  

---

## 🔹 Step 1: Create a New Virtual Machine
1. Open **VirtualBox** → Click **New**.  
2. Name: `AD001`  
   - Type: `Microsoft Windows`  
   - Version: `Windows 2012 (64-bit)`  
3. Assign **4096 MB RAM** (or more).  
4. Create a virtual hard disk:  
   - Type: **VDI (VirtualBox Disk Image)**  
   - Dynamically allocated  
   - Size: **60–80 GB**  
    <img src="/assets/img/THM/Windows/AD/AD1.png" alt="Task One" style="max-width:100%; height:auto;">
---

## 🔹 Step 2: Attach Installation Media
1. Go to **Settings → Storage**.  
2. Under Controller: SATA → click the empty disk.  
3. Attach the **Windows Server ISO**.  
4. Ensure only **two devices** are present:  
   - Your `.vdi` virtual hard disk  
   - The Windows Server ISO  

*(Tip: Remove any extra “Unattended ISO” that VirtualBox may auto-attach.)*

---

## 🔹 Step 3: Configure Networking
- Go to **Settings → Network**.  
- Adapter 1: **NAT** (for internet access).  
- (Optional) Add Adapter 2: **Host-Only Adapter** (for internal lab later).  

---

## 🔹 Step 4: Install Windows Server
1. Start the VM → It boots from the ISO.  
2. Choose:  
   - Language: **English (US)**  
   - Install type: **Windows Server 2022 Standard (Desktop Experience)**  
3. Accept license terms → Choose **Custom: Install Windows only**.  
4. On the disk screen:  
   - Delete existing partitions if present.  
   - Select **Unallocated Space → Next**.  
5. Setup will copy files and reboot.  

---

## 🔹 Step 5: Initial Configuration
1. Set a strong **Administrator password**.  
   <img src="/assets/img/THM/Windows/AD/AD6.png" alt="Task One" style="max-width:100%; height:auto;">
2. Log in and configure:  
   - Rename server: e.g., `SRV-DC01`.  
   - Assign a **static IP address**.  
   - Enable **Remote Desktop** (System Properties → Remote).  
   - Run **Windows Update**.  

---

## 🔹 Step 6: Take a Snapshot
In VirtualBox → **Machine → Take Snapshot**  
- Name it: *“Fresh Install”*  
- This lets you roll back later if needed.  

---

## 🎯 Next Steps
With Windows Server 2022 installed, the next milestones are:
1. **Promote to a Domain Controller (Active Directory)**  
2. Configure **DNS & File Services**  
3. Harden security policies  
4. Simulate attacks from **Kali Linux VM**  
<img src="/assets/img/THM/Windows/AD/AD8.png" alt="Task One" style="max-width:100%; height:auto;">
---

## 📸 Screenshots
1. <img src="/assets/img/THM/Windows/AD/AD2.png" alt="Task One" style="max-width:100%; height:auto;">
2. <img src="/assets/img/THM/Windows/AD/AD3.png" alt="Task One" style="max-width:100%; height:auto;">
3. <img src="/assets/img/THM/Windows/AD/AD4.png" alt="Task One" style="max-width:100%; height:auto;">
4. <img src="/assets/img/THM/Windows/AD/AD5.png" alt="Task One" style="max-width:100%; height:auto;">
5. <img src="/assets/img/THM/Windows/AD/AD6.png" alt="Task One" style="max-width:100%; height:auto;">
6. <img src="/assets/img/THM/Windows/AD/AD7.png" alt="Task One" style="max-width:100%; height:auto;">
---

This post marks the foundation of my **Windows Server Security Lab**, which I’ll expand in upcoming posts on **Active Directory, Security Hardening, and Pentesting**.
