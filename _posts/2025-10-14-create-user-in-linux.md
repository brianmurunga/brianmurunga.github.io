---
title: "Linux Administration – Part 1: Creating a User in Kali Linux"
date: 2025-10-14
tags: [Linux, Kali Linux, System Administration, Cybersecurity, Security Analyst]
image: https://upload.wikimedia.org/wikipedia/commons/2/2b/Kali-dragon-icon.svg
---

## 🎯 Scenario

In this post, I’ll demonstrate how to **create and manage users** in a Linux environment — specifically using **Kali Linux**, one of the most popular operating systems for cybersecurity and penetration testing.  

User management is a fundamental system administration task that strengthens **access control**, **privilege separation**, and **system security**.

---

## 💻 Environment Setup

**Operating System:** Kali Linux (2025.2 or later)  
**Platform:** Oracle VirtualBox  
**User Role:** System Administrator  

To get started, open your terminal and ensure you have root or `sudo` privileges.
<img src="/assets/img/THM/Windows/AD/kali.png" alt="Task One" style="max-width:100%; height:auto;">

---

## Step 1: Creating a New User

The `adduser` command is used to create a new user account.

```bash
sudo adduser BMW
```

You’ll be prompted to:
- Enter a new password  
- Confirm it  
- Optionally add user details (Full Name, Room Number, etc.)  

After completion, a new home directory will be created at:
```
/home/BMW
```

---

## Step 2: Assigning Administrative Privileges

To allow the new user to run administrative commands (like `sudo`), add them to the **sudo group**:

```bash
sudo usermod -aG sudo BMW
```

You can confirm the user’s groups with:
```bash
groups BMW
```

If `sudo` appears in the list, you’re all set ✅

---

## Step 3: Switching Users

To log in as the new user without logging out:

```bash
su - BMW
```

The `-` loads the user’s full environment profile.

To return to your previous session:
```bash
exit
```

---

## Step 4: Changing Passwords

To change your current password:
```bash
passwd
```

Or, if you’re an administrator updating another user’s password:
```bash
sudo passwd BMW
```

You’ll be asked to enter and confirm the new password.

---

## 🧹 Step 5: Removing a User (Optional)

If you ever need to remove a user account:

```bash
sudo deluser --remove-home BMW
```

This command deletes both the user and their home directory.  
To keep their files:
```bash
sudo deluser BMW
```

---

## ⚙️ Step 6: Renaming an Existing User (Alternative)

If you’d rather rename an existing user (for example, changing `kali` to `BMW`):

```bash
sudo usermod -l BMW -d /home/BMW -m kali
sudo groupmod -n BMW kali
```

This renames both the username and their home directory.

---

## Why This Matters

Learning to manage users is a cornerstone of system administration and security.  
It helps you understand how **Linux handles authentication**, **permissions**, and **privilege escalation** — critical for both defenders and attackers in cybersecurity.

---

## 📘 Summary Commands

| Task | Command |
|------|----------|
| Create user | `sudo adduser BMW` |
| Add sudo privileges | `sudo usermod -aG sudo BMW` |
| Switch user | `su - BMW` |
| Change password | `sudo passwd BMW` |
| Delete user | `sudo deluser --remove-home BMW` |
| Rename user | `sudo usermod -l NEW -d /home/NEW -m OLD` |

---

## Next Steps

In the next post, I’ll cover **Part 2: Managing File Permissions and Ownership in Linux**,  
where we’ll explore `chmod`, `chown`, and how to implement the principle of least privilege across users.

---

*Authored by [Brian Murunga](https://brianmurunga.github.io) — passionate about Linux administration, cybersecurity, maintaining and building secure digital systems.*
