# Windows Operating Systems (CompTIA A+ Core 2 — CIS 113)

This is the Windows doc — editions, installation, the admin consoles map, and the command line survival set. Windows Server depth lives in the CIS 158/258 material; this doc is client Windows at A+ depth.

## Windows Editions — Concept Level

- **Home** — the consumer edition: domain join is absent, BitLocker full management and Remote Desktop *hosting* are limited or absent, Group Policy Editor is not included. It exists so scenarios can say "this feature is not available on Home."
- **Pro** — the business workstation edition: domain join, Group Policy, BitLocker, Remote Desktop host, Hyper-V. The minimum serious answer for business features in exam scenarios.
- **Pro for Workstations** — Pro plus support for high-end hardware (more sockets/RAM) and workstation filesystems/features.
- **Enterprise / Education** — volume-licensing tiers adding the full security and management set (for example, broader AppLocker/credential protection and long-term update control). Education is Enterprise-shaped for schools.
- **Version vs. edition:** the version (Windows 10, Windows 11) sets the platform and requirements — Windows 11 requires TPM 2.0, Secure Boot-capable UEFI, and a supported CPU generation, which is why "old but working" PCs fail the upgrade check. The edition sets the feature ceiling.
- **32-bit vs. 64-bit:** 64-bit is the default and required to use more than about 4 GB of RAM; 32-bit survives only as legacy vocabulary and for ancient software/hardware.

## Install and Upgrade Paths

- **Clean install** — install onto a blank (or wiped) drive; no apps or settings carry over. The safest answer for a corrupted or malware-suspect machine.
- **In-place upgrade** — Setup runs from inside the existing OS and keeps files, apps, and settings while moving to a newer version/edition. Requires a supported upgrade path and a healthy starting system.
- **Repair install / in-place repair** — reinstalling the same version over itself to fix OS corruption while keeping apps and files.
- **Imaging and deployment vocabulary:** an image is a captured reference installation; deployment tools (Microsoft Deployment Toolkit / Windows Deployment Services lineage, and modern provisioning/Autopilot concepts) push images at scale. Partitioning vocabulary: MBR (legacy, 2 TB and four-primary-partition limits) vs. **GPT** (UEFI-era, large drives, many partitions), always paired: UEFI ↔ GPT, legacy BIOS ↔ MBR, with Secure Boot on the UEFI side.
- **Boot and recovery options:** Windows Recovery Environment (WinRE) — Startup Repair, System Restore (restore points), System Image Recovery, Command Prompt, Startup Settings (which leads to **Safe Mode** — minimal drivers/services for isolating a bad driver or app), and Reset This PC (refresh-style keep-files vs. full remove-everything). The boot order in UEFI setup decides whether USB/DVD recovery media even starts.

## Filesystems — Pointer Paragraph

NTFS is the Windows system filesystem: it adds per-file/folder permissions (ACLs), encryption (EFS), compression, journaling, quotas, and support for large files/volumes compared to FAT32 (4 GB single-file limit, no permissions) and exFAT (the flash-drive compromise: large files, minimal features). That paragraph is the A+ depth; permission mechanics and server shares are CIS 158/258 and syskit territory.

## The Admin Consoles Map — Which Tool Answers Which Question

A+ tests tool selection more than tool mastery. The map:

