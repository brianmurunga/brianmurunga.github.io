---
title: "TryHackMe: Web Application Security — Walkthrough"
date: 2025-08-08
tags: [tryhackme, web, pentesting, cybersecurity, owasp]
categories: [Web]
---

## Introduction

As part of my web penetration testing journey, I explored the **[Web Application Security](https://tryhackme.com/room/introwebapplicationsecurity)** room on TryHackMe.  
This beginner-friendly room introduces **how websites work** and demonstrates common vulnerabilities attackers exploit.

A web application is any service that runs in a browser and communicates with a backend server — from social media sites to online banking systems.  
The only thing you need to access one? **A browser**.

<img src="/assets/img/THM/Web/0.png" alt="Task One" style="max-width:100%; height:auto;">

---

## Security Risks in Web Applications

Web apps can suffer from many vulnerabilities. The room links these to OWASP Top 10 categories. Some key examples:

- **Unlimited login attempts** → *Identification and Authentication Failure* (makes brute-forcing possible)
- **Credentials in cleartext** → *Cryptographic Failure* (unencrypted data can be intercepted)
- **Direct access to restricted resources** → *Broken Access Control*

These weaknesses are often easy to exploit if proper controls are missing.

<img src="/assets/img/THM/Web/00.png" alt="Security Risks" style="max-width:100%; height:auto;">

---

## Hands-On: IDOR (Insecure Direct Object Reference)

The practical section focuses on **IDOR**, a form of *Broken Access Control*.  
Here’s the typical scenario:

1. The application uses predictable resource IDs in the URL:  
   <img src="/assets/img/THM/Web/1.png" alt="Inventory Management" style="max-width:100%; height:auto;">

2. By changing the `id` parameter, you can view another user’s profile:  
   <img src="/assets/img/THM/Web/2.png" alt="The current user" style="max-width:100%; height:auto;">  
   <img src="/assets/img/THM/Web/3.png" alt="When we alter user_id" style="max-width:100%; height:auto;">

3. This bypasses access control checks and exposes unauthorized data:  
   <img src="/assets/img/THM/Web/4.png" alt="The user who made changes" style="max-width:100%; height:auto;">

In the lab, I:
- Found the user who made unauthorized changes
- Accessed their record via IDOR
- Reverted the changes to retrieve the flag

**Flag:**  
<img src="/assets/img/THM/Web/5.png" alt="Flag after reverting changes" style="max-width:100%; height:auto;">

---

## Key Takeaways

- **Web applications** rely on client-server communication; understanding HTTP is crucial.
- **Authentication & encryption flaws** are common starting points for attackers.
- **Broken Access Control** issues like IDOR can be devastating yet easy to spot with methodical testing.
- Even beginner labs teach you the attacker mindset — which is vital for defending against real-world threats.

---

## Reflection

This room was an excellent introduction to web security concepts.  
It’s clear that **security isn’t just about servers or firewalls — it starts in the application’s logic and design**.  
I’ll be continuing into OWASP Top 10 vulnerabilities next, starting with **XSS** and **SQL Injection**.

---

*Completed on:* 8th August 2025  
*Platform:* [TryHackMe](https://tryhackme.com/)  
*Tools Used:* Browser, HTTP headers analysis
