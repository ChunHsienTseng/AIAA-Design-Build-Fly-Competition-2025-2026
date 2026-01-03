# Electrical Protection and Fusing (V0.1 – Concept Design)

## Purpose
This document defines the aircraft's **electrical protection strategy** at the
concept design stage, including fuse philosophy, protection objectives, and
inspection considerations under DBF constraints.

The propulsion system uses a **removable XT90S anti-spark arming plug** as the
primary arming and disarming mechanism.

---

## System Safety Architecture

The electrical system is divided into two independent power paths:

1. **Propulsion Power Path**
   Propulsion battery → Main fuse → **XT90S arming plug (removable)** → ESC → Motor

2. **Avionics / Control Power Path**
   Receiver battery → Receiver power switch → Receiver → Servos

ESC internal BEC is disabled and not used.

---

## Protection Objectives

Electrical protection addresses three risk categories:

### A. Catastrophic Fault Protection
- Prevent overheating or fire due to short circuits or severe overcurrent
- Protect wiring, connectors, ESC, and battery during fault conditions

### B. Control Continuity and Reliability
- Prevent receiver brownout
- Maintain stable control power during servo transients
- Minimize EMI-induced control disturbances

### C. Rules Compliance and Inspection Robustness
- Align with DBF electrical limits
- Provide clear, inspectable safety states
- Ensure documentation consistency across system artifacts

---

## Main Fuse Philosophy (Propulsion Path)

### Role of the Main Fuse
The propulsion main fuse provides **catastrophic fault protection**.
It is not intended to regulate normal operating current.

Due to fuse time–current characteristics, near-rated currents may be sustained
for extended periods without tripping.

---

### Fuse Rating Considerations
- DBF rules impose an upper bound on propulsion current
- Fuse rating must comply with the rule limit (upper bound 100 A)
- Normal operation is designed to remain below the fuse rating with margin

Final fuse rating is **TBD**, pending:
- Bench-measured peak current
- Thermal behavior of wiring and connectors
- ESC current tolerance

---

## XT90S Arming Plug as a Safety Element

### Function
The XT90S arming plug provides a **physical interruption of the propulsion power
path**.

- Plug removed: propulsion system physically disarmed
- Plug inserted: propulsion system armed

### Safety Benefits
- Clear, visible safety state during ground handling
- Reduced connector damage due to anti-spark design
- Eliminates reliance on unplugging the main battery for routine arming

---

## Avionics Path Protection

### Receiver Power Strategy
- Dedicated receiver battery supplies receiver and servos
- Receiver power switch provides operational control
- Optional small fuse may be added to protect avionics wiring

Primary protection objective is **control continuity**, not high-energy fault
interruption.

---

## Ground Safety Procedure (Concept)

### Power-Up
1. Receiver battery ON
2. Verify throttle failsafe and control neutral
3. Ensure personnel are clear of propeller
4. Insert XT90S arming plug

### Power-Down
1. Remove XT90S arming plug
2. Receiver battery OFF
3. Disconnect propulsion battery if required

---

## Inspection and Compliance Notes
- XT90S arming plug must be clearly identifiable
- Receiver and propulsion power paths must be unambiguous
- Fuse location and rating must be visible or documented
- BEC disablement must be verifiable

---

## Verification Plan (Concept)

Bench testing shall verify:
- Peak propulsion current under static conditions
- Voltage sag under load
- Connector and wiring temperature rise
- Receiver voltage stability during servo stress testing

Results will be used to finalize fuse rating and wiring specifications.

---

## Conclusion
Electrical protection is achieved through a combination of:
- Rule-compliant fuse strategy
- System tuning to limit operational current
- Physical propulsion arming via XT90S anti-spark arming plug
- Independent avionics power architecture

This approach balances safety, reliability, and compliance without unnecessary
hardware complexity.

---

Ownership: Chun Hsien Tseng – electrical protection philosophy and compliance analysis
