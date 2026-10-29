<div align="center">

<img src="assets/logo.png" alt="ALJO ULDX Logo" width="380" />

# ALJO ULDX
### Precision Aviation ULD Tracking & Ramp Yard Control System
**Engineered for Cargo Handlers, Ramp Control, Airlines & Logistics Hubs**

[![Version](https://img.shields.io/badge/version-v1.0.0-0ea5e9.svg?style=for-the-badge)](https://github.com/alenjoby/aljo-uldx-releases/releases/latest)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011%20(x64)-1e293b.svg?style=for-the-badge&logo=windows)](https://github.com/alenjoby/aljo-uldx-releases/releases/latest)
[![Aviation Compliance](https://img.shields.io/badge/IATA-Resolution%20687%20Compliant-10b981.svg?style=for-the-badge)](https://github.com/alenjoby/aljo-uldx-releases)
[![Offline First](https://img.shields.io/badge/Database-100%25%20Offline%20SQLite-f59e0b.svg?style=for-the-badge&logo=sqlite)](https://github.com/alenjoby/aljo-uldx-releases)
[![Auto Update](https://img.shields.io/badge/Auto--Update-Enabled%20(Zero%20Data%20Loss)-6366f1.svg?style=for-the-badge)](https://github.com/alenjoby/aljo-uldx-releases)

<br />

[⬇️ **Download Latest Windows Installer (v1.0.0)**](https://github.com/alenjoby/aljo-uldx-releases/releases/latest/download/ALJO-ULDX-Setup-1.0.0.exe) &nbsp;&bull;&nbsp; [📋 Release Notes](#-release-notes) &nbsp;&bull;&nbsp; [📖 User Guide](#-core-capabilities) &nbsp;&bull;&nbsp; [🎙️ Request Features](#-feature-requests--support)

---

</div>

## ✈️ Overview

**ALJO ULDX** is an enterprise desktop workstation application built specifically for air cargo operations, airport ramp teams, freight forwarders, and airline station coordinators. It replaces fragile manual spreadsheets with an ultra-responsive, zero-friction desktop control center that operates **100% offline** with zero cloud dependencies.

From real-time ULD yard tracking and natural serial sorting, to AI-assisted multi-workspace Excel imports, formal IATA Air Waybill handover sheets, and automated background sync across workstations, ALJO ULDX provides precision control over every container, pallet, and strap on your station.

---

## ⚡ Core Capabilities

```
┌────────────────────────────────────────────────────────────────────────┐
│                              ALJO ULDX                                 │
├────────────────────┬────────────────────┬──────────────────────────────┤
│  📦 ULD REGISTER   │  🔄 YARD MOVEMENTS │  📑 LEASING & DEMURRAGE      │
│  • Instant inline  │  • IN / OUT flows  │  • Lessor tracking           │
│  • Natural serial  │  • Origin / Dest   │  • Lease start/end dates     │
│  • Serviceability  │  • Flight & Sector │  • Overdue & idle detection  │
│  • Connector nets  │  • Full audit log  │  • Demurrage cost prevention │
└────────────────────┴────────────────────┴──────────────────────────────┘
```

### 1. 📦 Natural Serial-Wise ULD Sorting
Airport staff think in sequential container series (`PMC432`, `PMC501`, `PMC502`, `PMC503`, `PMC876`). ALJO ULDX parses the IATA 3-letter contour prefix, numeric serial number, and carrier code to sort every view naturally and numerically—eliminating alphabetical sorting errors where `PMC1000` is placed ahead of `PMC50`.
- Active across **Stock Register Tables**, **Excel Import Previews**, and **Exported Handover PDFs**.

### 2. ⚡ Real-Time Spreadsheet Register & Yard Movements
- **Zero-Friction Editing:** Immediate keyboard navigation (Tab / Shift+Tab, Enter, Arrows), instant inline typing, and millisecond auto-commit to disk.
- **Bi-Directional Movements:** Log container arrivals (`IN`) or dispatches (`OUT`) individually or in bulk.
- **Rich Operational Data:** Flight numbers, sectors (e.g. `SHJ-FZE`, `DXB-LHR`), destination IATA codes, custody handlers, tare weights, net/connector numbers, and remarks.
- **Audit Trails & Correction Log:** Mistyped a flight or destination? One-click movement corrections preserve a complete immutable history for audits.

### 3. 🧠 Smart Aviation Excel Importer
Import legacy daily handover files, agent spreadsheets, or customer stock sheets in seconds:
- **Resilient IATA Detection:** Multi-tier pattern matching extracts valid ULD codes across messy formats (`PMC 12345 EK`, `AKE54321GF`, `PAG-99881-PXA`).
- **Smart Noise Rejection:** Automatically identifies and discards date stamps, header rows, month names, and non-ULD remarks columns (`REMARKS`, `FEB-24`, etc.).
- **Multi-Workspace Auto-Routing:** Intelligently allocates destination codes and routing across multiple flight groups in a single workbook.
- **Range-Select Precision:** Click and drag directly on spreadsheet grids to scope imports to specific cell regions.

### 4. 📄 Formal IATA Air Waybill Handover & PDF Stock Sheets
- **Print & PDF Generation:** Generates clean, crisp A4 handover sheets in both Landscape and Portrait orientations.
- **Digital Signature Handover:** Built-in dual signature pads capture Dispatched By and Received By staff signatures, names, IDs, and timestamps directly on screen.
- **Instant Print Preview:** Live in-app PDF rendering via embedded PDF engine with custom filename generator.

### 5. ✈️ 9,053 Global Airports Offline Reference
- Integrated with the **OurAirports Open Aviation Database**.
- Instant autocomplete for every commercial and cargo airport worldwide (IATA, ICAO, airport name, city, country flag).
- Add custom station codes (e.g. `SHJ-FZE`, `CARGO-YARD-2`, `MAINT-HANGAR-4`) on the fly.

### 6. 🌙 Aero Light & Pure Black Dark Themes
- **Pure Black Dark Mode:** Tailored for dark ramp control towers, night shifts, and battery saving on portable laptops.
- **Aero Crisp Light Mode:** High-contrast daylight theme for sunlit warehouse offices.
- **Eye Comfort UI Zoom:** Dedicated zoom scale (40% to 150%) via Top Toolbar or keyboard shortcuts (`Ctrl +` / `Ctrl -` / `Ctrl 0`).

---

## 🔄 Automatic Zero-Touch Updates

ALJO ULDX includes a seamless background updater connected directly to this repository:

1. **Automatic Delivery:** Whenever developer **Alen Joby** publishes a new version to this repository, all installed computers receive the update automatically.
2. **100% Data Preservation:** Your active SQLite database and all historical backups are stored securely in `%APPDATA%/aljo-uldx/uld_manager.sqlite`. **Updates only replace executable code—your data is never touched or overwritten.**
3. **One-Click Restart:** When an update finishes downloading in the background, a notification banner appears. Click **Restart & Apply Now** to relaunch immediately on the newest version.

---

## 🎙️ Direct Developer Feedback & Voice Notes

Need a new custom column? Want an extra export format? Found an edge-case flight sheet?

ALJO ULDX includes a direct hotline to the developer:
- Click the **💡 Request Feature** button in the top toolbar or within Settings.
- Type your feedback or **record a voice note (up to 3 minutes)** directly using your microphone.
- Hit **Send** — your message and audio recording are securely delivered directly to developer Alen Joby (`alenjoby955@gmail.com`).

---

## 💻 System Requirements

| Specification | Minimum Requirement | Recommended |
|---|---|---|
| **Operating System** | Windows 10 (64-bit) | Windows 11 (64-bit) |
| **Processor** | Dual-core 1.8 GHz | Quad-core 2.4 GHz or higher |
| **Memory (RAM)** | 2 GB | 4 GB+ |
| **Storage** | 300 MB free space | 1 GB free space (for SQLite backups) |
| **Display** | 1280 × 720 | 1920 × 1080 Full HD |
| **Network** | Offline (No internet required for tracking) | Internet required only for auto-updates & voice feedback |

---

## 🚀 Installation Guide

1. Head to the [**Latest Release Page**](https://github.com/alenjoby/aljo-uldx-releases/releases/latest).
2. Download the installer: `ALJO ULDX Setup 1.0.0.exe`.
3. Run the installer:
   - Select your preferred installation directory (default: `%LOCALAPPDATA%\Programs\aljo-uldx`).
   - A desktop shortcut and Start Menu shortcut will be created automatically.
4. Launch **ALJO ULDX** and start managing your ULD yard!

> [!TIP]
> **Existing Installations:** Do not uninstall your previous version when updating manually. The installer automatically preserves your `%APPDATA%` database.

---

## 🛡️ Data Safety & Integrity Architecture

- **SQLite Database Engine:** Industry standard ACID-compliant SQLite engine running in native WebAssembly.
- **Automated Snapshots:** On-demand and pre-restore database backups saved with millisecond timestamps.
- **Integrity Checker:** Built-in PRAGMA integrity verification in Settings ensures zero data corruption.
- **Uninstall Protection:** NSIS configuration preserves all user data even if the application is uninstalled.

---

## 👨‍💻 Author & Engineering

**ALJO ULDX** is designed, developed, and maintained by:

**Alen Joby**  
Aviation Systems Engineering & Software Development  
📧 **Email:** [alenjoby955@gmail.com](mailto:alenjoby955@gmail.com)  
🌐 **Source Repository:** Private Enterprise Codebase

---

<div align="center">
  <sub>Copyright &copy; 2026 Alen Joby. All rights reserved. Precision Aviation ULD Tracking & Yard Control.</sub>
</div>
