---
title: "Connecting to RDP from Kali Linux"
date: 2025-08-13 
tags: [RDP, Windows, Kali, TryHackMe, Pentesting]
image: https://tryhackme-images.s3.amazonaws.com/user-uploads/63588b5ef586912c7d03c4f0/room-content/be629720b11a294819516c1d4e738c92.png
categories: [Labs, Networking, Windows]
---

# Connecting to RDP from Kali Linux

When working on **penetration testing labs** (like TryHackMe or HackTheBox), you’ll often encounter machines that allow connections via **Remote Desktop Protocol (RDP)**. RDP is a Microsoft protocol that lets you interact with a Windows machine’s desktop environment remotely – as if you were sitting right in front of it.  

In this post, I’ll show you how to connect to RDP sessions directly from **Kali Linux**, and we’ll walk through a small **lab example** using TryHackMe.

---

## What is RDP?
- **RDP (Remote Desktop Protocol)** allows you to connect to and control a Windows machine remotely.  
- System administrators use it to manage servers or workstations.  
- Attackers often abuse it for lateral movement once they get valid credentials.  

When labs provide RDP credentials, they usually look like this:  
<img src="/assets/img/THM/Windows/AD/9.png" alt="RDP" style="max-width:100%; height:auto;">

---

## 🔹 Step 1: Install an RDP Client
Kali Linux doesn’t come with an RDP client by default, but the most popular one is **xfreerdp**.  

Install it using:

sudo apt update
sudo apt install freerdp2-x11 -y
<img src="/assets/img/THM/Windows/AD/10.png" alt="Task One" style="max-width:100%; height:auto;">

## 🔹 Step 2: Connect with xfreerdp
xfreerdp3 /v:10.10.147.23 /u:Administrator /p:Password321 /d:THM /cert:ignore
<img src="/assets/img/THM/Windows/AD/12.png" alt="Task One" style="max-width:100%; height:auto;">
Here’s what the options mean:
/v: → The target IP address of the Windows machine.
/u: → The username provided.
/p: → The password provided.
/d: → The domain provided.
If the login is successful, you’ll see a Windows desktop environment inside your Kali Linux terminal window.

## 🔹Step 3: Interact with Windows
Now you can:
Open File Explorer
Check Control Panel
Launch Command Prompt / PowerShell
This is extremely useful when you need GUI access for testing or privilege escalation.
<img src="/assets/img/THM/Windows/AD/13.png" alt="Task One" style="max-width:100%; height:auto;">

## 🔹 Step 4: Security Note
1. RDP should never be exposed directly to the internet – attackers actively scan for open RDP ports (3389).
2. In secure environments, RDP is usually only accessible via VPN or bastion hosts.
- For labs like TryHackMe, your connection is safe because it’s contained within the VPN tunnel.

## 🔹 Connecting to RDP from Kali is simple with the right tools.
Use xfreerdp for quick command-line access.
Use Remmina if you want a GUI client.
Practicing in TryHackMe labs is the safest way to get hands-on experience with RDP.