# System Interfaces Definition

## Purpose
This document defines the **key system interfaces** between major aircraft
subsystems, with emphasis on electrical, mechanical, control, and operational
boundaries.

Clear interface definition ensures:
- Consistent integration between subsystems
- Reduced ambiguity during manufacturing and assembly
- Predictable behavior during ground and flight testing
- Alignment between system architecture, wiring, and safety procedures

This document complements the system block diagram located at:
`01_system_architecture/figures/system_block_diagram_01003.jpg`

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
| IF-01 | Propulsion Battery | XT90S Arming Plug | Electrical (Power) |
| IF-02 | XT90S Arming Plug | ESC | Electrical (Power) |
| IF-03 | ESC | Motor | Electrical (Power) |
| IF-04 | Receiver Battery | Receiver | Electrical (Power) |
| IF-05 | Receiver | Servos | Electrical (Control & Power) |
| IF-06 | Receiver | ESC | Electrical (Control Signal) |
| IF-07 | Airframe | Landing Gear | Mechanical |
| IF-08 | Pilot | XT90S Arming Plug | Operational / Safety |

---

## Detailed Interface Definitions

### IF-01: Propulsion Battery → XT90S Arming Plug
- **Type:** Electrical power
- **Voltage:** ~18.5 V nominal (5S)
- **Current:** Up to DBF propulsion current limit
- **Notes:**
  - Main propulsion power feed
  - Routed through main fuse
  - Fixed wiring; not routinely disconnected
  - Connectors and wiring rated for peak current and thermal margin

---

### IF-02: XT90S Arming Plug → ESC
- **Type:** Electrical power
- **Voltage:** ~18.5 V nominal (5S)
- **Current:** Up to DBF propulsion current limit
- **Notes:**
  - Primary physical arming/disarming interface
  - Removable jumper provides visible safety state
  - Anti-spark feature reduces connector wear and inrush stress

---

### IF-03: ESC → Motor
- **Type:** Electrical power (three-phase)
- **Voltage:** PWM-controlled three-phase output
- **Current:** Up to ESC rating
- **Notes:**
  - Phase order determines motor rotation direction
  - Cable length minimized to reduce losses and EMI

---

### IF-04: Receiver Battery → Receiver
- **Type:** Electrical power
- **Voltage:** 4.8–6.0 V (nominal or regulated)
- **Current:** Dependent on servo loading
- **Notes:**
  - Dedicated avionics power source
  - Independent from propulsion battery
  - Required for DBF compliance and control reliability

---

### IF-05: Receiver → Servos
- **Type:** Electrical power and control
- **Signal:** PWM
- **Voltage:** Matches receiver battery output
- **Notes:**
  - Multiple servos may draw transient stall currents
  - Wiring must minimize voltage drop to prevent brownout

---

### IF-06: Receiver → ESC
- **Type:** Control signal
- **Signal:** PWM throttle command
- **Voltage:** Signal-level only (no power transfer)
- **Notes:**
  - ESC internal BEC is disabled and not used
  - Throttle failsafe behavior must be configured and verified

---

### IF-07: Airframe → Landing Gear
- **Type:** Mechanical
- **Loads:** Static ground load, dynamic takeoff and landing loads
- **Notes:**
  - Landing gear geometry constrains propeller clearance
  - Interface fixed by CAD design

---

### IF-08: Pilot → XT90S Arming Plug
- **Type:** Operational / Human interface
- **Function:** Physically arm or disarm propulsion system
- **Notes:**
  - Plug insertion arms propulsion power
  - Plug removal guarantees motor cannot rotate
  - Used during ground handling, testing, and inspection

---

## Interface Control Principles
The following principles apply to all interfaces:

- Electrical power and control paths are clearly separated
- Propulsion and avionics power systems remain independent
- Safety-critical interfaces are physically inspectable
- Interfaces are documented and frozen prior to detailed wiring and protection design
- Any interface change requires documentation update

---

## Relation to Downstream Design
This interface definition informs:
- Electrical wiring architecture
- Protection and fusing strategy
- Assembly and ground safety procedures
- Bench and flight test planning

Related documents include:
- `04_electrical_system/wiring_architecture.md`
- `04_electrical_system/protection_and_fusing.md`

---

## Conclusion
Clear definition of system interfaces establishes a stable foundation
for detailed electrical integration, manufacturing, and validation.

By freezing interfaces at the concept stage, downstream design changes
can be evaluated systematically and safely.

---

Ownership: Chun Hsien Tseng – system interface definition and integration planning
