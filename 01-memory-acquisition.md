# Memory Acquisition (RAM Forensics)

## ❓ Why are we collecting memory first?

When a Windows system is compromised, the most valuable evidence often exists in **RAM (volatile memory)**.

Unlike disk artifacts, memory contains **live execution state**, which disappears immediately when the system shuts down or restarts.

This makes memory acquisition the **highest priority step in any DFIR investigation**.

**⚠️ Golden Rule of DFIR :**

> 🧠 “If the machine is ON → memory must be acquired FIRST.”

---

## 🎯 Why Memory Forensics is Critical

Memory analysis helps investigators uncover:

1. **Fileless Malware :** Attackers often execute payloads directly in memory without writing files to disk.

2. **Injected Code & Processes :** Malware may inject code into legitimate processes (e.g., explorer.exe, svchost.exe).

3. **Active Network Connections :** Live C2 (Command & Control) sessions are visible only in memory.

4. **Credentials & Secrets :** Memory may contain Passwords, Kerberos tickets, API keys, Encryption keys, ...

5. **Decrypted Payloads :** Even if malware is encrypted on disk, it is often **decrypted in RAM during execution**.

---

## 🧰 Best Free Tools for Memory Acquisition

We focus on **trusted, widely used, free DFIR tools**:

### 🔧 1. DumpIt (Recommended)

<p align="center">
  <img src="docs/dumpit-ram-capture.png" alt="DumpIt RAM Capture" width="100%" />
</p>

DumpIt is a lightweight one-click tool used to capture full physical memory in DFIR investigations.  It is widely used in incident response due to its speed and minimal system interaction.

---

### 🔧 2. Magnet RAM Capture

<p align="center">
  <img src="docs/magnet-ram-capture.png" alt="Magnet RAM Capture" width="100%" height="60%" />
</p>

Magnet RAM Capture is a free forensic tool used to acquire physical memory from Windows systems.  It provides a simple GUI interface, making it suitable for quick and reliable evidence collection.

---

### 🔧 3. Belkasoft Live RAM Capturer

<p align="center">
  <img src="docs/belkasoft-ram-capture.png" alt="Belkasoft RAM Capture" width="100%" />
</p>

Belkasoft Live RAM Capturer is a lightweight forensic tool used to acquire physical memory with minimal system impact.  
It is commonly used in DFIR cases where stealth and fast acquisition are required.

---

## 🧪 Recommended Method: DumpIt (Step-by-Step)

<p align="center">
  <img src="docs/dumpit-full-ram-capture.png" alt="DumpIt Full RAM Capture" width="100%" />
</p>

To perform memory acquisition using DumpIt, start by preparing a secure environment with a clean USB drive and sufficient external storage space (recommended: at least 1.2× the system RAM size). Execute `DumpIt.exe` with administrator privileges, which will prompt you to confirm the acquisition process. Once confirmed by pressing `y`, the tool will begin capturing the full physical memory by locking a snapshot of the system’s RAM.

The acquisition duration depends on the system’s memory size, ranging from a few minutes on smaller systems to longer on high-memory machines. During this process, it is critical to avoid any interaction with the system to preserve evidence integrity. Once completed, DumpIt generates a memory image file in the format `<hostname>-<date>.raw`, which should be securely stored for further forensic analysis.