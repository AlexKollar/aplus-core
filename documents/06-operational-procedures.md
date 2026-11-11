# Operational Procedures, Safety, and Troubleshooting Theory (CompTIA A+ Core 2 — CIS 113)

This is the ESD doc and the troubleshooting methodology doc. If you searched ESD, go to the Safety section: ESD is electrostatic discharge, and the controls are the wrist strap, the anti-static mat, equipotential grounding, and air/temperature discipline.

## The CompTIA Troubleshooting Methodology — In Order

The troubleshooting methodology is a fixed sequence on the A+ exam. The six steps, in order:

1. **Identify the problem.** Gather information, question the user, ask what changed, check logs and indicators, back up before making changes where appropriate, and note symptoms precisely.
2. **Establish a theory of probable cause.** Question the obvious first; consider multiple approaches (top-down, bottom-up, divide and conquer). Experience and documentation feed the theory — guessing randomly is not a theory.
3. **Test the theory to determine the cause.** Confirm or eliminate it with the smallest decisive test. If the theory is wrong, form a new one or escalate — do not keep changing parts.
4. **Establish a plan of action to resolve the problem and identify potential effects.** Know what the fix touches, what it might break, and what approval it needs *before* touching anything.
5. **Implement the solution or escalate as necessary.** Apply the fix (or hand it to the right level with notes), inside the agreed window.
6. **Verify full system functionality and, if applicable, implement preventive measures.** Test the whole system — not just the symptom — and add the prevention (update, cleaning, user guidance) that stops a repeat.
7. **Document the findings, actions, and outcomes.** (CompTIA counts this as the final step of the methodology — some listings fold it as the second half of step 6; on the exam, documentation is the last thing, never the first.)

Memory discipline: the order is the test. Backups belong in step 1 before changes, theory comes before testing, the plan comes before implementation, and documentation closes the job. Troubleshooting methodology questions punish skipping steps more than they punish wrong parts.

## Safety — ESD First, Then the Rest

### ESD — Electrostatic Discharge

- **What ESD is:** the sudden equalization of static charge between two objects at different potentials. A discharge a human cannot even feel (tens of volts) can damage or weaken a component rated for far less than the thousands of volts a felt shock involves. Damage can be immediate (dead board) or latent (the weakened part fails weeks later).
- **ESD controls — the working set:**
  - **Anti-static wrist strap** — bonds you to the same potential as the equipment (clip to the chassis/ground point), so charge never arcs through a component. Wear it for internal work; do not wear it when working inside a powered supply or on high-voltage parts (CRT-era and PSU safety rules override).
  - **Anti-static mat** — a grounded work surface that drains charge from parts and tools resting on it; the mat plus strap together is the standard bench answer.
  - **Equipotential bonding / same-potential rule** — when no strap exists, touch the chassis frequently and keep yourself and parts at the same potential; this is the honest field fallback, not an equal substitute.
  - **Anti-static bags** — parts travel and store in them (the metallized shielding kind protects; plain pink poly is only anti-static-ish handling material — exam scenarios favour the shielding bag for transport).
  - **Environment:** low humidity breeds static; moderate humidity, no carpet where avoidable, and ESD-safe handling habits (hold cards by edges, keep parts in bags until install).
- **ESD exam pattern:** any question asking how to protect a component *while installing it* wants the wrist strap and/or mat answer — ESD controls are procedural, not a device you install in the PC.

### Air Filters, Masks, and Physical Safety

- **Air filtration / respirator masks** — for dusty environments (construction dust, toner cleanup, attic/warehouse machines): protect lungs, use a toner-rated or HEPA approach for fine particles, never blow dust deeper into a machine with canned air held too close, and mind canned-air etiquette (upright, short bursts; the liquid propellant can frost a board).
- **Electrical safety:** PSUs and CRTs hold lethal charge — do not open them. Remove jewellery, respect the one-hand rule around live work (electrician practice that exams still cite), and treat a swollen lithium battery as a hazmat item, not a repair.
- **Heavy equipment and ergonomics:** rack gear is a two-person lift and a rack-rail job; the safety content is literal workplace safety.

## Environmental Controls — Concept Level

- **Temperature and humidity:** server and network rooms control both — heat kills hardware, humidity extremes invite ESD (too dry) or corrosion/condensation (too wet). Monitoring and alerting are part of the control, not paperwork.
- **UPS and clean power** (cross-reference the storage-and-power doc): battery backup and surge protection are environmental controls as much as equipment features.
- **Water, flooding, and detection:** sensors under raised floors and near pipes; never place the only copy of anything under plumbing.
- **Physical security ties in:** locked racks/rooms, access logs, camera coverage — operational procedure, not paranoia.

## Change Management Vocabulary

- **Change request / RFC** — the documented proposal: what, why, scope, risk, rollback.
- **Approval and the change advisory board (CAB)** — significant changes get reviewed and approved before the window, not during the outage.
- **Maintenance window** — the agreed low-impact time for the change.
- **Backout / rollback plan** — the rehearsed path back to the previous state if the change fails; a change with no backout plan is an exam wrong answer.
- **Documentation updates** — the change is not finished until diagrams, asset records, and procedures match reality. **Standard changes** (pre-approved, repeatable, low risk) vs. **emergency changes** (expedited, documented after) complete the vocabulary set.
- **Asset management** links here: inventory, tagging, warranty and lifecycle tracking are how an organization knows what it is changing.

## Documentation Habits and Professional Practice

- **Ticket discipline:** symptoms, steps taken, parts used, resolution, user verification. The next technician — often future you — reads this.
- **Knowledge base / known-good documentation:** network diagrams, labelling, standard operating procedures, and acceptable-use and password policies are operational documents, not bureaucracy.
- **Disposal and data destruction:** wiping (overwrite), degaussing (magnetic media), physical destruction (drilling, shredding, incineration), and certification of destruction. Follow organizational policy and environmental rules (e-waste, batteries, toner) — disposal is regulated, not a dumpster decision.
- **Regulated-data awareness at A+ level:** know the words PCI (cards), PII (personal information), PHI (health) and that incidents involving them escalate immediately under policy; the Security+ pack carries the depth.

## Troubleshooting Hooks for the Whole Program

Pair this methodology with the diagnostic chips: use **navi-syskit** for symptom-first hardware and Windows drills — its diagnostics follow this same order (identify, theory, test, plan, implement, verify, document), so the chip drills and the exam agree.

## Quick Self-Check

1. Troubleshooting methodology, step 2? Establish a theory of probable cause.
2. Documentation happens when? Last — after verification.
3. ESD protection while installing RAM? Wrist strap (and mat), bonded to the same potential.
4. A change has no rollback plan — exam verdict? Not ready; the backout plan is mandatory thinking.
5. Humidity very low — which risk rises? ESD.
