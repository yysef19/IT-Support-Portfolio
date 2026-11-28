
<div align="center">
  <h1>☁️ RMM & Endpoint Management Lab (Action1)</h1>
  <strong>Cloud-Based Patch Management, Asset Inventory, Vulnerability Scanning & Remote Automation</strong>

  <p>
    <img src="https://img.shields.io/badge/RMM%20Platform-Action1%20Cloud-0052CC?style=flat-square&logo=icloud&logoColor=white" alt="Action1 RMM" />
    <img src="https://img.shields.io/badge/Managed%20OS-Windows%20Server%202022%20%7C%20Windows%2010-0078D6?style=flat-square&logo=windows&logoColor=white" alt="Managed OS" />
    <img src="https://img.shields.io/badge/Domain%20Integration-karem.com%20(AD%20DS)-2B579A?style=flat-square" alt="Active Directory Integration" />
  </p>
</div>
<div align="center">
  <img src="RMM-Screenshots/lab-banner.png" alt="RMM-Endpoint-Management" width="85%" />
</div>
---

## ✨ Overview

This module extends our core corporate domain infrastructure (**[`01-Windows-Helpdesk-Lab`](../01-Windows-Helpdesk-Lab)**) by integrating **Action1**, a cloud-native Remote Monitoring and Management (RMM) platform, across both the Domain Controller and domain-joined client workstations in the **`karem.com`** environment.

It demonstrates modern **Tier 1 / Tier 2 Endpoint Administration** workflows—covering agent deployment via internal SMB shares, centralized software inventory auditing, real-time CVE vulnerability detection, silent remote software deployment, and user-notified managed server reboots.

> 📄 **Full Technical Walkthrough & Verification Log:** Read the complete step-by-step documentation in **[`RMM-Lab.md`](RMM-Lab.md)**.

---

## 🏗️ RMM Integration Architecture

```mermaid
flowchart TB
    CLOUD(["☁️ Action1 Cloud Console<br/>(Centralized RMM & Patch Engine)"])

    subgraph ONPREM["🏢 On-Premises Active Directory Environment (karem.com)"]
        direction LR

        subgraph DC["🖥️ Domain Controller: ALX-DC-01"]
            direction TB
            DC_INFO["Windows Server 2022 (192.168.169.137)<br/>• Action1 Agent v6.1.728.1<br/>• Active User: KAREM\Administrator<br/>• Findings: 31 Critical / 612 Non-Critical CVEs<br/>• Action: Managed Server Reboot"]
        end

        subgraph CLIENT["💻 Client Workstation: DESKTOP-P80NB90"]
            direction TB
            CL_INFO["Windows 10 Enterprise (22H2)<br/>• Action1 Agent v6.1.728.1<br/>• Active User: KAREM\sjack04<br/>• Findings: 5 Non-Critical CVEs<br/>• Action: Silent Install (Notepad++ 8.9.9.1)"]
        end

        DC <-->|"AD DS / DNS / SMB<br/>\\ALX-DC-01\IT_Files"| CLIENT
    end

    CLOUD <==>|"HTTPS / TLS (443)<br/>Telemetry, Patching & Automation"| DC
    CLOUD <==>|"HTTPS / TLS (443)<br/>Software Deployment & Inventory"| CLIENT

    style CLOUD fill:#0052CC,stroke:#58a6ff,color:#ffffff
    style ONPREM fill:#0d1117,stroke:#30363d,color:#c9d1d9
    style DC fill:#161b22,stroke:#58a6ff,color:#c9d1d9
    style CLIENT fill:#161b22,stroke:#58a6ff,color:#c9d1d9
    style DC_INFO fill:#0d1117,stroke:#30363d,color:#c9d1d9
    style CL_INFO fill:#0d1117,stroke:#30363d,color:#c9d1d9
```

## 🖥️ Managed Endpoints

| Managed Endpoint | Role & OS | Active User Context | Agent Status | Key Operations Executed |
| :--- | :--- | :--- | :--- | :--- |
| **`ALX-DC-01.karem.com`** | Domain Controller (Windows Server 2022) | `KAREM\Administrator` | Connected | Software Audit, CVE Scan (31 Critical), Managed Reboot |
| **`DESKTOP-P80NB90.karem.com`** | Client Workstation (Windows 10 22H2) | `KAREM\sjack04` | Connected | Vulnerability Audit, Silent Deployment (Notepad++) |

---

## 📂 Folder Contents

- **[`RMM-Lab.md`](RMM-Lab.md)** — Detailed 5-phase technical documentation, operational objectives, CVE findings analysis, and verification screenshots.
- **[`RMM-Screenshots/`](RMM-Screenshots/)** — 5 sequential verification screenshots (01 through 05).

---

### ☁️ Microsoft 365 & Hybrid Cloud Integration
Directory synchronization via Entra Connect, Microsoft 365 licensing, Exchange Online, Teams governance, and Intune MDM enrollment for this domain are documented in [`03-Microsoft-365-Administration`](../03-Microsoft-365-Administration).

### 🎫 Next Step: Live Testing & Support Tickets
Critical vulnerabilities and operational hurdles across the AD and RMM environments—including Critical CVE patch remediation—are documented as structured support tickets in [`04-IT-Support-Tickets`](../04-IT-Support-Tickets).
