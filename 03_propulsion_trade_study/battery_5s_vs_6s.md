# Battery Architecture Trade Study (5S vs 6S)

## Purpose
This document compares 5S and 6S battery architectures for the aircraft propulsion
system under DBF constraints, focusing on **rules compliance margin**, **current margin**,
and **system integration risk**.

This study assumes the propeller diameter envelope is fixed at **16–17 inches** per:
`02_geometry_constraints/prop_clearance_calc.md`

Kv–voltage RPM matching is documented separately in:
`03_propulsion_trade_study/kv_voltage_rpm_matching.md`

---

## Competition Constraints (Relevant)
- Battery energy limit: **≤ 100 Wh**
- Propulsion current limit: **≤ 100 A** (fuse-limited)

See baseline constraints:
`00_project_overview/requirements_constraints.md`

---

## Candidate Batteries
The following candidate packs are considered:

### Option A — 5S 5000 mAh
- Nominal voltage: 18.5 V
- Capacity: 5.0 Ah
- Energy (nominal): Wh = 18.5 × 5.0 = **92.5 Wh**
- Margin to 100 Wh: **+7.5 Wh**

### Option B — 6S 4500 mAh
- Nominal voltage: 22.2 V
- Capacity: 4.5 Ah
- Energy (nominal): Wh = 22.2 × 4.5 = **99.9 Wh**
- Margin to 100 Wh: **+0.1 Wh** (effectively zero)

---

## Interpretation: Wh Margin vs Performance
### Key point: Wh is energy capacity, not instantaneous power
- **Wh** determines how long the system can deliver a given power level.
- **Power (W)** depends on motor–prop load and is limited by current, ESC, and system losses.

In DBF missions (short flight durations), the additional ~7.4 Wh between 92.5 Wh and 99.9 Wh
typically does **not** create a meaningful performance advantage, but it does materially
change compliance risk.

---

## Compliance Risk Considerations
Operating extremely close to 100 Wh increases the chance of inspection disputes due to:
- Manufacturer labeling conventions and rounding
- Potential interpretation differences (nominal vs max voltage basis)
- Administrative/technical inspection conservatism

Therefore, a battery with near-zero Wh margin may be technically compliant yet
operationally risky.

---

## Current Margin Considerations (System-Level)
For the same required shaft power, current scales approximately as:

I ≈ P / V

Therefore:
- 6S (higher V) generally enables **lower current** for the same power
- Lower current improves thermal margin and reduces stress on wiring/ESC

This is a legitimate advantage of 6S, but it must be weighed against the Wh compliance risk.

---

## Summary of Trade-Off
- **5S (92.5 Wh):** strong Wh margin; simpler compliance; potentially higher current
- **6S (99.9 Wh):** lower current; better thermal margin; near-zero Wh margin (higher compliance risk)

---

## Recommendation (Baseline)
Given the fixed 16–17 inch propeller envelope and the competition energy limit,
the **baseline recommendation** is to prioritize rules compliance margin:

- Baseline: **5S battery architecture**
- Rationale: meaningful Wh buffer reduces inspection and administrative risk

6S remains a viable alternative if a clearly compliant <100 Wh pack with sufficient margin
is available and confirmed acceptable by the team/instructor.

---

Ownership: Chun Hsien Tseng – battery architecture trade study and compliance-risk rationale
