# Electrical Wiring Architecture (V0.1 – Concept Design)

## Purpose
This document defines the **electrical wiring architecture and design principles**
for the aircraft at the conceptual design stage.

The objective is to:
- Establish clear separation between propulsion and avionics power paths
- Define wiring topology, routing principles, and interface boundaries
- Identify electrical noise and reliability risks early
- Provide a stable framework for detailed wiring and protection design

This document reflects the current system architecture, where propulsion arming
is implemented via a **removable XT90S anti-spark arming plug**, rather than a
dedicated power switch.

---

## Architectural Overview

The electrical system consists of **two fully independent wiring architectures**:

1. **Propulsion Power Wiring**
   - High-current, high-noise power delivery
   - Physical arming/disarming via XT90S arming plug

2. **Avionics / Control Wiring**
   - Independent receiver battery
   - Safety-critical low-voltage control power

This separation is mandatory for DBF compliance and system reliability.

(Reference system block diagram:
`01_system_architecture/figures/system_block_diagram.png`)

---

## Propulsion Power Wiring Architecture

### Power Path
Propulsion battery → Main fuse → **XT90S arming plug (removable)** → ESC → Motor

### Key Characteristics
- High current (up to DBF limit)
- Rapid current transients during throttle changes
- Significant electromagnetic interference (EMI) potential

### Design Principles
- Minimize total wire length in the high-current loop
- Use fixed, strain-relieved wiring for all non-removable connections
- Concentrate routine connect/disconnect actions at the XT90S arming plug
- Physically separate propulsion wiring from avionics wiring

---

## XT90S Arming Plug Implementation

### Function
The XT90S arming plug serves as the **primary propulsion arming and disarming
mechanism**.

- **Plug inserted:** propulsion system armed; motor can rotate
- **Plug removed:** propulsion system disarmed; motor physically cannot rotate

### Design Intent
- The XT90S arming plug is externally accessible
- Anti-spark feature reduces connector wear and inrush current stress
- Plug removal provides a clear, visible safety state during ground handling

The arming plug replaces the need for a dedicated propulsion power switch.

---

## Avionics / Control Wiring Architecture  
### (Separate Receiver Battery – DBF Compliant)

### Power Path
Receiver battery → Receiver power switch → Receiver → Servos

### Key Characteristics
- Low voltage (≈5–6 V)
- Lower average current but high transient servo stall currents
- Safety-critical; brownout is unacceptable

### Design Principles
- Fully independent from propulsion power wiring
- Short, low-resistance paths from receiver battery to receiver
- Avoid daisy-chaining high-load servos through thin or extended leads

---

## Control Signal Wiring

### Receiver → ESC
- PWM throttle signal only
- No power transfer from ESC to receiver
- ESC internal BEC is disabled and not used

### Routing Principles
- Route control signal wiring away from high-current propulsion wiring
- Cross high-current wires at approximately 90° if unavoidable
- Avoid long parallel runs with motor phase wires

---

## Grounding and Return Path Considerations

### Philosophy
- No shared power return between propulsion and avionics systems
- Each system maintains its own closed current loop
- Signal grounds remain local to their respective power systems

This minimizes ground bounce and EMI coupling into control signals.

---

## EMI and Noise Mitigation

Mitigation strategies include:
- Short ESC-to-motor phase wiring
- Physical separation between power and signal wiring
- Twisting motor phase wires when possible
- Optional ferrite beads on servo leads if bench testing indicates sensitivity

---

## Connector and Interface Standardization (Preliminary)

- High-current connectors rated with thermal margin above expected load
- XT90S connectors used for propulsion arming interface
- Control connectors selected for vibration resistance and retention

Specific connector part numbers and wire gauges remain **TBD** pending procurement
and bench test results.

---

## Assembly and Inspection Considerations

- XT90S arming plug must be clearly visible and accessible
- Propulsion and avionics wiring must be visually distinguishable
- Chafing protection required at all structure pass-through points
- Wiring routes must be inspectable without disassembly

---

## TBD Items
- Final wire gauge selection
- Connector part numbers
- Harness lengths and routing details
- Fuse rating confirmation based on bench testing

---

## Conclusion
This wiring architecture establishes a clear, DBF-compliant separation between
propulsion and avionics power systems.

Use of a removable XT90S arming plug provides a simple, reliable, and inspectable
means of propulsion arming without additional switching hardware.

---

Ownership: Chun Hsien Tseng – electrical wiring architecture and integration planning
