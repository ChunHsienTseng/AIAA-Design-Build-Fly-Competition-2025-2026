# Electrical Wiring Architecture (V0.1 – Concept Design)

## Purpose
This document defines the **electrical wiring architecture and design principles**
for the aircraft at the conceptual stage.

The objective is to:
- Establish clear separation between propulsion and avionics power paths
- Define wiring topology, routing principles, and interface boundaries
- Identify electrical noise and reliability risks early
- Provide a stable framework for detailed wiring and protection design

This document intentionally avoids final wire gauges, connector part numbers,
and harness layouts, which will be finalized after component procurement and
bench testing.

---

## Architectural Overview

The electrical system consists of **two fully independent wiring architectures**:

1. **Propulsion Power Wiring**
   - High-current, high-noise power delivery
   - Short-duration peak loads up to DBF limits

2. **Avionics / Control Wiring**
   - Low-voltage, safety-critical control power
   - Must remain operational regardless of propulsion system state

This separation is mandatory for DBF compliance and system reliability.

(Reference system block diagram:
`01_system_architecture/figures/system_block_diagram.png`)

---

## Propulsion Power Wiring Architecture

### Power Path
Propulsion battery → Arming/Safety Device → Main Fuse → ESC → Motor

### Key Characteristics
- High current (up to 100 A peak)
- Rapid current transients
- Significant electromagnetic interference (EMI) potential

### Design Principles
- Minimize total wire length in the high-current loop
- Use direct, point-to-point routing with minimal splices
- Avoid routing propulsion power wiring near avionics signal wiring
- Ensure mechanical strain relief at battery, switch, and ESC connections

---

## Avionics / Control Wiring Architecture  
### (Separate Receiver Battery – DBF Compliant)

### Power Path
Receiver battery → Receiver switch → Receiver → Servos

### Key Characteristics
- Low voltage (≈5–6 V)
- Lower average current but high transient stall currents
- Safety-critical; brownout is unacceptable

### Design Principles
- Independent wiring from propulsion system
- Short, low-resistance paths from receiver battery to receiver
- Star-style power distribution from receiver to servos where possible
- Avoid daisy-chaining high-load servos through thin traces or long leads

---

## Control Signal Wiring

### Receiver → ESC
- PWM throttle signal only (no power transfer)
- ESC internal BEC is disabled and not used
- Signal ground referenced only to receiver battery system

### Design Principles
- Route control signal wiring away from high-current propulsion wiring
- Cross high-current wires at approximately 90° if unavoidable
- Avoid long parallel runs with motor phase wires

---

## Grounding and Return Path Considerations

### Philosophy
- No shared power return between propulsion and avionics systems
- Each system maintains its own closed current loop
- Signal grounds are kept local to their respective power systems

### Rationale
This minimizes:
- Ground bounce
- Noise coupling into control signals
- Risk of receiver reset during high-power operation

---

## EMI and Noise Mitigation

Potential noise sources:
- ESC switching
- Motor phase currents
- High dI/dt during throttle changes

Mitigation strategies:
- Keep ESC-to-motor phase wires as short as practical
- Twist motor phase wires when possible
- Maintain physical separation between power and signal wiring
- Add ferrite beads to servo leads if bench testing indicates noise sensitivity

---

## Connector and Interface Standardization (Preliminary)

At the architectural level:
- High-current connectors should be rated comfortably above expected continuous current
- Control connectors should prioritize retention and vibration resistance
- All connectors should be keyed or polarized to prevent misconnection

Specific connector types and wire gauges are **TBD** pending component selection
and bench test results.

---

## Assembly and Inspection Considerations

- Wiring routes must be visible and inspectable
- Chafing protection required where wires pass near structure
- Clear labeling of propulsion vs avionics wiring
- Receiver battery wiring must remain accessible for inspection and servicing

---

## TBD Items (To Be Finalized)
The following items will be finalized after procurement and testing:

- Wire gauge selection for propulsion and avionics wiring
- Connector part numbers and ratings
- Final routing paths and harness lengths
- Fuse rating and placement details
- Strain relief and mounting hardware

---

## Relation to Downstream Design
This wiring architecture provides inputs to:
- Electrical protection and fusing design
- Detailed harness drawings
- Manufacturing and assembly procedures
- Ground and flight test validation

Subsequent documents:
- `04_electrical_system/protection_and_fusing.md`
- `06_test_and_validation/bench_test_plan.md`

---

## Conclusion
This document establishes a clear, DBF-compliant wiring architecture that
prioritizes safety, reliability, and noise isolation.

By defining wiring principles before physical implementation, the risk of
integration issues during assembly and testing is significantly reduced.

---

Ownership: Chun Hsien Tseng – electrical wiring architecture and integration planning
