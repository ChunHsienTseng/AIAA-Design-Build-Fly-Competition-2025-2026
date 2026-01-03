# Electrical System Power Budget

## Purpose
This document defines the **electrical power budget** for the aircraft,
covering both propulsion and avionics subsystems.

The objective is to:
- Ensure compliance with DBF electrical rules
- Quantify peak and typical power demands
- Provide inputs for wiring, protection, and system integration decisions

This analysis is based on the finalized propulsion baseline defined in:
`03_propulsion_trade_study/decision_summary.md`

---

## System Architecture Overview
The electrical system is divided into **two fully independent power paths**,
as required by DBF rules:

1. **Propulsion Power Path**
   - Propulsion Battery → Safety/Arming → ESC → Motor → Propeller

2. **Avionics / Control Power Path**
   - Receiver Battery → Receiver Switch → Receiver → Servos

If the ESC includes an internal BEC, it is **disabled and not used**.

---

## Reference Constraints
- Maximum battery energy (propulsion): **≤ 100 Wh**
- Maximum propulsion current: **≤ 100 A** (fuse-limited)
- Separate receiver battery required for avionics
- Baseline propulsion battery architecture: **5S (~18.5 V nominal)**

(Reference: `00_project_overview/requirements_constraints.md`)

---

## Propulsion Power Budget

### Assumptions
- Nominal battery voltage: 18.5 V (5S)
- Peak propulsion current: ≤ 100 A
- Typical operating current: 60–80 A
- High-power operation duration: short (DBF mission profile)

### Power Estimates
- **Peak electrical input power**  
  P_peak ≈ 18.5 V × 100 A ≈ **1850 W**

- **Typical operating power**  
  P_typical ≈ 18.5 V × 70 A ≈ **1300 W**

These values represent electrical input to the ESC and motor.
Mechanical shaft power will be lower due to system losses.

---

## Avionics and Control Power Budget  
### (Separate Receiver Battery – DBF Compliant)

### Architecture Requirement
Receiver and servo power is supplied by a **dedicated receiver battery**.
The propulsion battery does **not** supply avionics power.
Any ESC-integrated BEC is **disabled** and electrically isolated.

### Typical Loads

| Component | Quantity | Estimated Current | Voltage | Power |
|---------|----------|-------------------|---------|-------|
| Receiver | 1 | ~0.1 A | 4.8–6.0 V | ~0.5 W |
| Servos (average) | 4–6 | ~0.3–0.5 A each | 6.0 V | ~7–18 W |
| Servos (stall, transient) | 4–6 | up to ~2 A each | 6.0 V | transient |

### Notes
- Servo stall currents are transient and typically not simultaneous.
- Receiver power stability is safety-critical.
- Brownout prevention is a primary design requirement.

---

## Energy Considerations

### Propulsion Battery
- Energy budget governed by 100 Wh limit
- Typical DBF flights consume only a fraction of available energy
- Energy margin is maintained by baseline 5S battery selection

### Receiver Battery
- Avionics energy consumption is **negligible** relative to propulsion
- Typical energy use ≪ 1 Wh per flight
- Receiver battery sizing is driven by reliability, not endurance

---

## Power Margin and Risk Considerations

### Propulsion Path
- Peak current constrained by 100 A fuse
- ESC and wiring must tolerate short-duration overloads
- Thermal margin must be verified via bench testing

### Avionics Path
- Receiver battery must support transient servo loads with margin
- Voltage stability is more critical than absolute capacity
- Electrical noise isolation from propulsion system is required

---

## Implications for Electrical Design
This power budget informs the following downstream decisions:

- Main power wiring gauge and connector selection
- Arming/safety switch placement
- Receiver battery type and capacity
- Electrical protection and fail-safe strategy

These topics are addressed in:
- `04_electrical_system/protection_and_fusing.md`
- `04_electrical_system/wiring_architecture.md`

---

## Conclusion
The electrical power budget confirms that:
- Propulsion power dominates system electrical demand
- Avionics loads are small but safety-critical
- A fully separated receiver battery architecture is required and implemented

This budget provides a quantitative foundation for detailed electrical
integration, manufacturing, and testing activities.

---

Ownership: Chun Hsien Tseng – electrical power budgeting and DBF compliance analysis
