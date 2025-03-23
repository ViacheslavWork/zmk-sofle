- [Chinese](README.md)
- [English](README_EN.md)

# Update List

- 2024/12/21
  1. Added support for zmk-studio (just refresh the left hand to use).
- 2024/10/24
  1. Modified power supply mode to reduce power consumption.
  2. Fixed the automatic shut-off feature for RGB power supply.

> If your keyboard was updated before October 24, please update to the latest firmware.
> 
---
# Contact Me

For 3D printed model files or any issues and malfunctions with the keyboard, please contact 380465425@qq.com

# Sofle Keymap


<img src="keymap-drawer/sofle.svg" >

# ZMK Build Configuration for Eyelash Sofle

This **YAML configuration** defines different firmware builds for a **split keyboard (Eyelash Sofle)** with Nice!View displays.

---

## **🔍 Breakdown of Each Entry**
Each `include:` entry defines a separate firmware build with specific settings.

### **1️⃣ Standard Left Side**
```yaml
  - board: eyelash_sofle_left
    shield: nice_view
```
- **Board:** `eyelash_sofle_left` → Defines the **left half** of the keyboard.  
- **Shield:** `nice_view` → Enables **Nice!View OLED display** on this half.  
- **Purpose:** A standard left-side build with an OLED display.

---

### **2️⃣ Standard Right Side**
```yaml
  - board: eyelash_sofle_right
    shield: nice_view_custom
```
- **Board:** `eyelash_sofle_right` → Defines the **right half** of the keyboard.  
- **Shield:** `nice_view_custom` → Uses a **custom** OLED configuration (maybe different graphics/UI).  
- **Purpose:** Right half build with a custom OLED setup.

---

### **3️⃣ Left Side with ZMK Studio Support**
```yaml
  - board: eyelash_sofle_left
    shield: nice_view
    snippet: studio-rpc-usb-uart
    cmake-args: -DCONFIG_ZMK_STUDIO=y -DCONFIG_ZMK_STUDIO_LOCKING=n
    artifact-name: eyelash_sofle_studio_left
```
- **Board:** `eyelash_sofle_left` → Left side.  
- **Shield:** `nice_view` → Uses a standard OLED display.  
- **Snippet:** `studio-rpc-usb-uart` → Adds support for **ZMK Studio (RPC over USB/UART)**.  
- **CMake Args:**  
  - `CONFIG_ZMK_STUDIO=y` → Enables **ZMK Studio integration** for live keymap editing.  
  - `CONFIG_ZMK_STUDIO_LOCKING=n` → Disables key-locking features in ZMK Studio.  
- **Artifact Name:** `eyelash_sofle_studio_left` → Output file will have this name.  
- **Purpose:** Left-side build that supports **ZMK Studio** for real-time keymap changes.

---

### **4️⃣ Left Side with Settings Reset**
```yaml
  - board: eyelash_sofle_left
    shield: settings_reset
```
- **Board:** `eyelash_sofle_left` → Left side.  
- **Shield:** `settings_reset` → Enables a **factory reset function**.  
- **Purpose:** This build is likely used to **clear settings and reset the keyboard**.

---

## **🎯 Summary**
| **Build** | **Purpose** |
|-----------|------------|
| **Left + Nice!View** | Standard left half with OLED |
| **Right + Nice!View Custom** | Right half with a custom OLED display |
| **Left + ZMK Studio** | Left half with **ZMK Studio** support for live keymap changes |
| **Left + Settings Reset** | Left half firmware for **resetting settings** |
