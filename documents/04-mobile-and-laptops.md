# Mobile Devices and Laptops (CompTIA A+ Core 1 — CIS 113)

## Laptop Anatomy vs. Desktop — What's Soldered, What's Serviceable

The laptop design rule: everything is traded for thin, light, and battery life. Compared to a desktop of the same era, a laptop more often has parts integrated or soldered to the main board.

- **Typically serviceable (varies by model — always check the service manual):** storage (M.2 or 2.5-inch), sometimes RAM (one or two SO-DIMM slots), the battery (increasingly internal but usually replaceable with disassembly), Wi-Fi card (M.2), keyboard, fans, and the screen assembly.
- **Typically soldered / not upgradeable on modern thin laptops:** RAM soldered directly to the board (common on ultra-thin models and all Apple-silicon machines), CPU soldered (BGA) on essentially all modern laptops, GPU integrated or soldered.
- **Exam consequence:** "upgrade the RAM" scenarios only work when the machine has SO-DIMM slots and free capacity. Soldered RAM cannot be upgraded after purchase — buy the capacity up front.
- **Desktop contrast:** desktops keep CPU socketed, RAM slotted, storage and GPU swappable. That serviceability gap is the conceptual heart of this topic.
- **Form vocabulary:** convertible / 2-in-1 (screen folds or detaches), tablet mode, docking station vs. port replicator (a dock may add video, power, and expansion; a replicator mainly multiplies ports), and the laptop security cable slot.

## Displays on Laptops — Including Legacy Inverter Notes

- **Panels:** laptops use the same LCD families as the display doc (IPS is now common; TN survives in budget models) plus OLED on premium models.
- **Inverter — legacy but still examined:** older CCFL-backlit laptop screens needed an **inverter board** to convert the laptop's DC power to the high-voltage AC a cold-cathode fluorescent lamp requires. Symptoms of a dying inverter/backlight: a very dim screen where the image is faintly visible under a flashlight, flickering, or a screen that lights briefly then goes dark while the machine keeps running. LED-backlit screens (the modern default) do not use an inverter — a dim LED screen points at the backlight, its driver, or the panel itself. A+ still asks the inverter question for the CCFL generation; answer it in that generation's terms.
- **Other laptop display parts:** the digitizer on touch models (touch fails while the image is fine = digitizer or its cable), the webcam and microphone in the bezel, Wi-Fi antennas routed around the screen frame (a screen replacement that kills Wi-Fi usually pinched or forgot the antenna leads), and the lid close sensor/switch.
- **External display behaviour:** Fn-key or OS display modes — duplicate, extend, second-screen-only. A user "with a broken screen" on external display often just has the wrong mode selected.

## Batteries and Battery Care

- **Chemistry:** lithium-ion (Li-ion) dominates; lithium-polymer (Li-Po) is its pouch-cell variant in thin devices. Neither has the old nickel "memory effect" — partial charges are fine.
- **Care facts that matter in support:** heat is the main lifespan enemy; deep storage at 0% or 100% for months ages a battery; swelling is a stop-and-replace condition — a swollen battery can lift a trackpad, crack a case, and is a fire risk. Never puncture a lithium battery.
- **Symptoms and vocabulary:** rapid discharge / poor calibration (OS gauge lying), swelling, a device that only runs on AC, charging-port wear (loose USB-C, damaged barrel jack or its solder joints). Battery health percentages in OS/firmware are estimates — treat them as approximate.
- **Replaceability trend:** sealed internal batteries are the industry direction; "user-replaceable battery" is now a feature to verify, not assume. Phones and tablets: battery replacement is a repair-shop job involving adhesives and heat.

## Mobile Operating Systems and Admin Basics

- **The two families:** Android (Google; open-source core with vendor skins; Google Play as the default store) and iOS/iPadOS (Apple only; App Store as the only default store). Updates, backups, and account ties (Google account / Apple ID) are the daily support surface.
- **MDM at concept level:** Mobile Device Management lets an organization enrol devices, push configuration and apps, enforce passcode/encryption policy, locate, lock, and remotely wipe — especially lost/stolen devices. **MAM** (mobile application management) manages the apps/data instead of the whole device, the BYOD-friendly variant. **BYOD, CYOD, COPE, COBO** are the ownership models the exam names: personal-owned, company-chosen, company-owned-personally-enabled, company-owned-business-only, in that order of control.
- **Support vocabulary:** screen calibration and autorotation locks, tethering/hotspot, airplane mode radios (cellular, Wi-Fi, Bluetooth, NFC, GPS as separate radios), VPN on mobile, two-factor authenticator apps, and factory reset as the last resort *after* backup verification.
- **Synchronization:** accounts sync mail, contacts, calendars, and photos to cloud services; "contacts vanished" is usually a sync/account problem, not device data loss.

## Mobile Accessories, Ports, and Wireless Vocabulary

- **Ports:** USB-C is the converging mobile standard (and now the iPhone standard as well); Lightning was Apple's prior plug; Micro-USB is legacy Android/accessory. Wireless charging (Qi family) avoids the port entirely — heat and alignment are its limits.
- **Radios and short-range tech:** NFC (tap-to-pay and pairing, centimetre range), Bluetooth (pairing, profiles, tethering), hotspot/tethering over Wi-Fi or USB, and casting/mirroring to displays.
- **Location services:** GPS plus Wi-Fi/cell triangulation; accuracy and battery trade-offs.

## Laptop and Mobile Troubleshooting Hooks

- Overheating laptop: clogged vents/fans, failed fan, dried thermal paste — same cooling story as desktops, smaller passages. Confirm fan spin before software theories.
- No charge: try the adapter on the right wattage (an undersized USB-C charger may maintain but not charge under load), inspect the port, then the battery.
- Sticky/spilled keyboard, cracked screen, dead Wi-Fi after repair: physical-service answers, see antennas note above.
- Device security basics for support: screen lock, biometric unlock (fingerprint/face — convenience tied to a PIN fallback), failed-attempt wipe policies, locate/wipe through the platform account or MDM.

Hands-on counterpart: **navi-syskit** includes laptop symptoms in its diagnostic drills.

## Quick Self-Check

1. Faint image visible only with a flashlight on an old CCFL laptop — suspect what? Inverter/backlight.
2. Soldered RAM can be upgraded later — true or false? False.
3. A swollen battery is safe to keep using if it still charges? No — replace it, fire risk.
4. Company wipes only the work apps on a personal phone — MDM or MAM? MAM.
5. Wi-Fi died right after a screen swap — likely cause? Pinched/disconnected antenna leads in the lid.
