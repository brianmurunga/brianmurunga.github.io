---
title: "Part 2.1 – Server Naming Standards"
date: 2025-09-01
categories: [Windows Server, Active Directory, Lab Setup]
tags: [Server Naming, AD DS, IT Infrastructure, Bmluns]
---

# 🖥️ Part 2.1 – Server Naming Standards

Before setting up Active Directory, it’s important to define a **server naming convention**.  
Consistent naming ensures clarity, scalability, and easier management as the organization grows.

---

## 📌 Naming Convention Structure

**Format:**  

- **Company Prefix:** `BMLUNS` → identifies the organization  
- **Role:** `DC`, `FS`, `SQL`, `WEB`, etc. → defines the server’s function  
- **Number:** starts at `01` → increments as more servers are added  

---

## 🖥️ Example Naming Standards – Bmluns Organization  

| **Role**                  | **Server Name**   | **Purpose** |
|----------------------------|------------------|-------------|
| Primary Domain Controller  | **BMLUNS-DC01**  | First Active Directory Domain Controller for `bmluns.local`. Handles authentication, AD DS, DNS. |
| Secondary Domain Controller (future) | **BMLUNS-DC02** | Backup AD DS + DNS. Provides redundancy & load balancing. |
| File Server                | **BMLUNS-FS01**  | Centralized file storage & shared folders for departments. |
| Web/Application Server     | **BMLUNS-WEB01** | Hosts internal apps or company website. |
| SQL Database Server        | **BMLUNS-SQL01** | Runs Microsoft SQL Server for finance, HR, or other apps. |
| WSUS Server                | **BMLUNS-WSUS01** | Manages Windows updates for the organization. |
| Print Server (optional)    | **BMLUNS-PRN01** | Manages shared printers across departments. |
| Backup Server              | **BMLUNS-BKP01** | Handles scheduled backups of critical company data. |

---

## 📌 Why Naming Standards Matter

- ✅ **Clarity** – IT staff know the function of each server at a glance.  
- ✅ **Scalability** – Easy to expand (e.g., `BMLUNS-DC03`, `BMLUNS-FS02`).  
- ✅ **Professionalism** – Demonstrates IT governance and structured planning.  
- ✅ **Troubleshooting** – Reduces confusion in large environments.  

---

📖 *Next Step → Proceed to [Part 2: Active Directory Installation](./2025-09-01-part2-ad-ds-installation.md)*  
