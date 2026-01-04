# Electrical System BOM (Design-Level Summary)

## Purpose
This document provides a **design-level Bill of Materials (BOM)**
for the electrical system.

The intent is to:
- Capture key component selections and rationale
- Track which items are fixed vs TBD
- Maintain traceability between design decisions and hardware

This is **not a final procurement list**.

---

## Propulsion Power System

| Item | Status | Notes / Rationale |
|----|----|----|
| Propulsion Battery (5S) | Selected | ≤100 Wh architecture with compliance margin |
| Main Fuse | TBD | Rating to be finalized after bench current testing |
| Fuse Holder (M8 terminals) | Selected | Supports high-current secure connections |
| XT90S Arming Plug (jumper) | Selected | Primary propulsion arming/disarming device |
| XT90 / XT90S Fixed Connectors | Selected | Rated for high current with margin |
| 8 AWG High-Current Wiring | Selected | Thermal margin for propulsion loop |
| ESC | Selected | Rated above expected continuous and peak current |
| Motor | Selected | Matched to 16–17″ prop envelope |

---

## Avionics / Control Power System

| Item | Status | Notes / Rationale |
|----|----|----|
| Receiver Battery | TBD | Chemistry and capacity to be finalized |
| Receiver Power Switch | Selected | Operational control of avionics power |
| Receiver | Selected | Compatible with servo and voltage requirements |
| Servos | Selected | Quantity and torque defined by airframe |
| Servo Extension Leads | TBD | Required depending on airframe layout |

---

## Wiring and Protection Accessories

| Item | Status | Notes / Rationale |
|----|----|----|
| Heat Shrink Tubing | TBD | Strain relief and insulation |
| Ferrite Beads | Optional | EMI mitigation if required by testing |
| Cable Ties / Mounts | TBD | Harness routing and vibration control |
| Labeling / Marking | TBD | Inspection clarity and maintenance |

---

## Instrumentation (Test Phase)

| Item | Status | Notes / Rationale |
|----|----|----|
| DC Current Meter / Clamp | Selected | Required for bench current measurement |
| IR Thermometer | Selected | Thermal monitoring during tests |
| RPM Tachometer | Optional | Performance characterization |
| Thrust Measurement | Optional | Static thrust comparison only |

---

## Notes
- Items marked **TBD** will be finalized after bench testing and integration
- Any change to selected items requires documentation update
- Final procurement list will be derived from this document

---

Ownership: Chun Hsien Tseng – electrical BOM definition and traceability
