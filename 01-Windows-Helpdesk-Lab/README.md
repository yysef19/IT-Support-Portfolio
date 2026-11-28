 <div align="center">

  # 🖥️ Windows Helpdesk & Active Directory Lab

  **Core Windows Server 2022 & Windows 10 Enterprise Domain Administration**

  [![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-0078D6?style=flat-square&logo=windows&logoColor=white)](Helpdesk-Lab.md)
  [![Windows 10](https://img.shields.io/badge/Windows%2010-Enterprise-0078D6?style=flat-square&logo=windows&logoColor=white)](Helpdesk-Lab.md)
  [![Active Directory](https://img.shields.io/badge/Active%20Directory-AD%20DS%20%7C%20GPO%20%7C%20RSAT-2B579A?style=flat-square)](Helpdesk-Lab.md)
    <img src="Helpdesk-Lab-Screenshots/lab-banner.png" alt="Windows Helpdesk & Active Directory Lab" width="85%" />

</div>

---

## ✨ Overview

This lab documents the ground-up setup and administration of a corporate Windows domain (`karem.com`). It covers core **Tier 1 / Tier 2 IT Support** tasks including Active Directory design, Group Policy hardening, NTFS permissions, domain join, RSAT remote management, and least-privilege delegation.

> 📄 **Full Documentation & Screenshots:** View the complete 11-phase walkthrough in **[`Helpdesk-Lab.md`](Helpdesk-Lab.md)**.

---

## 🏗️ Lab Architecture

```text
                     [ VMware Virtual Network ]
                                  │
          ┌───────────────────────┴───────────────────────┐
          ▼                                               ▼
┌─────────────────────┐                         ┌─────────────────────┐
│   Domain Controller │                         │  Client Workstation │
│      ALX-DC-01      │◄──── DNS / Kerberos ───►│   DESKTOP-P80NB90   │
│ Windows Server 2022 │      192.168.169.137    │ Windows 10 Enterprise│
└──────────┬──────────┘                         └──────────┬──────────┘
           │                                               │
           ├─► Domain: karem.com (KAREM)                   ├─► Domain-Joined Client
           ├─► OUs: IT, HR, Sales                          ├─► User Logon: karem\sjack04
           ├─► GPO: HR Screen Lock & USB Block             ├─► Mapped Drive: Z: (\\ALX-DC-01\IT_Files)
           └─► RBAC: Sales Password Reset Delegation       └─► Remote Admin: RSAT (ADUC)
```

| Role | Hostname / Details |
| --- | --- |
| **Domain & Forest** | `karem.com` (NetBIOS: `KAREM`) |
| **Domain Controller** | `ALX-DC-01` — Windows Server 2022 (`192.168.169.137`) |
| **Client Workstation** | `DESKTOP-P80NB90` — Windows 10 Enterprise |

---

## 📂 Folder Contents

* **[`Helpdesk-Lab.md`](Helpdesk-Lab.md)** — Detailed step-by-step technical documentation, command reference, and troubleshooting log.
* **[`Helpdesk-Lab-Screenshots/`](Helpdesk-Lab-Screenshots/)** — 11 sequential verification screenshots (`01` through `11`).

---

### 🛠️ RMM & Endpoint Management Integration
Centralized remote monitoring, automated patch deployment, and vulnerability remediation for `ALX-DC-01` and `DESKTOP-P80NB90` via Action1 RMM are documented in [`02-RMM-Patch-Management`](../02-RMM-Patch-Management).

### 🎫 Next Step: Live Testing & Support Tickets
Practical troubleshooting scenarios and incident resolution logs for this environment are documented separately in [`04-IT-Support-Tickets`](../04-IT-Support-Tickets).
