# Browser Artifacts

## Why are we collecting Browser Artifacts?

After collecting user-level artifacts, **browser data provides direct insight into web-based activity**, which is one of the most common initial access vectors.

Attackers frequently rely on browsers for:

- Phishing attacks
- Malware downloads
- Credential harvesting
- Command & Control (C2) via web protocols

Browser artifacts help reconstruct **what the user (or attacker) accessed, downloaded, and executed**.

---

## Why Browser Artifacts are Critical

Browser data helps investigators uncover:

- **Initial Infection Vector**
    - Malicious URLs visited
    - Phishing websites accessed

- **Malware Delivery**
    - Downloaded payloads
    - Drive-by downloads

- **Credential Access**
    - Stored credentials
    - Login activity and autofill data

- **User Behavior**
    - Search queries
    - Browsing patterns and timelines

- **Command & Control Activity**
    - Connections to suspicious domains
    - Web-based attacker infrastructure

---

## Key Browser Artifact Locations

### Google Chrome

```bash
C:\Users\<USER>\AppData\Local\Google\Chrome\User Data\
```

Chrome stores complete **browsing history, downloads, cookies, sessions, and saved credentials**, making it one of the richest forensic sources.

---

### Microsoft Edge (Chromium-based)

```bash
C:\Users\<USER>\AppData\Local\Microsoft\Edge\User Data\
```

Edge uses the same Chromium structure as Chrome, providing **similar artifacts including history, downloads, and web sessions**.

---

### Mozilla Firefox

```bash
C:\Users\<USER>\AppData\Roaming\Mozilla\Firefox\Profiles\
```

Firefox stores browser data in profile folders, including **history, bookmarks, cookies, and form data**, often used to track user behavior.

---

## High-Value Browser Files

Within each browser profile, prioritize collecting:

### History & Activity

```bash
History (Chrome/Edge)
places.sqlite (Firefox)
```

Contains visited URLs, timestamps, and frequency — critical for identifying **malicious domains and attack timelines**.

---

### Downloads

```bash
Download History (within History DB)
```

Tracks downloaded files, including **malware payloads and attacker tools**, even if the files were deleted.

---

### Cookies

```bash
Cookies (Chrome/Edge)
cookies.sqlite (Firefox)
```

Contains saved credentials (encrypted), which may indicate **compromised accounts or attacker access**.

---

### Credentials

```bash
Login Data (Chrome/Edge)
logins.json (Firefox)
```

Contains **saved credentials (encrypted)**, which may indicate compromised accounts or unauthorized access.

---

### Credit Card Data

```bash
Web Data (Chrome/Edge)
```
Stores autofill data including **credit card information (encrypted)**, billing details, and form inputs — valuable for detecting financial data theft or fraud activity.

---

### Extensions

```bash
Extensions\
```

Browser extensions can be abused for **persistence, data exfiltration, credential harvesting, or injecting malicious scripts**. Investigating installed extensions helps identify rogue or attacker-installed add-ons.

---

### Cache & Sessions

```bash
Cache\
Session Storage\
```

May contain temporary web content, scripts, authentication data, and traces of attacker infrastructure not stored elsewhere.

---

## Recommended Method: Manual Collection (Best Practice)

To ensure **maximum forensic integrity**, browser artifacts should be collected manually.

### Step 1 — Identify Browser Profiles

Check for installed browsers in user directories:

```bash
C:\Users\<USER>\AppData\Local\
C:\Users\<USER>\AppData\Roaming\
```

---

### Step 2 — Copy Browser Data

Using a **trusted external USB / forensic drive**, collect:

```bash
C:\Users\<USER>\AppData\Local\Google\Chrome\User Data\
C:\Users\<USER>\AppData\Local\Microsoft\Edge\User Data\
C:\Users\<USER>\AppData\Roaming\Mozilla\Firefox\Profiles\
```

---

### Step 3 — Preserve Evidence Integrity

- Do NOT open browsers on the suspect machine
- Preserve timestamps (MAC times)
- Hash collected data (MD5/SHA256)
- Maintain chain of custody