- **Task Manager** — live CPU/RAM/disk/network per process, startup programs tab, performance graphs. First stop for "the computer is slow right now."
- **Event Viewer** — Windows logs (System, Application, Security). Crashes, driver failures, service errors, and logon auditing live here. A scenario that says "find out *why* it crashed last night" is an Event Viewer answer.
- **Computer Management** — the umbrella console bundling several tools below.
- **Disk Management** — partitions and volumes: initialize disks (MBR/GPT), create/format volumes, drive letters, shrink/extend, disk health status words.
- **Device Manager** — driver state per device: disable/enable, update/roll back driver, warning icons, the answer to "this hardware stopped working after an update."
- **Task Scheduler** — jobs that run on triggers (time, logon, event).
- **Services (services.msc)** — background services: start/stop, startup type (Automatic / Automatic Delayed / Manual / Disabled), recovery actions. The **print spooler** lives here (restart it for stuck print queues).
- **Local Users and Groups / Computer Management users** — local accounts and group membership; domain accounts are managed on the domain side, not here.
- **Group Policy Editor (gpedit.msc)** — local policy settings (Pro+); domain Group Policy is the server-side counterpart that syskit covers.
- **Registry Editor (regedit)** — the configuration database: hives (HKLM, HKCU, HKCR, HKU, HKCC) and keys/values. Powerful and unforgiving: export/back up before editing; many exam scenarios about a "registry tweak" are really about that caution.
- **System Configuration (msconfig)** — boot options, Safe Boot toggles, and service/startup troubleshooting isolation.
- **System Information (msinfo32)** — the read-only inventory report: OS build, hardware, drivers, IRQ/resource summaries — also the file you *send* to support.
- **Resource Monitor / Performance Monitor** — deeper counters than Task Manager when "slow" needs evidence over time.
- **MMC** — Microsoft Management Console, the frame the snap-ins plug into; "build a custom console" is MMC vocabulary.
- **Settings vs. Control Panel** — modern Windows splits them; know that many classic applets (Programs and Features lineage, Internet Options, Mail) persist under Control Panel/search while Settings is the default surface. Either route to the right tool earns the exam point.

## Command-Line Survival Set

Each command with what it *proves* — the A+ way to learn them:

- **ipconfig** — the adapter's IP, mask, gateway, DNS (**/all** adds MAC and DHCP detail; **/release** and **/renew** cycle a DHCP lease; **/flushdns** clears the resolver cache). First network command, always.
- **ping** — reachability to an address, in order: loopback (127.0.0.1), own IP, gateway, remote host. The order *is* the diagnostic.
- **dir / cd / md / rd / del / copy / robocopy / xcopy** — directory listing and file management; robocopy is the robust bulk-copy tool (mirroring, retries, logging) — backup scripts in scenarios are robocopy.
- **chkdsk** — filesystem/disk error checking (**/r** hunts bad sectors and needs a reboot on the system drive).
- **sfc /scannow** — System File Checker: verifies protected OS files against known-good copies and repairs them — the first repair command for "Windows itself seems corrupted."
- **DISM** — services the Windows image itself; **DISM /Online /Cleanup-Image /RestoreHealth** repairs the component store SFC draws from. Order in a deep-corruption scenario: DISM first, then SFC again.
- **format / diskpart** — diskpart is the scriptable partitioning tool (list disk, select, clean, convert gpt/mbr) — destructive; double-check the selected disk number before any clean.
- **shutdown** — **/s** shutdown, **/r** restart, **/t** timer; remote shutdown vocabulary included.
- **gpupdate / gpresult** — force Group Policy refresh / report which policies actually applied (domain contexts).
- **winver** — the version/build dialog; **hostname**, **systeminfo** — quick identity and inventory.
- **net** family — **net use** (map drives/shares), **net user** (local account facts), **netstat** (live connections and listening ports — what is this machine talking to, and what is listening).
- **bootrec / bcdedit** (WinRE context) — boot configuration repair vocabulary for "Windows will not boot after a disk change."
- Safety rule the exam loves: **format, diskpart clean, and del are destructive; chkdsk /r and DISM are slow** — choose the least destructive command that answers the question.

## Accounts, Sign-in, and Everyday Security Hooks

Local account vs. Microsoft account vs. domain account — know which sign-in a scenario describes; UAC (User Account Control) prompts are the consent gate for admin actions, and disabling UAC is never the correct fix. Windows Hello (PIN/biometrics) is a sign-in method, not a password replacement in the domain sense.

Hands-on counterpart: **navi-syskit** carries the Windows Server administration side (AD, GPO order, shares) that builds on this client foundation.

## Quick Self-Check

1. Domain join on Windows Home? Not available — Pro or above.
2. Event Viewer answers what kind of question? What happened — logs of crashes, services, logons.
3. SFC finds corruption it cannot fix — next tool? DISM /RestoreHealth, then SFC again.
4. Stuck print queue — which service? The print spooler (in Services).
5. GPT pairs with which firmware? UEFI (with Secure Boot available).
