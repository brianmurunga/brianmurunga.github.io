---
title: "Windows Server Lab – Part 1: Planning the Infrastructure"
date: 2025-09-01
tags: [Windows Server, Active Directory, Planning, Lab Setup]
image: https://msftstories.thesourcemediaassets.com/2022/05/Microsoft-logo_rgb_c-wht-1536x688.png
---

## 🎯 Scenario

I’m building a Windows Server lab to simulate an organisation with **70 employees** across multiple departments.  
The goal is to design and configure a **centralised IT infrastructure** using **Active Directory Domain Services (AD DS)**, enforce security policies, and later simulate attacks and defenses.

---

## 🏢 Organisation Setup
 <img src="/assets/img/THM/Windows/AD/dc01.png" alt="Task One" style="max-width:100%; height:auto;">
- **Employees:** ~70  
- **Departments:**  
  - ICT (10)  
  - Finance (15)  
  - HR (10)  
  - Legal (5)  
  - Operations (20)  
  - Management (10)  

---

## 🌐 Domain & Server Plan

- **Corporate Domain (real-world):** `bmluns.com`  
- **Lab Domain (for this project):** `bmluns.local` (to avoid DNS conflicts)  
- **Primary Server (Domain Controller):** `SRV-DC01`  
- **Roles to Deploy:**  
  - Active Directory Domain Services (AD DS)  
  - DNS Server  
  - File Server (shared departmental folders)  
  - Group Policy Management  

---

## 🗂️ Active Directory Design

**Organisational Units (OUs):**
- ICT  
- Finance  
- HR  
- Legal  
- Operations  
- Management  

**Groups :**
- `ICT_Admins`  
- `Finance_Users`  
- `HR_Users`  
- `Ops_Staff`  
- `Management_Users`  

**Users:**
- Simulate ~70 employee accounts (one per staff member).  
- Format: `firstinitiallastname@bmluns.com` (e.g., `jdoe@bmluns.com`).  

---

## 📂 File & Resource Sharing

Departmental shared folders:  
- `\\BMLUNS-DC01\Finance` → accessible only to Finance_Users.  
- `\\BMLUNS-DC01\HR` → accessible only to HR_Users.  
- `\\BMLUNS-DC01\Public` → read-only for all staff.  

Permissions will be configured with **least privilege access**.

---

## 🔐 Security Policies (to be enforced via Group Policy)

- Password complexity (min length, complexity, expiry).  
- Account lockout after multiple failed attempts.  
- Restricted Remote Desktop access (ICT_Admins only).  
- Firewall rules & logging enabled.  

---

## 📌 Next Steps

In the next post, I’ll cover **Part 2: Installing Windows Server 2022 on VirtualBox**, including initial configuration, networking, and preparing the server to become a Domain Controller.

---

*This planning step shows how to translate organisational requirements into a structured IT setup, balancing functionality with security — a critical skill for both ICT administration and security analysis.*
