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
