# Network Artifacts

## Why are we collecting Network Artifacts?

After analyzing host-based artifacts, network artifacts **provide visibility into external communication and attacker infrastructure**.

They help investigators understand:

- Who the system communicated with
- What data may have been exfiltrated
- Whether Command & Control (C2) channels were established

Network evidence is critical for identifying **attacker infrastructure, lateral movement, and data exfiltration paths**.

---

## Why Network Artifacts are Critical

Network data helps investigators uncover:

- **Command & Control (C2)**
  - Connections to malicious IPs/domains
  - Beaconing behavior
  
- **Data Exfiltration**
  - Large outbound transfers
  - Suspicious protocols (FTP, HTTP POST, DNS tunneling)

- **Lateral Movement**
  - SMB, RDP, WinRM connections
  - Internal scanning activity

- **Initial Access**
  - Download of payloads
  - External exploit communication

---

## Recommended Method

### Step 1 — Live Response (If System is ON)

Collect volatile data:

```bash
ipconfig /all
arp -a
netstat -ano
route print
```

- Captures **active connections and network configuration**
- Identifies potential C2 communication in real time

---

### [Step 2 — Memory Acquisition](01-memory-acquisition.md)

Acquire RAM (DumpIt, etc.) to : 

- Extract DNS cache, sockets, and live connections
- Recover decrypted network data

---

### Step 3 — Collect Persistent Logs

```bash
C:\Windows\System32\LogFiles\Firewall\
C:\Windows\System32\winevt\Logs\
```

- Provides historical network activity
- Helps reconstruct past connections

---

### [Step 4 — Collect User-Level Network Evidence](05-user-artifacts-appdata-temp.md)

```bash
C:\Users\<USER>\AppData\
```

- Browser artifacts reveal external communication and downloads
