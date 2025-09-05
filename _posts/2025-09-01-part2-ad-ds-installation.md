---
title: "Part 2 – Installing Active Directory Domain Services (AD DS)"
date: 2025-09-01
categories: [Windows Server, Active Directory, Lab Setup]
tags: [AD DS, Windows Server, Domain Controller, Security Analyst Lab]

---

# Part 2 – Installing Active Directory Domain Services (AD DS)

## 🎯 Goal
Set up **Active Directory** on our Windows Server 2022 VM and prepare the domain `bmluns.local` for 70 employees across multiple departments.

---

## 🔹 Step 1: Prepare the Server
- Ensure Windows Server is installed and updated.  
- Rename the server to something meaningful (e.g., `DC01`).  
- Set a **static IP address** (important for DNS). Example: `192.168.1.10`.  

---

## 🔹 Step 2: Install AD DS Role
1. Open **Server Manager** → *Manage* → *Add Roles and Features*.  
2. Choose **Role-based or feature-based installation**.  
3. Select your server (`DC01`).  
4. Install **Active Directory Domain Services** role.  
5. Wait for installation, then click the **flag notification** to *Promote this server to a domain controller*.  

---

## 🔹 Step 3: Create the Domain
- Select **Add a new forest**.  
- Enter root domain: `bmluns.local`.  
- Choose **Forest functional level**: Windows Server 2022.  
- Set a **DSRM password** (Directory Services Restore Mode).  
- Complete installation and let the server reboot.  

---

## 🔹 Step 4: Verify Domain Setup
- Log back in as `bmluns\\Administrator`.  
- Open **Active Directory Users and Computers (ADUC)**.  
- Confirm the new domain exists: `bmluns.local`.  

---

✅ At this stage, you now have a **domain controller (DC)** running for your organization.

---

👉 Next: **Part 3 – Organizing OUs, Groups, and Users** for ICT, Finance, HR, Legal, Operations, and Management.
