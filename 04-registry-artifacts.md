# Registry Artifacts & Persistence

## Why are we collecting Registry Artifacts?

The Windows Registry provides **a centralized database of system and user activity**, making it a critical forensic source.

It contains valuable evidence related to **persistence mechanisms, executed programs, system configuration, and user behavior**.

Unlike event logs (structured) and disk files (static), the registry stores granular configuration changes and historical traces that attackers often rely on.

**⚠️ Golden Rule of DFIR :**

> “Persistence almost always leaves a trace in the Registry.”

---

## Why Registry Forensics is Critical

Registry analysis helps investigators uncover:

- **Persistence Mechanisms**
    - Auto-start entries (Run / RunOnce keys)
    - Malicious services and scheduled execution

- **User Activity**
    - Recently executed programs (UserAssist, RunMRU)
    - Opened files and system interaction traces

- **System Configuration**
    - Installed software and OS settings
    - Security policies and environment configuration

- **Device & External Activity**
    - USB device connection history
    - Mounted drives and external storage usage

---

## Key Registry Hives to Collect

The most important registry hives in Windows DFIR:

- **SAM :** User accounts and authentication data
- **SYSTEM :** Services, drivers, and system configuration
- **SOFTWARE :** Installed applications and system settings
- **SECURITY :** Local security policies and permissions
- **NTUSER.DAT :** User-specific activity and preferences
- **USRCLASS.DAT :** User shell and GUI-related artifacts

**Default Locations :**

``C:\Windows\System32\config\``

``C:\Users\<username>\``

---

## Best Free Tools for Registry Analysis

### 1. Registry Explorer (Recommended)

A powerful forensic registry viewer that enables deep analysis of offline hive files with advanced search and bookmarking features. It simplifies complex registry structures and helps investigators quickly identify suspicious keys and persistence mechanisms.

---

### 2. RegRipper

A command-line forensic tool that extracts and interprets registry artifacts using predefined plugins tailored for DFIR investigations. It automates parsing and produces structured outputs that highlight relevant evidence such as persistence and user activity.

---

### 3. KAPE

A fast incident response tool used to collect and process registry hives along with other forensic artifacts from compromised systems. It supports targeted acquisition and automated parsing, making it ideal for large-scale or time-sensitive investigations.

---

## Recommended Method: Manual Collection (Best Practice)

To ensure **maximum forensic integrity**, the best approach is to **manually copy raw registry hive files first**, then analyze them offline.

### Step 1 — Locate Registry Hives

#### System Registry Hives

``C:\Windows\System32\config\``

This folder contains the main system registry databases:

- SAM
- SYSTEM
- SOFTWARE
- SECURITY