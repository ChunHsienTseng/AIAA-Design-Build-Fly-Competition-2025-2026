# Propulsion System Decision Summary

## Purpose
This document summarizes the **finalized propulsion-related design decisions**
resulting from the completed geometry constraints and propulsion trade studies.

The goal is to clearly record:
- What configuration has been selected
- Why it was selected over alternatives
- What parameters are now fixed versus adjustable

This summary serves as the baseline for subsequent electrical system integration,
manufacturing, and testing activities.

---

## Fixed Inputs
The following inputs are treated as fixed and non-negotiable:

- Competition constraints: ≤100 Wh battery energy, ≤100 A propulsion current
- Aircraft configuration: Taildragger
- Propeller hub height: 10 inches above ground
- Landing gear geometry: Fixed by CAD design

These constraints are defined in:
`00_project_overview/requirements_constraints.md`

---

## Key Design Decisions

### 1. Propeller Diameter Envelope
Based on landing gear geometry and conservative takeoff assumptions
(rotation angle, squat, and clearance margin), the feasible propeller
diameter is limited to:

- **Recommended propeller diameter: 16–17 inches**

Propellers ≥18 inches are not feasible without modifying landing gear
geometry or thrust line height.

(Reference: `02_geometry_constraints/prop_clearance_calc.md`)

---

### 2. Battery Architecture (Baseline)
Two battery architectures were evaluated: 5S and 6S.

- **Baseline selection:** **5S battery architecture**
- Typical configuration: 5S, 5000 mAh (~92.5 Wh)

**Rationale:**
- Provides meaningful margin under the 100 Wh limit
- Reduces compliance and inspection risk
- Sufficient to meet propulsion power requirements for a 16–17″ prop

A 6S architecture remains technically viable but was not selected as the
baseline due to near-zero Wh margin in commonly available packs.

(Reference: `03_propulsion_trade_study/battery_5s_vs_6s.md`)

---

### 3. Motor Kv Range
Given the fixed propeller diameter envelope and target operating RPM,
motor Kv must be matched to the selected battery voltage.

- **Target motor Kv range (5S): 400–450 Kv**

This range enables the required loaded RPM for 16–17″ propellers while
maintaining acceptable current levels and tuning flexibility via prop pitch.

(Reference: `03_propulsion_trade_study/kv_voltage_rpm_matching.md`)

---

## Summary of Selected Baseline Configuration

| Parameter | Baseline Selection |
|---------|-------------------|
| Propeller diameter | 16–17 inches |
| Battery architecture | 5S |
| Battery energy | ~92.5 Wh |
| Motor Kv range | 400–450 Kv |

---

## Parameters Remaining Adjustable
The following parameters remain open for tuning during testing and integration:

- Exact motor model within the 400–450 Kv range
- Propeller pitch (within structural and current limits)
- ESC selection and cooling implementation
- Electrical wiring and protection details

Adjustments to these parameters must remain consistent with the fixed
constraints and decisions listed above.

---

## Implications for Next Design Phases
With the propulsion baseline defined, the following activities can proceed:

- Electrical system power budgeting and protection design
- ESC and wiring selection
- Bench testing of propulsion system (thrust, current, temperature)
- Manufacturing and installation planning

---

## Conclusion
The propulsion system baseline has been established using a
constraint-driven, system-level engineering approach. The selected
configuration balances performance, regulatory compliance, and integration
risk, and provides a stable foundation for downstream design and testing work.

---

Ownership: Chun Hsien Tseng – propulsion system trade study and decision synthesis
