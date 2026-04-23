# Windows Event Logs

## Why are we collecting Windows Event Logs?

After acquiring memory and disk images, Windows Event Logs provide a **chronological record of system and user activity**.

They are one of the most valuable sources for reconstructing attacker behavior and identifying **initial access, persistence, lateral movement, and impact**.

Unlike memory (volatile) and disk (static), event logs offer **structured, timestamped evidence** of what happened on the system.

**⚠️ Golden Rule of DFIR :**

> “Logs tell the story — preserve them before they are overwritten or cleared.”

---

## Why Windows Event Logs are Critical?

Event logs help investigators uncover:

- **Authentication Activity**
    - Successful and failed logins (brute force attempts)
    - Logon types (interactive, remote, RDP)

- Privilege Escalation