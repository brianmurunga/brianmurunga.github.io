---
title: "Fixing Partition Errors in Windows Server Install on VirtualBox"
date: 2025-08-20
tags: [Windows Server, VirtualBox, Troubleshooting, Lab Setup]
image: <img src="/assets/img/THM/Windows/AD/ad.png" alt="Task One" style="max-width:100%; height:auto;">
---
While setting up **Windows Server 2022 on VirtualBox**, I ran into a common error during the installation:
> *“There is an error selecting this partition for install. Please select a different partition or refresh selections.”*
<img src="/assets/img/THM/Windows/AD/ad.png" alt="Task One" style="max-width:100%; height:auto;">
This error appeared when I reached the **disk selection screen**. Here’s how I fixed it.
---
## 🔎 Root Cause
The issue occurs because VirtualBox had mounted an **extra “Unattended Install” ISO** alongside my Windows Server ISO, which confused the installer. The VM had:
- A virtual hard disk (`ADB.vdi`)  
- The Windows Server ISO  
- An extra **0 B Unattended ISO** automatically added by VirtualBox  
---
## ✅ Solution
### 1. Remove Extra ISO
- Shut down the VM.  
- Go to **Settings → Storage**.  
- Under the **SATA Controller**, remove the empty *“Unattended-…iso (0 B)”*.  
- Keep only:  
  - Your virtual hard disk (`.vdi`)  
  - The Windows Server ISO  
---
### 2. Reboot and Delete Partition
- Boot the VM from the Windows Server ISO.  
- At the **“Select location to install Windows Server”** screen:  
  - Select the partition.  
  - Click **Delete** → Confirm.  
  - Highlight the **Unallocated Space**.  
  - Click **Next**.  
Windows Setup will create the necessary partitions automatically.

---

### 3. (Optional) Use Diskpart if Issue Persists
If the error still appears:
1. Press **Shift + F10** to open Command Prompt.  
2. Enter:
   ```powershell
   diskpart
   list disk
   select disk 0
   clean
   create partition primary
   format fs=ntfs quick
   exit


