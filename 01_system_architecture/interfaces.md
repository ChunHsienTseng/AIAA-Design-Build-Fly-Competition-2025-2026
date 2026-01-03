# System Interfaces Definition

## Purpose
This document defines the **key system interfaces** between major aircraft
subsystems, with emphasis on electrical, mechanical, and control boundaries.

Clear interface definition ensures:
- Consistent integration between subsystems
- Reduced ambiguity during manufacturing and assembly
- Predictable behavior during ground and flight testing

This document complements the system block diagram located at:
`01_system_architecture/figures/system_block_diagram.png`

---

## System Overview
The aircraft is treated as an integrated system composed of the following
primary subsystems:

- Propulsion system
- Electrical power system
- Avionics and flight control system
- Airframe and landing gear
- Ground safety and arming system

Each subsystem interacts with others through well-defined interfaces
described below.

---

## Interface Summary Table

| Interface ID | Subsystem A | Subsystem B | Interface Type |
|-------------|------------|-------------|----------------|
| IF-01 | Propulsion Battery | ESC | Electrical (Power) |
| IF-02 | ESC | Motor | Electrical (Power) |
| IF-03 | Receiver Battery | Receiver | Electrical (Power) |
| IF-04 | Receiver | Servos | Electrical (Control & Power) |
| IF-05 | Receiver | ESC | Electrical (Control Signal) |
| IF-06 | Airframe | Landing Gear | Mechanical |
| IF-07 | Pilot | Arming / Safety Switch | Operational |

---

## Detailed Interface Definitions

### IF-01: Propulsion Battery → ESC
- **Type:** Electrical power
- **Voltage:** ~18.5 V nominal (5S)
- **Current:** Up to 100 A (fuse-limited)
- **Notes:**
  - Main propulsion power path
  - Routed through arming/safety device
  - Wiring and connectors must be rated for peak current

---

### IF-02: ESC → Motor
- **Type:** Electrical power (three-phase)
- **Voltage:** PWM-controlled three-phase output
- **Current:** Up to ESC rating
- **Notes:**
  - Phase order determines motor rotation direction
  - Cable length minimized to reduce losses and EMI

---

### IF-03: Receiver Battery → Receiver
- **Type:** Electrical power
- **Voltage:** 4.8–6.0 V (regulated or nominal)
- **Current:** Dependent on servo loading
- **Notes:**
  - Dedicated avionics power source
  - Independent from propulsion battery
  - Required for DBF compliance

---

### IF-04: Receiver → Servos
- **Type:** Electrical power + control signal
- **Signal:** PWM
- **Voltage:** Matches receiver battery output
- **Notes:**
  - Multiple servos may draw transient stall currents
  - Wiring must avoid voltage drop and brownout

---

### IF-05: Receiver → ESC
- **Type:** Control signal
- **Signal:** PWM throttle command
- **Voltage:** Signal-level only (no power transfer)
- **Notes:**
  - ESC BEC is disabled and not used
  - Throttle failsafe behavior must be configured

---

### IF-06: Airframe → Landing Gear
- **Type:** Mechanical
- **Loads:** Static ground load, dynamic takeoff/landing loads
- **Notes:**
  - Landing gear geometry constrains propeller clearance
  - Interface fixed by CAD design

---

### IF-07: Pilot → Arming / Safety Switch
- **Type:** Operational / Human interface
- **Function:** Enable or disable propulsion power
- **Notes:**
  - Required for safe ground handling
  - Must interrupt propulsion battery power path

---

## Interface Control Principles
The following principles apply to all interfaces:

- Electrical power and control paths are clearly separated
- Avionics and propulsion power systems remain independent
- Interfaces are documented before wiring or protection design
- Any interface change requires documentation update

---

## Relation to Downstream Design
This interface definition informs:
- Electrical wiring architecture
- Fuse and protection placement
- Assembly and pre-flight inspection procedures
- Test and validation planning

Subsequent documents include:
- `04_electrical_system/wiring_architecture.md`
- `04_electrical_system/protection_and_fusing.md`

---

## Conclusion
Clear definition of system interfaces establishes a stable foundation
for detailed electrical integration, manufacturing, and testing.

By freezing interfaces early, downstream design changes can be
controlled and evaluated systematically.

---

Ownership: Chun Hsien Tseng – system interface definition and integration planning
