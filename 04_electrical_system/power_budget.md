# Electrical System Power Budget

## Purpose
This document defines the **electrical power budget** for the aircraft,
covering both propulsion and avionics subsystems.

The objective is to:
- Ensure compliance with DBF electrical limits (≤100 A, ≤100 Wh)
- Identify peak and continuous power demands
- Provide inputs for wiring, protection, and ESC/BEC selection

This analysis is based on the finalized propulsion baseline defined in:
`03_propulsion_trade_study/decision_summary.md`

---

## System Overview
The electrical system is divided into two primary subsystems:

1. **Propulsion Power Path**
   - Battery → ESC → Motor → Propeller

2. **Avionics / Control Power Path**
   - Battery → BEC / Receiver Power → Receiver → Servos

These subsystems have different power characteristics and risk profiles
and are therefore budgeted separately.

---

## Reference Constraints
- Maximum propulsion current: **≤100 A** (fuse-limited)
- Maximum battery energy: **≤100 Wh**
- Baseline battery architecture: **5S (~18.5 V nominal)**

(Reference: `00_project_overview/requirements_constraints.md`)

---

## Propulsion Power Budget

### Assumptions
- Battery voltage (nominal): 18.5 V (5S)
- Peak propulsion current: ≤100 A
- Continuous propulsion current (estimated): 60–80 A
- Flight duration under high power: short (DBF mission profile)

### Power Estimates
- **Peak electrical power:**  
  P_peak ≈ 18.5 V × 100 A ≈ **1850 W**

- **Typical operating power:**  
  P_typical ≈ 18.5 V × 70 A ≈ **1300 W**

These values represent electrical input power to the ESC and motor.
Mechanical shaft power will be lower due to system losses.

---

## Avionics and Control Power Budget

### Major Loads
The following avionics loads are considered typical for a DBF aircraft:

| Component | Quantity | Estimated Current | Voltage | Power |
|---------|----------|-------------------|---------|-------|
| Receiver | 1 | ~0.1 A | 5–6 V | ~0.6 W |
| Control servos (avg) | 4–6 | ~0.3–0.5 A each (avg) | 6 V | ~7–18 W |
| Control servos (peak, transient) | 4–6 | up to ~2 A each (stall) | 6 V | transient |

### Notes
- Servo stall currents are **transient** and not simultaneous in normal flight
- Worst-case peaks must still be considered for BEC sizing
- Avionics power is small relative to propulsion power, but critical for safety

---

## Avionics Power Summary
- **Typical avionics power:** ~10–20 W
- **Peak transient power:** higher during aggressive control inputs
- **Energy contribution:** negligible compared to propulsion (≪1 Wh per flight)

This confirms that avionics loads do **not materially impact** the 100 Wh energy limit,
but they do affect BEC and wiring reliability.

---

## Power Margin Considerations

### Propulsion
- Peak power limited by 100 A fuse
- ESC and wiring must tolerate short-duration peak loads
- Thermal margin must be verified during bench testing

### Avionics
- BEC must support combined servo stall current with margin
- Voltage stability is critical to prevent receiver brownout
- Electrical noise isolation from propulsion system is important

---

## Implications for Electrical Design
This power budget informs the following downstream decisions:

- ESC current rating and cooling requirements
- Main power wiring gauge and connector selection
- BEC type (linear vs switching) and current rating
- Electrical protection and fail-safe strategy

These topics are addressed in subsequent documents:
- `04_electrical_system/protection_and_fusing.md`
- `04_electrical_system/wiring_architecture.md`

---

## Conclusion
The electrical power budget confirms that:
- The propulsion system operates near the upper end of available electrical power
- Avionics power consumption is small but safety-critical
- Clear separation of propulsion and control power considerations is required

This budget provides a quantitative foundation for detailed electrical system
integration and testing.

---

Ownership: Chun Hsien Tseng – electrical power budget and system-level sizing
