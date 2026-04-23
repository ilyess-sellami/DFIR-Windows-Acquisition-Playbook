# User Artifacts (AppData / Temp / Downloads)

## Why are we collecting User Artifacts?

After system-level evidence (memory, disk, logs, registry), user artifacts provide direct **visibility into human and attacker activity on the system**.

These locations often contain **executed payloads, staging directories, exfiltrated data, and malware traces** that are frequently overlooked.

They are especially valuable for identifying:

- Initial execution of malware
- Staging of tools and payloads
- Data theft and file collection
- Execution traces of attacker behavior

---

## Why User Artifacts are Critical

User directories often contain the most actionable forensic evidence:

- **Malware Execution**
    - Dropped executables and scripts
    - Fileless loader staging files

- **Persistence Traces**
    - Startup shortcuts (.lnk files)
    - Payload drop locations

- **Data Exfiltration**
    - Archived sensitive files (ZIP, RAR, 7z)
    - Staging folders for transfer tools

- **Execution Evidence**
    - Recently accessed files
    - Suspicious binaries and scripts

---

## Key User Artifact Locations (Full Paths)

### User Profile Root

```bash
C:\Users\<USER>\
```

This is the root of all user activity and contains access to every personal directory where attackers may operate or store data.

---

### AppData (HIGH PRIORITY)

```bash
C:\Users\<USER>\AppData\Roaming\
C:\Users\<USER>\AppData\Local\
C:\Users\<USER>\AppData\LocalLow\
```

AppData is the **most abused location by malware** for storing payloads, configuration files, persistence mechanisms, and stealthy execution components.

---

### Critical sub-paths to prioritize:

```bash
C:\Users\<USER>\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\
C:\Users\<USER>\AppData\Local\Microsoft\Windows\INetCache\
C:\Users\<USER>\AppData\Local\Packages\
```

- **Startup →** Common persistence location (auto-executed malware)
- **INetCache →** Stores downloaded web content and potential payloads
- **Packages →** Used by modern apps; may hide attacker artifacts

---

### Temp Directories (VERY HIGH VALUE)

```bash
C:\Users\<USER>\AppData\Local\Temp\
C:\Windows\Temp\
```

Temporary directories are heavily used by attackers to **drop, extract, and execute payloads**, often leaving behind short-lived but critical forensic traces.

---

### Downloads Folder

```bash
C:\Users\<USER>\Downloads\
```

This is typically the **initial entry point of malware**, containing phishing attachments, downloaded payloads, and attacker-delivered tools.

---

### Desktop & Documents

```bash
C:\Users\<USER>\Desktop\
C:\Users\<USER>\Documents\
```

These folders often contain **user-accessible files**, staged data, or sensitive documents targeted for exfiltration by attackers.

---

## Recommended Method: Manual Collection (Best Practice)

To ensure **maximum forensic integrity**, user artifacts should be collected manually from a trusted forensic environment.

### Step 1 — Identify Target Users

```bash
C:\Users\
```

- Enumerate all user profiles
- Focus on active, recent, or suspicious accounts

---

### Step 2 — Copy User Artifact Directories

```bash
C:\Users\<USER>\AppData\
C:\Users\<USER>\Downloads\
C:\Users\<USER>\Desktop\
C:\Users\<USER>\Documents\
C:\Users\<USER>\AppData\Local\Temp\
C:\Windows\Temp\
```

---

### Step 3 — Focus on Suspicious Files

Look for:

- Executables and scripts (``.exe``, ``.dll``, ``.ps1``, ``.bat``, ``.vbs``)
- Archives (``.zip``, ``.rar``, ``.7z``, ``.iso``)
- Recently created or modified files
- Files with random or suspicious naming patterns

---

### Step 4 — Preserve Evidence Integrity

- Do NOT open or execute files
- Preserve **timestamps (MAC times)**
- Generate hashes (MD5/SHA256)
- Maintain chain of custody documentation