# Motherboards, CPUs, and RAM (CompTIA A+ Core 1 — CIS 113)

## Motherboard Form Factors

The form factor decides the case, the power supply mounts, the number of expansion slots, and which standoff holes line up. A board only fits a case that supports its form factor or smaller.

- **ATX** — the full-size desktop standard, approximately 12 × 9.6 inches. Typically seven expansion slots. The reference point every other desktop size is compared to.
- **Micro-ATX (mATX)** — approximately 9.6 × 9.6 inches; fewer slots than ATX, fits ATX cases, the budget and mainstream default.
- **Mini-ITX** — approximately 6.7 × 6.7 inches; one expansion slot; small-form-factor and embedded builds. Power and cooling headroom are the trade-offs.
- **E-ATX and larger server/workstation sizes** — wider than ATX; exist for multi-socket and many-slot boards. Case support must be checked explicitly.

Exam habit: if a scenario says a board will not fit or a standoff is shorting the board, think form factor and standoffs first.

## Sockets, Chipsets, and Compatibility — at Concept Level

- **Socket** — the physical and electrical interface between CPU and board (for example, Intel LGA sockets where the pins live on the board, and AMD AM4/AM5 sockets). A CPU only works in its matching socket family, and often only with a supporting chipset and BIOS/UEFI version.
- **Chipset** — the board logic that brokers traffic between the CPU, RAM, storage, USB, and expansion. The chipset tier decides features such as overclocking support, number of USB and SATA ports, and PCIe lane splitting. Many modern functions (memory controller, much PCIe) live on the CPU itself; the chipset handles the rest of the I/O.
- **Compatibility rule for the exam and the bench:** match socket, then chipset, then RAM generation, then power delivery and cooling. Swapping any one of those without checking the others is how a build ends up not posting.
- **Firmware — BIOS and UEFI:** UEFI is the modern replacement for legacy BIOS: graphical setup, mouse support, Secure Boot, support for large boot drives via GPT. CMOS is the historical name for the settings store; today settings live in non-volatile firmware memory, kept by the board battery. A dead coin-cell battery classically shows up as a clock that will not stay set.

## CPU Ideas the Exam Actually Tests

- **Cores** — independent execution units on one package. More cores help parallel work (virtual machines, rendering, compiling); they do not automatically make a single-threaded task faster.
- **Threads and simultaneous multithreading** — Intel calls it Hyper-Threading, AMD calls it SMT. One physical core presenting two logical processors lets idle execution resources do useful work. It is not the same as doubling the cores.
- **Cache — L1, L2, L3** — small, fast memory on or near the CPU. L1 is smallest and fastest, split into instruction and data cache per core. L2 is larger, usually per-core. L3 is largest, usually shared across cores. Cache exists because even fast RAM is slow compared to the CPU.
- **Clock speed vs. instructions per cycle** — gigahertz alone does not compare CPUs across generations. Architecture decides how much work each cycle does.
- **Integrated graphics** — a GPU on the CPU package. CPUs without it require a discrete video card for display output; exam scenarios hide this in "new build, no display" questions.
- **Virtualization support** — hardware extensions (Intel VT-x, AMD-V; plus second-level address translation, EPT/NESTED paging) that let a hypervisor run guest operating systems efficiently. If a VM will not start or a hypervisor option is missing, check that virtualization is present on the CPU *and* enabled in UEFI setup.
- **64-bit vs. 32-bit** — a 64-bit CPU (x64) runs 64-bit and most 32-bit software; it is required to address more than about 4 GB of RAM usefully. ARM CPUs appear in thin laptops and tablets; the key exam point is that software is compiled per architecture — x64 programs do not run natively on ARM without emulation/translation.
- **Cooling vocabulary** — heat sink (passive metal), fan (active), thermal paste between CPU and cooler, liquid cooling for high heat loads, and thermal throttling: the CPU slowing itself down to survive heat. A machine that slows under load or shuts down under load is a cooling question until proven otherwise.

## RAM Generations — Desktop DIMMs, Stated Carefully

RAM generations are **not** interchangeable. Each generation has a different notch (keying) position on the module, so the wrong generation physically will not seat in the slot. Voltages below are the standard nominal voltages for mainstream desktop modules; low-voltage variants exist and are flagged.

| Generation | Desktop DIMM pins | Nominal voltage | Plain-words note |
|---|---|---|---|
| DDR3 | 240-pin | 1.5 V (DDR3L low-voltage variant: 1.35 V) | Older desktops and laptops; near end of life in new builds. |
| DDR4 | 288-pin | 1.2 V | The long-running mainstream standard. Different notch from DDR3 despite similar size. |
| DDR5 | 288-pin | 1.1 V | Newer mainstream. Same pin *count* as DDR4 but a different notch position and on-module power regulation — still not interchangeable with DDR4. |

Numbers here are the values A+ expects; treat clock speeds and transfer rates as approximate and board-dependent — the exam tests generation, voltage direction (newer = lower voltage, higher speed), and non-interchangeability more than exact data-rate tables.

- **DIMM vs. SO-DIMM** — DIMM is the desktop/long form; SO-DIMM is the short laptop form. Same generation logic, different physical size.
- **Speed naming** — a module marked DDR4-3200 runs a 3200 MT/s transfer rate; the PC4-25600 style label is the same speed expressed as bandwidth. Faster RAM in a slower board generally clocks down to what the board/CPU supports.

## Channels, Ranking, and ECC — in Plain Words

- **Single, dual, and quad channel** — the memory controller can use multiple pathways to RAM at once when modules are installed in matched banks. Dual-channel with a matched pair is the normal performance recommendation; the board manual's slot diagram decides which slots pair together (commonly slots 2 and 4 first on four-slot boards — always follow the manual, not habit).
- **Mixing modules** — mixed sizes can work but may fall back to single-channel for the unmatched portion (flex mode) or to the slowest module's speed. For exam answers: match size, speed, and timings; populate per the manual.
- **ECC vs. non-ECC** — ECC (error-correcting code) memory adds extra bits that detect and correct single-bit errors. It belongs in servers and workstations where silent corruption matters. ECC requires CPU, board, and module support together; most consumer boards use non-ECC. ECC and non-ECC are not a casual mix.
- **Registered vs. unbuffered** — server modules are often registered/buffered (a register chip helps electrical load with many modules). Registered and unbuffered modules do not mix. Consumer boards take unbuffered.
- **Parity** (historical note the exam still touches) — older error *detection* without correction; ECC is its successor concept.

## Troubleshooting Hooks for This Doc

No POST with new RAM: reseat, try one module, check the generation and slot population order. Random crashes and corrupted files under load: suspect RAM and run a memory diagnostic (MemTest86-style, or the Windows Memory Diagnostic in the OS doc of this pack). Beep codes and diagnostic LEDs vary by maker — there is no universal beep-code table, and any source that claims one is guessing.

Hands-on counterpart: for symptom-to-cause bench diagnostics that use this material, use the **navi-syskit** chip — it walks the same hardware through a diagnostic order.

## Quick Self-Check

1. DDR4 nominal voltage? 1.2 V. DDR5? 1.1 V.
2. Same pin count, DDR4 vs. DDR5 — interchangeable? No: notch position and power design differ.
3. The newest, largest, shared cache level? L3.
4. A hypervisor will not run and the CPU supports VT-x — what else? It must be enabled in UEFI setup.
5. Dual-channel needs what? Matched modules in the paired slots the manual names.
