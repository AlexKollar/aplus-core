# Storage and Power (CompTIA A+ Core 1 — CIS 113)

This is the NVMe doc. If you searched NVMe, start at the NVMe section below: NVMe is the protocol that lets flash storage talk over PCIe lanes instead of through the older disk-controller languages.

## The Three Storage Families

- **HDD — hard disk drive.** Magnetic platters, a spinning motor, and moving heads. Strengths: cheapest capacity, good for bulk and archives. Weaknesses: slowest, fragile while running, audible failure warnings (clicking, grinding, repeated spin-up attempts). Speeds are quoted in RPM (5,400 / 7,200 / 10,000+); latency comes from waiting for the platter and head.
- **SSD — solid-state drive (SATA).** NAND flash, no moving parts, in a 2.5-inch box speaking the SATA disk interface. Much faster than an HDD, but capped by the SATA link (SATA III is nominally 6 Gbps, roughly 550 MB/s in real sequential reads — approximate, controller-dependent).
- **NVMe SSD — flash speaking NVMe over PCIe.** NVMe (Non-Volatile Memory Express) is a protocol designed for flash, using the computer's PCIe lanes — the same high-speed pathways graphics cards use — instead of SATA. That is the whole NVMe advantage: NVMe removes the SATA bottleneck and the disk-era command overhead.

## NVMe in Plain Words — and NVMe vs. SATA

- **NVMe transport:** PCIe lanes. A typical consumer NVMe drive uses **four PCIe lanes (×4)**. Each PCIe generation roughly doubles per-lane bandwidth, so a Gen 3 ×4, Gen 4 ×4, and Gen 5 ×4 NVMe drive have very different ceilings even though the card looks similar. Treat headline sequential numbers as generation- and benchmark-dependent approximations; the exam concept is lanes × generation, not a memorized MB/s for every generation.
- **NVMe form factors:** the stick-like **M.2** card is the mainstream NVMe shape (2280 means 22 mm wide, 80 mm long). **U.2** and add-in PCIe cards exist in enterprise contexts. Critical trap: **M.2 is a form factor, not a protocol.** An M.2 slot can carry an NVMe (PCIe) drive, a SATA drive, or both — check the board manual. The key notch differs (NVMe M.2 is typically M-key; SATA M.2 is often B+M key) but the manual is the authority.
- **Why NVMe is faster beyond raw bandwidth:** NVMe supports many deep command queues in parallel, built for flash's parallel nature and modern multi-core CPUs. AHCI, the SATA-era host protocol, was designed around a single queue for spinning disks.
- **Exam sorting:** fastest / newest / PCIe lanes → NVMe. 2.5-inch box with a SATA cable → SATA SSD (or a laptop HDD — listen for spinning/clicking in the scenario). Cheapest bulk terabytes → HDD.
- **mSATA** (older small-card SATA) is legacy vocabulary the exam may still name; it is not NVMe.

## Storage Interfaces — the Vocabulary Set

- **SATA** — the disk-era serial interface for HDDs and SATA SSDs; data cable plus a separate power connector. SATA III 6 Gbps is the current desktop revision.
- **PCIe lanes** — scalable serial links: ×1, ×4, ×8, ×16 describe how many lanes a slot/device uses. NVMe drives and graphics cards are the two A+ consumers.
- **M.2** — the compact card connector (see NVMe above); also hosts some Wi-Fi cards.
- **External interfaces** — USB drives, and the legacy eSATA vocabulary. Optical drives (CD/DVD/Blu-ray) still appear in A+ scenarios: SATA-connected, treated as removable media.
- **SD and flash card formats** appear in mobile/camera contexts; know they are removable flash, not system storage families.

## RAID — Pointer Paragraph

RAID combines drives for speed, redundancy, or both: RAID 0 stripes with no redundancy (lose one drive, lose the array), RAID 1 mirrors, RAID 5 stripes with parity (tolerates one drive loss), RAID 10 mirrors stripes. That is the vocabulary level this pack carries. The depth — building, rebuilding, and administering arrays, especially on Windows Server — lives in the Windows Server / syskit material for this program, not here. Do not let an A+ question talk you into calling RAID a backup: RAID survives a drive failure; backup survives deletion, corruption, ransomware, and theft.

## PSUs — Wattage, Rails, and 80 PLUS

- **What a PSU does:** converts wall AC to the DC voltages the PC uses (mainly +12 V, +5 V, +3.3 V rails) and delivers them on standardized connectors.
- **Rails in plain words:** a rail is a supply line at one voltage. Modern CPUs and GPUs feed mostly from the **+12 V rail**, so a PSU's +12 V current capacity matters more than the headline number alone.
- **Wattage sizing:** add up the real load (CPU + GPU dominate), leave headroom for transients and future parts. Undersized supplies show up as shutdowns under load, not as polite errors. Oversizing wastes a little money; undersizing buys crashes.
- **80 PLUS** — an efficiency certification family (80 PLUS, Bronze, Silver, Gold, Platinum, Titanium, in rising efficiency). Higher tiers waste less power as heat, especially at typical partial loads. It is an efficiency rating, not a quality guarantee by itself.
- **Modular vs. non-modular** — modular supplies let you detach unused cables (cleaner airflow and builds); non-modular are cheaper. Semi-modular is the middle case.
- **Connector vocabulary:** 24-pin ATX main power; 4/8-pin CPU (EPS/ATX12V) power near the socket; 6/8-pin PCIe power for graphics cards; SATA power (flat, L-shaped) for drives; legacy Molex for old peripherals and fans. A missing 4/8-pin CPU power connector is a classic no-POST cause.

## Safe Power Handling

- The PSU holds charge after unplugging. **Do not open a power supply** — replace it as a unit.
- Unplug before servicing, then press the power button once to bleed residual charge. Work with anti-static precautions (see the operational procedures doc in this pack for ESD).
- AC input: many supplies auto-switch 110/220 V; older or cheaper units have a manual voltage selector — the wrong setting can destroy the supply.
- Power protection vocabulary: **surge protector** (absorbs spikes), **UPS / battery backup** (rides through outages and brownouts, gives time to shut down cleanly), **line conditioner** (smooths voltage). A surge strip is not a UPS.
- Redundant power supplies in servers: two units sharing load so one can fail (or be swapped hot) without downtime.

## Troubleshooting Hooks for This Doc

Clicking or grinding from the case: HDD dying — back up first, diagnose second. Drive missing in setup: check data *and* power cables, M.2 protocol vs. slot support for NVMe, and whether the slot shares lanes with a populated PCIe slot (a real board-manual behavior). Shutdowns only under gaming/render load: suspect PSU capacity or heat before software.

Hands-on counterpart: **navi-syskit** turns these storage and power facts into bench diagnostic order.

## Quick Self-Check

1. NVMe talks over what? PCIe lanes (typically ×4).
2. An M.2 drive is automatically NVMe? No — M.2 is the shape; the drive may be SATA.
3. SATA III ceiling, roughly? About 550 MB/s real sequential (6 Gbps link).
4. 80 PLUS measures what? Power conversion efficiency.
5. New GPU shuts the machine down under load — first hardware suspect? PSU capacity on the +12 V rail.
