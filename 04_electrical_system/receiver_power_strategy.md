# Receiver Power Strategy (V0.1 – Concept Design)

## Purpose
This document defines the **receiver and avionics power strategy**
for the aircraft at the conceptual design stage.

The objective is to ensure:
- Reliable receiver and servo operation
- Immunity to propulsion system electrical noise
- Compliance with DBF requirements
- Robust control continuity under worst-case servo loading

This document complements:
- `04_electrical_system/wiring_architecture.md`
- `04_electrical_system/protection_and_fusing.md`
- `01_system_architecture/interfaces.md`

---

## Avionics Power Architecture Overview

The aircraft uses a **fully independent avionics power system**
separate from the propulsion battery.

Architecture summary:
- Dedicated receiver battery supplies receiver and servos
- ESC internal BEC is disabled and not used
- Receiver power switch provides operational control
- No electrical coupling between propulsion and avionics power paths

This architecture is selected to maximize control reliability and
minimize EMI and brownout risk.

---

## Rationale for Separate Receiver Battery

### Brownout Risk in High-Power Systems
High-power propulsion systems can induce:
- Voltage sag during throttle transients
- EMI coupling through shared grounds or BECs
- Receiver resets under simultaneous servo stall conditions

A dedicated receiver battery isolates avionics from these effects.

---

### DBF Compliance Considerations
- Independent receiver power is a common and accepted DBF practice
- Eliminates reliance on ESC BEC performance under high load
- Simplifies inspection and failure mode analysis

---

## Receiver Battery Characteristics (Concept Level)

### Voltage
- Nominal output: 4.8–6.0 V (depending on chemistry)
- Compatible with receiver and servo ratings

### Capacity
- Sized to support worst-case servo loading with margin
- Exact capacity **TBD** pending servo count and bench testing

### Chemistry (TBD)
Candidate options include:
- 2S LiFe
- 2S LiPo with regulation
- 5-cell NiMH

Final selection will be based on:
- Weight
- Voltage stability
- Charging and handling considerations

---

## Receiver Power Switch

### Function
- Provides a clear ON/OFF control for avionics power
- Allows safe handling and setup independent of propulsion system
- Enables staged power-up during ground operations

### Design Considerations
- Rated for servo transient currents
- Mechanically secure and vibration-resistant
- Easily accessible during pre-flight checks

---

## Servo Load and Power Distribution

### Considerations
- Multiple servos may draw simultaneous stall currents
- Voltage drop in receiver wiring must be minimized
- Daisy-chaining high-load servos should be avoided

### Strategy
- Short power paths from receiver battery to receiver
- Star-like distribution from receiver to servos where possible
- Bench testing will validate voltage stability under load

---

## Verification Plan (Concept)
Receiver power strategy will be validated during bench testing by:
- Aggressive servo movement tests
- Observation of receiver stability
- Monitoring for resets or brownout symptoms

If issues are observed, mitigation options include:
- Increasing receiver battery capacity
- Improving power distribution wiring
- Adding voltage buffering as needed

---

## Conclusion
A dedicated receiver battery with an independent power switch
provides the most robust and inspectable avionics power solution
for this DBF aircraft.

This strategy prioritizes control reliability and simplifies
integration and testing.

---

Ownership: Chun Hsien Tseng – avionics power strategy and integration
