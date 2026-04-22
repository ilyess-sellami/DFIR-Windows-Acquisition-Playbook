# 🛡️ DFIR Windows Acquisition Playbook

## ❓ Scenario

A Windows machine is suspected to be **compromised**.

Possible indicators include:
- Suspicious processes or malware execution
- Unknown network connections or C2 traffic
- Evidence of persistence mechanisms
- Potential data exfiltration or credential theft

The system may still be **live or already powered off**, requiring a structured forensic acquisition approach.

---

## 🎯 Objectives

This playbook provides a **standardized DFIR acquisition workflow** to:

- Preserve **volatile evidence first (memory, live data)**
- Collect **disk-level forensic images**
- Extract **Windows artifacts (logs, registry, persistence)**
- Recover **user and attacker activity traces**
- Enable **timeline reconstruction of the incident**
- Support **incident response and forensic investigation**

---

## 📚 Table of Contents

1. 🧠 Memory Acquisition (RAM Dump)
2. ⚡ Live System Collection (Processes & Network)
3. 💾 Disk Imaging (Full Forensic Image)
4. 📜 Windows Event Logs
5. 🧬 Registry Artifacts & Persistence
6. 📁 User Artifacts (AppData / Temp / Downloads)
7. 🌐 Browser Artifacts
8. ⏱️ Timeline Artifacts (MFT, Prefetch, Amcache)
9. 🌍 Network Artifacts
