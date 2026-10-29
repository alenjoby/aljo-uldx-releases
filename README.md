<div align="center">

<img src="assets/logo.png" alt="ALJO ULDX Logo" width="360" />

# ALJO ULDX
### Precision Aviation ULD Tracking & Ramp Yard Control
**Built for Station Managers, Ramp Coordinators, Air Cargo Operators & Logistics Hubs**

[![Release](https://img.shields.io/github/v/release/alenjoby/aljo-uldx-releases?color=0284c7&label=Release&style=flat-square)](https://github.com/alenjoby/aljo-uldx-releases/releases/latest)
[![Platform](https://img.shields.io/badge/Platform-Windows%20x64-334155?logo=windows&logoColor=white&style=flat-square)](https://github.com/alenjoby/aljo-uldx-releases/releases/latest)
[![Architecture](https://img.shields.io/badge/Architecture-Offline--First%20SQLite-059669?logo=sqlite&logoColor=white&style=flat-square)](https://github.com/alenjoby/aljo-uldx-releases)
[![Standard](https://img.shields.io/badge/Standard-IATA%20Res%20687-0284c7?style=flat-square)](https://github.com/alenjoby/aljo-uldx-releases)
[![Sync](https://img.shields.io/badge/Updates-Automated%20Background%20Sync-6366f1?logo=github&logoColor=white&style=flat-square)](https://github.com/alenjoby/aljo-uldx-releases)

<br />

[**Download Windows Installer (v1.0.0)**](https://github.com/alenjoby/aljo-uldx-releases/releases/latest/download/ALJO-ULDX-Setup-1.0.0.exe) &nbsp;&bull;&nbsp; [System Specifications](#system-specifications) &nbsp;&bull;&nbsp; [Deployment Guide](#deployment--installation) &nbsp;&bull;&nbsp; [Update Architecture](#automated-update-architecture)

---

</div>

## Overview

**ALJO ULDX** is an industrial desktop workstation system engineered for aviation ground handling, air cargo terminals, and freight forwarders. It delivers high-density, real-time control over unit load devices (containers, pallets, and nets) with an embedded, zero-latency database operating entirely offline.

Designed to replace fragile spreadsheets and error-prone manual handovers, ALJO ULDX provides natural numeric serial sorting, heuristic Excel ingestion, Air Waybill PDF stock sheets with integrated digital signature capture, and automated background sync with full data persistence.

---

## Architectural Highlights

```
+--------------------------------------------------------------------------------+
|                                ALJO ULDX CLIENT                                |
+-----------------------+--------------------------------+-----------------------+
|   STOCK REGISTER      |       RAMP YARD MOVEMENTS      |  LEASING & DEMURRAGE  |
|   - Inline Fast-Entry |       - IN / OUT Audit Records |  - Lessor Tracking    |
|   - Serial-Wise Order |       - Flight / Sector Routing|  - Lease Period Timer |
|   - Damage Reporting  |       - Custody Attribution   |  - Demurrage Alert    |
|   - Net / Straps Link |       - Movement Corrections   |  - Cost Mitigation    |
+-----------------------+--------------------------------+-----------------------+
|  STORAGE: %APPDATA%/aljo-uldx/uld_manager.sqlite (100% Offline ACID Database)  |
|  AIRPORTS: 9,053 Global Stations (IATA / ICAO) Embedded Reference Dataset      |
+--------------------------------------------------------------------------------+
```

---

## System Capabilities

### 1. Natural Serial-Wise ULD Ordering
Aviation ramp personnel identify containers by contour type and numeric sequence (e.g., `PMC432`, `PMC501`, `PMC502`, `PMC503`, `PMC876`). ALJO ULDX separates the IATA 3-character prefix, numeric serial, and airline suffix to sort every view numerically. This prevents conventional alphabetical sorting flaws where `PMC1000` precedes `PMC50`.
- Applied consistently across the active stock register, Excel import previews, and exported handover reports.

### 2. High-Density Stock Register & Yard Movements
- **Keyboard-Centric Grid:** Immediate keyboard navigation (`Tab`, `Shift+Tab`, `Enter`, arrows) with sub-millisecond local SQLite commits.
- **Bi-Directional Yard Operations:** Rapid single-entry and bulk logging of unit arrivals (`IN`) and dispatches (`OUT`).
- **Comprehensive Metadata:** Flight numbers, sector routing (e.g., `SHJ-FZE`, `DXB-LHR`), destination codes, custody handoff, tare weight, connector net numbers, and operational remarks.
- **Auditable Correction Trails:** One-click movement corrections preserve a permanent, non-destructive audit trail for compliance verification.

### 3. Heuristic Excel Ingestion & Extraction
Import third-party manifests, airline stock sheets, and daily handover workbooks without manual formatting:
- **Resilient Regex Engine:** Extracts valid IATA ULD identifiers across irregular formats (`PMC 12345 EK`, `AKE54321GF`, `PAG-99881-PXA`).
- **Automated Noise Suppression:** Distinguishes ULD records from dates, months, and descriptive comments (`REMARKS`, `FEB-24`, etc.).
- **Multi-Workspace Assignment:** Routes destination codes and sectors across distinct flight sections within a single spreadsheet.
- **Range-Select Ingestion:** Allows operators to highlight and scope imports directly to specific cell ranges.

### 4. IATA Handover & Digital Signature Stock Sheets
- **Vector PDF Output:** Generates standardized A4 stock sheets in both landscape and portrait orientations.
- **Dual Signature Capture:** Integrated signature pads record Dispatched By and Received By personnel signatures, staff IDs, names, and timestamps directly on the workstation.
- **Integrated Print Engine:** Instant in-app PDF rendering via embedded viewer.

### 5. Global Airport Reference Database
- **9,053 Stations:** Comprehensive offline IATA and ICAO airport dataset powered by OurAirports.
- **Instant Autocomplete:** Type-ahead search indexing IATA code, municipality, airport name, and country flag.
- **Custom Location Codes:** Define internal yard codes and ramp zones (e.g., `SHJ-FZE`, `RAMP-ZONE-3`, `HANGAR-B`).

### 6. Dual-Mode Interface & Optical Zoom Scaling
- **Pure Black Dark Mode:** High-contrast palette designed for darkened ramp control centers and low-light night shifts.
- **Aero Crisp Light Mode:** High-readability daylight theme for standard terminal offices.
- **Proportional UI Zoom:** Scale the entire application interface between 40% and 150% (`Ctrl +`, `Ctrl -`, `Ctrl 0`) to accommodate warehouse tablets or ultra-wide monitoring displays.

---

## Automated Update Architecture

ALJO ULDX features a background update delivery pipeline designed for enterprise reliability:

```
[ Developer: Alen Joby ]
         |
         v (npm run release)
[ Public Release Manifest ] --> (aljo-uldx-releases/releases/latest)
                                         |
                                         v (Silent Background Poll)
                            [ Installed Workstations ]
                                         |
                                         v (Download in Background)
                             [ Notification Banner ]
                                         |
                                         v (Restart & Apply Now)
                             [ Binaries Swapped (3 sec) ]
                                         |
                                         +--> Active SQLite DB Untouched
                                         +--> %APPDATA% Completely Preserved
```

- **Zero-Touch Background Sync:** The application queries the public release feed 5 seconds after startup and downloads newer releases silently.
- **100% Data Preservation:** The user database (`uld_manager.sqlite`) resides in `%APPDATA%/aljo-uldx/`, isolated from application binaries. Updating never modifies, resets, or overwrites existing records.
- **Non-Disruptive Notification:** When an update is ready, a discrete top banner and Settings card allow the operator to restart immediately or continue working until their shift ends.

---

## In-App Feedback & Voice Notes

Operators can submit feature requests or operational reports directly to the engineering team:
- Access via the **Request Feature** button in the primary toolbar or within Settings.
- Submit text descriptions or **record an audio voice note (up to 3 minutes)** via microphone.
- Form submissions and voice recordings are delivered directly to **alenjoby955@gmail.com** via Web3Forms.

---

## System Specifications

| Parameter | Minimum | Recommended |
|---|---|---|
| **Operating System** | Windows 10 (64-bit, Build 19041+) | Windows 11 (64-bit) |
| **Processor** | Intel Core i3 / AMD Ryzen 3 (2.0 GHz) | Intel Core i5 / AMD Ryzen 5 or higher |
| **Memory (RAM)** | 2 GB | 4 GB+ |
| **Storage** | 350 MB disk space | 1 GB+ (for historical database backups) |
| **Display Resolution** | 1280 x 720 | 1920 x 1080 Full HD |
| **Connectivity** | 100% Offline | Internet required only for automated updates |

---

## Deployment & Installation

1. Download the executable: [**ALJO-ULDX-Setup-1.0.0.exe**](https://github.com/alenjoby/aljo-uldx-releases/releases/latest/download/ALJO-ULDX-Setup-1.0.0.exe).
2. Execute the installer:
   - Destination defaults to `%LOCALAPPDATA%\Programs\aljo-uldx`.
   - Desktop and Start Menu shortcuts are configured automatically.
3. Launch **ALJO ULDX**.

> [!NOTE]
> When updating manually from an executable, do not uninstall the previous version. Running the new installer directly updates application binaries while maintaining all existing database files.

---

## Data Persistence & Integrity

- **Storage Engine:** ACID-compliant SQLite via WebAssembly with write-ahead atomic operations.
- **Automatic Snapshots:** On-demand and pre-restore database backups created with ISO timestamping.
- **Integrity Validation:** Direct SQLite `PRAGMA integrity_check` accessible from the Settings panel.
- **Safe Uninstallation:** Application packaging includes explicit flags preventing user data removal upon uninstallation.

---

## Developer & Contact

**ALJO ULDX** is engineered and maintained by:

**Alen Joby**  
Aviation Systems Engineering & Software Development  
Email: [alenjoby955@gmail.com](mailto:alenjoby955@gmail.com)  
Releases: [github.com/alenjoby/aljo-uldx-releases](https://github.com/alenjoby/aljo-uldx-releases)  
Source Repository: Private Enterprise Access

---

<div align="center">
  <sub>Copyright &copy; 2026 Alen Joby. All rights reserved. Precision Aviation ULD Tracking & Yard Control.</sub>
</div>
