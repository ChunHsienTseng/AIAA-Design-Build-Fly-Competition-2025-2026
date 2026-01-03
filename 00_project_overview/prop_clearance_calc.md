# Propeller Clearance and Diameter Envelope Calculation

## Purpose
This document determines the **feasible propeller diameter envelope** based on
aircraft landing gear geometry and takeoff rotation constraints.

The resulting propeller diameter limit serves as a **blocking input** for
subsequent propulsion system trade studies, including motor Kv selection,
battery architecture, and electrical current sizing.

---

## Reference Constraints and Assumptions
This analysis is based on the requirements and assumptions defined in:

`00_project_overview/requirements_constraints.md`

Key referenced inputs are summarized below for clarity.

### Fixed Geometry Inputs
- Landing gear configuration: Taildragger
- Propeller hub height above ground (h0): 10.0 inches
- Landing gear geometry: Fixed by CAD design

### Assumptions
- Takeoff rotation angle (α): ≈ 12°
- Landing gear squat / ground irregularity (s): ≈ 0.4 inches
- Propeller ground clearance margin (m): ≈ 1.5 inches

These assumptions are conservative and aligned with common DBF practice.
They may be refined after physical testing if required.

---

## Clearance Geometry Model

During takeoff rotation, the aircraft pitches about the main landing gear contact
point. The lowest point of the propeller tip occurs during this rotation.

To avoid propeller strike, the vertical distance between the propeller tip and
the ground must remain positive with an adequate safety margin.

The maximum allowable propeller radius is therefore limited by:

R_max = (h0 − s − m) / cos(α)

where:
- h0 = propeller hub height above ground
- s  = landing gear squat
- m  = ground clearance margin
- α  = takeoff rotation angle

The corresponding maximum propeller diameter is:

D_max = 2 × R_max

---

## Numerical Evaluation

Substituting the known values:

- h0 = 10.0 in
- s  = 0.4 in
- m  = 1.5 in
- α  = 12°
- cos(12°) ≈ 0.978

Calculation:

R_max = (10.0 − 0.4 − 1.5) / 0.978  
R_max = 8.1 / 0.978  
R_max ≈ 8.28 in  

D_max = 2 × 8.28 ≈ 16.6 in

---

## Resulting Propeller Diameter Envelope

Based on the above calculation:

- Maximum geometric propeller diameter: ≈ 16.6 inches
- Recommended design envelope: **16–17 inches**

This envelope provides reasonable margin for:
- Surface irregularities
- Dynamic effects during rotation
- Pilot technique variability

---

## Design Implications

The 16–17 inch propeller envelope directly constrains propulsion system design:

- Propellers ≥ 18 inches are **not feasible** without modifying landing gear
  height or thrust line geometry.
- Motor Kv selection must target appropriate RPM for a 16–17 inch propeller.
- Battery architecture (5S vs 6S) must be evaluated within this fixed diameter
  limit.

This propeller clearance analysis **precedes and informs** motor–propeller–
battery trade studies documented in:

`03_propulsion_trade_study/`

---

## Sensitivity Notes
Small variations in assumed rotation angle or clearance margin can shift the
maximum allowable diameter by several tenths of an inch. However, these changes
do not materially alter the conclusion that the feasible propeller size is
bounded near 16–17 inches for the current geometry.

---

## Conclusion
Given the fixed landing gear geometry and conservative takeoff assumptions,
the aircraft can safely accommodate a propeller diameter of approximately
**16–17 inches**.

This constraint is treated as fixed for subsequent propulsion and electrical
system design unless the landing gear geometry is revised.

---

Ownership: Chun Hsien Tseng – geometry-based propulsion constraint analysis
