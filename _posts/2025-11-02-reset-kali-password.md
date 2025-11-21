---
title: "Resetting a Forgotten Kali Linux Password (Safe Admin Trick)"
date: 2025-11-02
tags: [Troubleshooting]
image: https://www.kali.org/wallpapers/images/2025/kali-tiles.jpg
---

# Resetting a Forgotten Kali Linux Password (Safe Admin Trick)

If you ever forget your Kali Linux password, don’t panick, there is a built‑in recovery method you can safely use by leveraging GRUB’s recovery capabilities that any system owner should know.

---

## 🔧 Steps to Reset the Password

### 1. Access GRUB Menu  
Reboot your machine and hold **Shift** (BIOS) or **Esc** (UEFI) to display the GRUB boot menu.

### 2. Edit the Boot Parameters  
Highlight the default Kali entry and press **e** to edit.  
Find the line starting with:  
```
linux /boot/vmlinuz-...
```

Replace `ro quiet splash` with:  
```
rw init=/bin/bash
```

### 3. Boot Into a Root Shell  
Press **Ctrl + X** or **F10** to boot.

### 4. Change the Password  
At the root shell prompt, run:  
```
passwd your_username
```
<img src="/assets/img/Troubleshooting/passwds.png" alt="Task One" style="max-width:100%; height:auto;">

Set a new password.

### 5. Reboot  
Run:  
```
exec /sbin/init
```
<img src="/assets/img/Troubleshooting/passwds1a.png" alt="Task One" style="max-width:100%; height:auto;">
---

## 🛡️ Important Notes  
- This works only if someone has **physical access** to the machine.  
- This isn’t hacking, it’s system recovery for legitimate owners.  
- Keep GRUB locked with a password if you want to prevent unauthorised access.

---



