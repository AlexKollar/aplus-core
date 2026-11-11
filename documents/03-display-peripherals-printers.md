# Displays, Peripherals, and Printers (CompTIA A+ Core 1 — CIS 113)

## Display Panel Technologies — Honest Comparison

- **TN (Twisted Nematic)** — the oldest mainstream LCD panel type. Strengths: cheapest, fastest response historically. Weaknesses: poor viewing angles and weaker colour. Now mostly budget panels.
- **IPS (In-Plane Switching)** — best colour accuracy and viewing angles of the classic LCD family; the default recommendation for photo/design work and shared viewing. Slightly higher cost; contrast is good but not the deepest.
- **VA (Vertical Alignment)** — the middle path: deep blacks and high contrast (movie-friendly), viewing angles and response between TN and IPS, with some dark-scene smearing on cheaper panels.
- **OLED** — each pixel makes its own light: perfect blacks, excellent contrast and response. Watch for burn-in risk with static content and higher cost. Increasingly common in laptops and phones.
- **LCD backlight vocabulary** — most LCDs are lit by an LED backlight behind the panel ("LED monitor" means LED-backlit LCD, not a different panel science). A dim wash, dark edges, or a dead backlight (image faintly visible with a flashlight) is a backlight/inverter-era symptom — see the mobile doc for inverters.
- **Specs the exam names:** resolution (pixels; native resolution is the sharp one), refresh rate in Hz (60 Hz office standard; higher for gaming), brightness in nits/cd·m², contrast ratio, response time in ms. Projectors add throw distance and lumens, and lamp life.

Touchscreens use a **digitizer** layer over the display; a screen that shows a picture but ignores touch has a digitizer/input problem, not a panel problem.

## Cable and Connector Zoo — Concept Level

- **HDMI** — the living-room and office default: video plus audio in one cable, on monitors, TVs, laptops, and consoles. Versions raise bandwidth (resolution/refresh ceilings); cables are largely interchangeable for ordinary office resolutions.
- **DisplayPort (DP)** — the PC-monitor-first connector: highest mainstream bandwidths, daisy-chaining (MST) on supporting monitors, and a locking latch on full-size plugs. Mini-DP shares the signal.
- **USB-C / Thunderbolt** — USB-C is the plug shape; Thunderbolt is a capability riding that plug (Intel/Apple lineage, now folded into USB4 thinking). A USB-C port may carry data only, data plus charging, or data plus display (DisplayPort Alt Mode) plus Thunderbolt — the port's logos and the device spec decide. "USB-C cable fits but no display" is an Alt Mode / capability question, not a broken-cable question first.
- **VGA (legacy)** — analogue, blue 15-pin; no audio; softer image. Still tested because it still exists on old projectors. **DVI (legacy)** — digital/analogue bridge era; no audio on most variants. **Component/composite/S-Video** are older video vocabulary, recognize-and-move-on level.
- **Peripheral connectors:** USB-A (rectangular, the classic), USB-B (printer/scanner square-ish plug — still the printer back-panel default), Micro-USB (older phones/accessories), Lightning (Apple's earlier mobile plug), and USB-C as the converging standard. USB versions (2.0/3.x) are about speed, not plug shape alone — shape and version are separate axes and exam questions mix them deliberately.
- **Audio:** 3.5 mm analogue jacks, optical (TOSLINK) digital, HDMI/DP carrying audio.
- **Adapters convert plugs, not capability** — a passive adapter cannot invent a signal the source does not emit. Direction matters on many display adapters.

## Printer Families — Vocabulary Level with Honest Trade-offs

- **Laser** — toner (dry powder) fused to paper with heat. Fast, cheap per page, sharp text. The office workhorse. Uses the multi-step process detailed below.
- **Inkjet** — liquid ink sprayed through nozzles. Cheap hardware, good photos, higher per-page cost; heads clog when idle for long stretches.
- **Thermal** — heat on treated paper (receipts, labels) or via ribbon (some label printers). No ink/toner to replace; special paper fades with heat/time.
- **Impact (dot matrix)** — pins strike an inked ribbon. Loud, low quality, and still alive because it prints through **multipart/carbon forms** nothing else can.
- **3D printers** (objective vocabulary) — filament (FDM) and resin (SLA-family) printing; know the words, the heated bed/extruder, and basic safety (heat, resin handling, ventilation).
- **Shared vocabulary:** duplex (two-sided), ADF (automatic document feeder on scanners/MFPs), MFP (multifunction printer), PCL and PostScript (page description languages — the printer's instruction languages), print spooler (the OS service that queues jobs; restarting it clears many stuck-queue scenarios), and TCP/IP vs. USB vs. shared-printer connectivity.

## The Laser Printing Process — In Order

The laser printing process order is an exam favourite because it is a sequence. The seven steps, in order:

1. **Processing** — the printer's formatter receives the job and rasterizes it into a page image (this is where RAM and the page language matter).
2. **Charging** — a primary corona wire or charge roller gives the imaging drum a uniform negative charge.
3. **Exposing** — a laser (or LED array) writes the page image onto the drum, discharging the charge where toner should land, leaving a latent image.
4. **Developing** — toner is attracted to the discharged areas of the drum; the image becomes visible toner on the drum.
5. **Transferring** — a transfer roller/corona gives the paper an opposite charge, pulling the toner image from drum to paper.
6. **Fusing** — heat and pressure rollers melt the toner into the page permanently. This is why laser output comes out warm.
7. **Cleaning** — a blade and discharge lamp clear leftover toner and charge from the drum so the next page starts clean.

Memory hook for the laser printing process order: **P**lease **C**an **E**very **D**og **T**alk **F**unny **C**onstantly — Processing, Charging, Exposing, Developing, Transferring, Fusing, Cleaning. Failures map to steps: ghost images point at cleaning/drum, blank pages at exposing/transfer, smearing that rubs off at fusing, and a solid black page at charging.

## Printer Maintenance Vocabulary

- **Maintenance kit** (laser) — the scheduled bundle of wear parts: fuser, transfer roller, pickup/separation rollers and pads. "Perform printer maintenance" prompts and errors at page-count intervals mean install the kit, then reset the counter.
- **Calibration** — aligning colour/registration so layers and colours land where they should (both inkjet alignment and laser colour calibration).
- **Cleaning cycles** — inkjets run head-cleaning cycles that consume ink to unclog nozzles; paper-path cleaning and roller cleaning fix pickup and jamming problems across families.
- **Consumables honesty:** toner cartridges, ink cartridges/tanks, thermal paper, impact ribbons, and 3D filament/resin. OEM vs. third-party is a cost/quality/warranty conversation, not an exam absolute.
- **Safety with lasers (printers):** the fuser is hot, toner is a fine powder (use a toner-rated vacuum, not compressed air indoors), and the drum is light-sensitive — do not leave it sitting in bright light.

## Troubleshooting Hooks

No display on a known-good monitor: cable, input selection, then source port capability (see USB-C Alt Mode above). Garbled or memory-overflow printer errors: the processing step is starved — lower resolution or add printer RAM context in scenario terms. Repeated jams at one spot: read the jam location as a map — pickup, path, fuser, exit.

Hands-on counterpart: **navi-syskit** carries printer and display symptoms in its diagnostic tables.

## Quick Self-Check

1. Laser process, third step? Exposing.
2. Toner rubbing off the page points at which step? Fusing.
3. Best colour/viewing angles, classic LCD? IPS.
4. USB-C fits, charges, but no picture — think what? DisplayPort Alt Mode capability of the port/cable.
5. Multipart invoice forms require which family? Impact.
