---
title: "Fixing the 'PS/2 Mouse Not Detected' Error on a Lenovo ThinkPad T460s"
date: 2025-10-22
tags: [ThinkPad, Lenovo, BIOS, UEFI, Hardware, Troubleshooting]
image: https://upload.wikimedia.org/wikipedia/commons/2/2c/Lenovo_logo_2015.svg
---

## 🎯 Scenario

When booting my **Lenovo ThinkPad T460s**, I occasionally saw an error message during startup:

> `PS/2 Mouse not detected`

This was confusing since I wasn’t even using an external PS/2 mouse — and sometimes, my **touchpad and TrackPoint** worked perfectly fine afterward, especially when running in **UEFI mode**.  

After some digging, I learned that this issue is linked to how the **BIOS initializes internal PS/2 controllers** — and it can appear intermittently depending on your firmware and boot settings.

---

## 💻 Device & Environment

**Laptop Model:** Lenovo ThinkPad T460s  
**Operating System:** Windows 11 (UEFI mode)  
**Firmware:** Lenovo BIOS (UEFI)  
**Error Message:** `PS/2 Mouse not detected`

---

## 🧠 Understanding the Problem

Even though ThinkPads are modern laptops, the **touchpad and TrackPoint** are still internally connected through a **PS/2 interface**.  

During boot, the BIOS or UEFI firmware initializes that PS/2 controller.  
If the process is skipped or interrupted — such as by **Fast Boot**, **Hybrid Boot** or outdated firmware — you’ll see:

> “PS/2 Mouse not detected”

That message doesn’t mean your external mouse is missing — it refers to your **internal pointing devices**.

---

## ⚙️ Common Causes

- ⚡ **Fast Boot / Hybrid Boot enabled** — skips full hardware initialization.  
- 🧩 **Outdated BIOS or Embedded Controller (EC)** firmware.  
- 🔋 **Residual power** after shutdown prevents controller reset.  
- 🔄 **Legacy Boot mode** — incomplete device initialization.  
- 🔌 **Loose touchpad/TrackPoint cable** (rare but possible).

---

## 🛠️ Step-by-Step Fix

### 1. Disable Fast Boot

**In BIOS:**
- Go to `Startup → Boot`
- Disable **Fast Boot**

**In Windows:**
- Control Panel → Power Options → Choose what power buttons do  
- Uncheck **Turn on fast startup**

---

### 2. Update BIOS & Embedded Controller

Head to the official Lenovo support page for the T460s:

👉 [Lenovo Support – T460s Drivers & Updates](https://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t460s/downloads)

Download and run the **BIOS Update Utility** (Windows or bootable version).  
A newer firmware often resolves intermittent device detection.

---

### 3. Perform a Power Drain

1. Shut down your laptop.  
2. Unplug the charger and disconnect external devices.  
3. Hold the **power button for 30 seconds** to discharge static power.  
4. Reconnect power and boot normally.

This forces the **Embedded Controller** to fully reset and reinitialize all onboard devices.

---

### 4. Check BIOS Configuration

Navigate to:
- **Config → Mouse/Keyboard**
  - ✅ Ensure both **Touchpad** and **TrackPoint** are *Enabled*
- **UEFI/Legacy Boot**
  - Set to **UEFI Only**
- Keep **USB Legacy Support** enabled (so external devices work too).

---

### 5. Optional Fixes

- Load **Setup Defaults** in BIOS and save changes.  
- Reinstall **Lenovo Vantage** and update the **Synaptics/Elan Touchpad drivers**.  
- If issue persists, test with an **external USB mouse** to isolate hardware vs. firmware.

---

## ✅ My Results

After applying the steps above — mainly disabling **Fast Boot** and updating BIOS — my ThinkPad T460s now consistently detects both the **touchpad** and **TrackPoint** on every boot.

No more random “PS/2 mouse not detected” messages 🎉

---

## 💡 Key Takeaway

Sometimes what looks like a hardware failure is actually a **firmware initialization glitch**.  
Understanding how BIOS/UEFI handle device setup can save you hours of troubleshooting — and extend your laptop’s life.

---

*Authored by [Brian Murunga](https://brianmurunga.github.io)*
