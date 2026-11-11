# Glossary and Acronyms (CompTIA A+ — CIS 113)

Quick-lookup expansions for the acronyms A+ students search mid-study. NVMe is Non-Volatile Memory Express; ESD is electrostatic discharge; PSU is power supply unit; DIMM is dual inline memory module; UEFI is Unified Extensible Firmware Interface; MDM is mobile device management; RAID is redundant array of independent disks; UPS is uninterruptible power supply. Each entry below gives the expansion plus a one-line meaning — the retrieval-friendly form for revision.

## Hardware and Firmware

- **ATX** — Advanced Technology Extended — the standard full-size desktop motherboard form factor.
- **BIOS** — Basic Input/Output System — legacy PC firmware; succeeded by UEFI.
- **UEFI** — Unified Extensible Firmware Interface — modern firmware with Secure Boot and GPT boot support.
- **CMOS** — complementary metal-oxide semiconductor — historically the firmware settings memory; the term survives for the settings/battery.
- **POST** — power-on self-test — the firmware's hardware check at startup; failures surface as beeps, LEDs, or codes.
- **CPU** — central processing unit — the main processor.
- **GPU** — graphics processing unit — renders display output; integrated or discrete.
- **SMT / Hyper-Threading** — simultaneous multithreading — one core presenting two logical processors.
- **RAM** — random-access memory — volatile working memory; contents vanish at power-off.
- **DIMM** — dual inline memory module — the desktop RAM stick form.
- **SO-DIMM** — small outline DIMM — the laptop RAM stick form.
- **DDR** — double data rate — the RAM family prefix (DDR3/DDR4/DDR5 generations).
- **ECC** — error-correcting code — memory that detects and corrects single-bit errors; server/workstation territory.
- **TPM** — Trusted Platform Module — the hardware crypto chip Windows 11 requires (version 2.0) for key protection and measured boot.

## Storage and Power

- **HDD** — hard disk drive — spinning magnetic storage.
- **SSD** — solid-state drive — flash storage with no moving parts.
- **NVMe** — Non-Volatile Memory Express — the flash protocol that runs over PCIe lanes; the fastest mainstream storage interface.
- **SATA** — Serial ATA — the disk-era interface for HDDs and SATA SSDs.
- **PCIe** — Peripheral Component Interconnect Express — the lane-based expansion/storage bus (×1/×4/×8/×16).
- **AHCI** — Advanced Host Controller Interface — the SATA host protocol NVMe replaced for flash.
- **RAID** — redundant array of independent disks — combining drives for speed and/or redundancy; not a backup.
- **SMART** — Self-Monitoring, Analysis, and Reporting Technology — drive health self-reporting; warnings precede many failures.
- **PSU** — power supply unit — converts AC to the DC rails a PC uses.
- **UPS** — uninterruptible power supply — battery backup that rides through outages.
- **ESD** — electrostatic discharge — static equalization that can silently damage components; see also the safety doc.

## Display, Printing, and Peripherals

- **LCD** — liquid-crystal display — the panel family behind TN/IPS/VA monitors, lit by a backlight.
- **IPS** — in-plane switching — LCD type with the best colour and viewing angles.
- **VA** — vertical alignment — LCD type known for deep contrast.
- **TN** — twisted nematic — oldest LCD type; fast and cheap, poor angles.
- **OLED** — organic light-emitting diode — per-pixel light; perfect blacks, burn-in risk.
- **HDMI** — High-Definition Multimedia Interface — video-plus-audio cable standard.
- **DP** — DisplayPort — PC-first display connector with daisy-chaining support.
- **MST** — Multi-Stream Transport — DisplayPort daisy-chaining of monitors.
- **MFP** — multifunction printer — print/scan/copy/fax in one device.
- **ADF** — automatic document feeder — feeds multi-page scans/copies hands-free.
- **PCL** — Printer Command Language — HP's page description language.
- **DPI** — dots per inch — print/scan resolution measure.

## Mobile and Wireless

- **MDM** — mobile device management — enrol, configure, enforce policy, and wipe devices centrally.
- **MAM** — mobile application management — manages work apps/data without owning the whole device.
- **BYOD** — bring your own device — personal hardware used for work.
- **COPE** — corporate-owned, personally enabled — company device with permitted personal use.
- **NFC** — near-field communication — centimetre-range tap technology (payments, pairing).
- **GPS** — Global Positioning System — satellite location.
- **Li-ion / Li-Po** — lithium-ion / lithium-polymer — the dominant rechargeable battery chemistries.
- **IMEI** — International Mobile Equipment Identity — a mobile device's hardware identifier on cellular networks.
- **SIM / eSIM** — subscriber identity module — physical card or embedded profile tying device to carrier account.

## Windows and Operations

- **UAC** — User Account Control — the admin-consent prompt in Windows.
- **WinRE** — Windows Recovery Environment — the built-in repair environment (Safe Mode access, Startup Repair, System Restore).
- **SFC** — System File Checker — verifies and repairs protected Windows files (`sfc /scannow`).
- **DISM** — Deployment Image Servicing and Management — repairs the component store SFC relies on.
- **MMC** — Microsoft Management Console — the frame hosting admin snap-ins.
- **RDP** — Remote Desktop Protocol — Windows remote control (host side requires Pro or above).
- **NTFS** — NT File System — Windows' permission-capable system filesystem.
- **FAT32 / exFAT** — older / flash-friendly filesystems — FAT32 caps a single file at 4 GB; exFAT lifts that with fewer features than NTFS.
- **MBR / GPT** — master boot record / GUID Partition Table — legacy vs. UEFI-era disk partitioning schemes.
- **CAB** — change advisory board — approves significant changes.
- **RFC (change context)** — request for change — the documented change proposal (not to be confused with internet RFCs).
- **PII** — personally identifiable information — data identifying a person; handle under policy.
- **EULA / SLA** — end-user licence agreement / service-level agreement — licence terms / measurable service commitments.

## One-Line Concept Glossary (Non-Acronym Essentials)

- **Backout plan** — the rehearsed way to undo a change that fails; mandatory thinking in change management.
- **Digitizer** — the touch-sensing layer over a display; picture fine + touch dead = digitizer.
- **Inverter** — legacy laptop board powering a CCFL backlight from DC; dim-but-visible screen on old laptops.
- **Maintenance kit** — a laser printer's scheduled wear-parts bundle (fuser, rollers, pads).
- **Secure Boot** — UEFI feature admitting only signed boot components.
- **Spooler** — the Windows print queue service; restart it for stuck print jobs.
- **Standoff** — the brass spacer isolating a motherboard from the case tray; missing/extra standoffs cause shorts.
- **Thermal paste** — the interface material between CPU and cooler; dried paste causes heat problems.
- **Wrist strap** — the ESD control bonding the technician to the equipment's potential.

Cross-reference: hands-on diagnostics for most terms above live in the **navi-syskit** chip; networking terms (subnetting, ports) live in navi-netkit and the Networking Core pack.
