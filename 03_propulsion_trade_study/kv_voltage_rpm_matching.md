# Motor Kv, Voltage, and RPM Matching

## Purpose
This document evaluates the relationship between **motor Kv**, **battery voltage**,
and **propeller operating RPM** to identify feasible propulsion configurations
for the aircraft.

The analysis is constrained by the propeller diameter envelope determined in:

`02_geometry_constraints/prop_clearance_calc.md`

and the system-level limits defined in:

`00_project_overview/requirements_constraints.md`

---

## Design Context
The aircraft geometry limits the propeller diameter to **16–17 inches**.
For a given propeller diameter and pitch, acceptable performance requires the
propeller to operate within a reasonable RPM range that balances:

- Static thrust
- Current draw (≤ 100 A)
- Propeller efficiency
- Motor torque capability

Motor Kv and battery voltage must therefore be selected together as a system.

---

## RPM Requirement for 16–17 Inch Propellers
Based on typical RC propeller performance data and DBF experience, a
16–17 inch propeller generally operates efficiently in the approximate range of:

- **5,500 – 6,500 RPM (loaded)**

Significantly higher RPM increases current draw and reduces efficiency, while
lower RPM may not provide sufficient static thrust for takeoff.

This RPM range is used as a target for motor–battery matching.

---

## Motor Kv and Voltage Relationship
Motor Kv defines the motor’s no-load speed constant:

RPM_no-load ≈ Kv × V

Under propeller load, the actual operating RPM is lower due to torque demand,
winding resistance, and ESC losses. A common engineering approximation is:

RPM_loaded ≈ 0.75 – 0.85 × (Kv × V)

For early-stage trade studies, an **80% loading factor** is used.

---

## Candidate Battery Architectures

### 5S Battery (Nominal Voltage ≈ 18.5 V)
For a target loaded RPM of ~6,000 RPM:

Required Kv ≈ 6000 / (0.8 × 18.5)  
Required Kv ≈ **405 Kv**

This places the feasible Kv range approximately at:

- **400 – 450 Kv**

This range provides flexibility for prop pitch selection and current tuning.

---

### 6S Battery (Nominal Voltage ≈ 22.2 V)
For the same target loaded RPM:

Required Kv ≈ 6000 / (0.8 × 22.2)  
Required Kv ≈ **338 Kv**

This places the feasible Kv range approximately at:

- **330 – 360 Kv**

---

## Interpretation of Results

Both battery architectures can achieve the required RPM for a 16–17 inch propeller
when paired with an appropriate motor Kv:

- **5S systems** require higher Kv motors
- **6S systems** require lower Kv motors

This relationship is a direct consequence of motor speed constant physics and
does not inherently favor one architecture over the other in terms of thrust.

---

## Design Trade-Off Considerations

While both architectures can meet RPM requirements, they differ in secondary effects:

### 5S Architecture
- Higher current for the same power
- Lower nominal voltage
- Greater Wh margin under the 100 Wh rule (with common 5S packs)
- Wider motor availability in the 400–450 Kv range

### 6S Architecture
- Lower current for the same power
- Higher nominal voltage
- Tighter Wh margin under the 100 Wh rule
- Requires careful battery selection to avoid compliance risk

These trade-offs are evaluated in detail in:

`03_propulsion_trade_study/battery_5s_vs_6s.md`

---

## Conclusion
Given the fixed propeller diameter envelope of **16–17 inches**, both
**5S (400–450 Kv)** and **6S (330–360 Kv)** motor–battery combinations
can achieve the required operating RPM.

Final selection between these architectures should be driven by:
- Energy margin (Wh compliance)
- Current margin
- Component availability
- System-level integration considerations

---

Ownership: Chun Hsien Tseng – motor Kv and voltage matching analysis
