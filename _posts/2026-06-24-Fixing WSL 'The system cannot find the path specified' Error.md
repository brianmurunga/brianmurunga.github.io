---
title: "Fixing WSL 'The system cannot find the path specified' Error"
date: 2026-06-24
tags: [Troubleshooting, WSL, Windows]
image: https://learn.microsoft.com/en-us/windows/wsl/media/store.png
---

# Fixing WSL "The system cannot find the path specified" Error

If you encounter the error `The system cannot find the path specified` when trying to run `wsl.exe` on Windows 11/10, don't worry – this is a common issue with modern WSL installations that can be resolved by understanding how WSL is now distributed on Windows.

---

##  Understanding the Problem

Modern versions of Windows distribute WSL as a **Microsoft Store application** installed in:
C:\Program Files\WindowsApps\MicrosoftCorporationII.WindowsSubsystemForLinux_[version]_x64__8wekyb3d8bbwe


The `wsl.exe` file in `C:\Windows\System32` is simply a **launcher stub** that redirects to the actual installation. When this launcher becomes corrupted or the WindowsApps installation breaks, you'll see the "path not found" error – even though the file physically exists in System32.

---

## 🛠️ Step-by-Step Solution

### 1. Verify WSL is Actually Installed

Check if WSL exists as a Windows App:

```powershell
Get-AppxPackage *WindowsSubsystemForLinux*

If installed, you'll see output showing the package name and installation location. Note the version number (e.g., 2.5.9.0).

2. Test WSL Directly from WindowsApps
Run WSL from its actual installation location:
& "C:\Program Files\WindowsApps\MicrosoftCorporationII.WindowsSubsystemForLinux_[version]_x64__8wekyb3d8bbwe\wsl.exe" --help

Replace [version] with your actual version number.

If this works: The WSL installation itself is fine; only the System32 launcher is broken.

If this fails: The WSL installation is corrupted and needs reinstallation.

3. Reinstall WSL (if corrupted or launcher is broken)
Option A: Reinstall via Winget (Recommended)
# Remove the existing installation
Get-AppxPackage MicrosoftCorporationII.WindowsSubsystemForLinux | Remove-AppxPackage

# Reinstall from Microsoft Store
winget install --id Microsoft.WSL --source msstore

Option B: Install via Microsoft Store
Open Microsoft Store

Search for "Windows Subsystem for Linux"

Click "Install" or "Update"

Option C: Ensure Windows Features are Enabled
# Enable required features
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

4. Restart Your Computer

