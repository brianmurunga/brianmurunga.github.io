---
title: "Hotstreets"
date: 2025-08-10
tags: [web]
image: /assets/img/H4k-IT/WEB/hotstreet1.png
categories: [Web]
---

**Description:**  
This lab demonstrates the risks of exposing sensitive information in client-side code and using weak authentication mechanisms. The goal was to access the administrator panel and retrieve the hidden flag.  

<img src="/assets/img/H4k-IT/WEB/hotstreet1.png" alt="One" style="max-width:100%; height:auto;">

## Walkthrough

### 1. Reconnaissance
Upon visiting the **Hotstreets** landing page, the site appeared to be a car dealership platform with options to browse cars and a **Login** button.  
Before doing anything else, I viewed the page’s **source code** (`CTRL+U`) to check for any hints.  

<img src="/assets/img/H4k-IT/WEB/hotstreet3.png" alt="Web" style="max-width:100%; height:auto;">

**Finding:** Inside the HTML comments, I found hardcoded **username** and **password**.  

<img src="/assets/img/H4k-IT/WEB/hotstreet4.png" alt="Web" style="max-width:100%; height:auto;">

### 2. Post-Login Exploration
Once logged in, I navigated through the **dashboard**.  

<img src="/assets/img/H4k-IT/WEB/hotstreet5.png" alt="Task One" style="max-width:100%; height:auto;">

Viewing the **page source** again revealed another HTML comment. This time, it contained the **flag**.  

<img src="/assets/img/H4k-IT/WEB/hotstreet6.png" alt="Task One" style="max-width:100%; height:auto;">

## Key Vulnerabilities
1. **Credentials in Client-Side Source Code** – Sensitive data should never be stored in HTML or JavaScript files accessible to the public.  
2. **No Input Sanitization** – The login form was vulnerable to SQL injection.  
3. **Flag in Source Code** – The flag was visible to anyone who inspected the page.  

## Mitigation
- Remove all hardcoded credentials from source code.  
- Use server-side authentication with proper hashing & salting.  
- Implement prepared statements to prevent SQL injection.  
- Never store sensitive information in client-rendered HTML.  
