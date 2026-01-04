# Bench Test Plan – Propulsion and Electrical Validation (V0.1)

## Purpose
This bench test plan defines the procedures and measurements required to validate
the propulsion and electrical system **before flight testing**.

Primary objectives:
- Verify compliance margin to DBF limits (≤100 A propulsion current)
- Confirm safe thermal behavior (wiring/connectors/ESC/motor)
- Establish baseline performance data for prop/motor/battery selection
- Validate ground safety workflow using the XT90S arming plug

This plan is aligned with:
- Propulsion baseline: `03_propulsion_trade_study/decision_summary.md`
- Wiring architecture: `04_electrical_system/wiring_architecture.md`
- Protection strategy: `04_electrical_system/protection_and_fusing.md`
- System interfaces: `01_system_architecture/interfaces.md`

---

## System Configuration Under Test

### Electrical Architecture (DBF-Compliant)
- Propulsion battery: 5S (≤100 Wh baseline)
- Propulsion arming/disarming: **removable XT90S anti-spark arming plug**
- Avionics power: separate receiver battery (ESC BEC disabled)

### Propeller Envelope
- Propeller diameter: 16–17 inches (per landing gear clearance analysis)

---

## Required Instrumentation (Minimum Set)
Minimum measurements required:
- **Current** (propulsion): clamp meter or inline current sensor
- **Voltage** (propulsion battery): multimeter or telemetry
- **Temperature**: IR thermometer or thermal probe (ESC, motor, connectors, wiring)
- **Time**: stopwatch or phone timer

Recommended (if available):
- **RPM**: optical tachometer
- **Thrust**: load cell or scale-based thrust stand
- **Data logging**: ESC telemetry or inline wattmeter logging

---

## Safety Requirements (Mandatory)

### Physical Safety Setup
- Propeller area clear; no personnel in prop arc during arming
- Test stand or restrained airframe (no free movement)
- Eye protection recommended
- Fire safety: LiPo safe bag/box nearby; extinguisher if available

### Ground Arming Procedure (Must Be Followed)
**Power-Up**
1. Receiver battery ON
2. Verify throttle at zero and throttle failsafe active
3. Confirm test area is clear
4. Insert XT90S arming plug (propulsion armed)

**Power-Down**
1. Remove XT90S arming plug (propulsion disarmed)
2. Receiver battery OFF
3. Disconnect propulsion battery if required

---

## Test Matrix (What We Will Test)

### Variables
- Propeller candidate(s): 16–17 inch diameter with 2–3 pitch options (as available)
- Throttle points: 30%, 50%, 70%, 100%
- Duration: short runs with cool-down (avoid overheating early)

### Fixed Conditions
- Same battery pack (or same model pack) per test set
- Same motor/ESC/wiring configuration
- Same ambient conditions as possible

---

## Test Procedures

### Test 0 – Pre-Check and Documentation
Record:
- Date/time, ambient temperature
- Battery model, capacity, C-rating, measured voltage
- Propeller diameter/pitch and condition
- ESC model/settings (timing, PWM frequency, brake)
- Wire gauge and connector types in propulsion loop
- Fuse rating installed (if applicable)

Pass condition:
- Throttle failsafe confirmed
- XT90S arming plug accessible and removable
- No loose wiring; connectors fully seated

---

### Test 1 – No-Prop Electrical Verification (Optional but Recommended)
Purpose: confirm signal path and failsafe without prop risk.

Steps:
1. Remove propeller
2. Arm propulsion with XT90S plug
3. Verify motor starts smoothly at low throttle
4. Verify failsafe behavior (simulate signal loss if possible)

Pass condition:
- Smooth spin-up
- Expected rotation direction
- Failsafe cuts throttle

---

### Test 2 – Incremental Throttle Current Sweep (With Prop Installed)
Purpose: map current draw vs throttle and identify peak current margin.

Steps:
1. Install propeller securely
2. Run at 30% throttle for 10–15 seconds
3. Record: current, voltage, ESC temp, motor temp
4. Cool down 1–2 minutes
5. Repeat at 50%, 70%
6. At 100% throttle, run 5–10 seconds only for initial peak capture

Record at each point:
- I_peak (highest observed)
- V_loaded
- Temperatures (ESC, motor, battery connector, fuse holder, wiring near connectors)

Pass condition (preliminary):
- I_peak does not exceed DBF limit
- No abnormal vibration
- No rapid temperature spikes at connectors

---

### Test 3 – Sustained Load Thermal Check
Purpose: verify continuous operation does not overheat wiring/connectors/ESC.

Steps:
1. Choose a representative throttle (typically 60–75%)
2. Run for 30–60 seconds (start conservative)
3. Record temperature rise every 15 seconds:
   - ESC case
   - Motor can
   - XT90/XT90S interfaces
   - Fuse holder
   - 8 AWG cable near lugs/terminals (if used)

Stop immediately if:
- Smell of hot insulation
- Connector discoloration
- ESC temperature rises rapidly
- Any component becomes too hot to safely approach

Pass condition:
- Temperatures stabilize or rise slowly
- No single hotspot at connectors/terminals

---

### Test 4 – (Optional) RPM and Thrust Characterization
If RPM measurement is available:
- Record RPM at 50%, 70%, 100% throttle for each prop

If thrust stand is available:
- Record static thrust at 70% and 100% (short duration)
- Note that static thrust is used for comparison and sizing, not exact flight prediction

---

### Test 5 – Avionics Brownout Check (Separate Receiver Battery)
Purpose: ensure receiver power remains stable under servo activity during propulsion operation.

Steps:
1. With propulsion disarmed (XT90S plug removed), move servos aggressively
2. Observe receiver behavior (no resets, no control dropouts)
3. With propulsion armed and motor running at low throttle, repeat servo activity
4. If telemetry is available, record receiver voltage

Pass condition:
- No receiver reset or brownout symptoms
- Control response remains stable

---

## Data Recording Template (Copy/Paste)

For each prop tested:

- Prop: ___ in × ___ pitch  
- Battery: 5S ___ mAh (measured V: ___)  
- Ambient temp: ___ °F/°C  

Throttle 30%:
- I_peak: ___ A | V_loaded: ___ V | ESC: ___ °C | Motor: ___ °C | Connector: ___ °C

Throttle 50%:
- I_peak: ___ A | V_loaded: ___ V | ESC: ___ °C | Motor: ___ °C | Connector: ___ °C

Throttle 70%:
- I_peak: ___ A | V_loaded: ___ V | ESC: ___ °C | Motor: ___ °C | Connector: ___ °C

Throttle 100% (short run):
- I_peak: ___ A | V_loaded: ___ V | ESC: ___ °C | Motor: ___ °C | Connector: ___ °C

Sustained run (___% throttle, ___ sec):
- Max ESC: ___ °C | Max Motor: ___ °C | Max Connector: ___ °C | Notes: ___

Observations:
- Vibration: (none / mild / severe)  
- Any abnormal heat hotspots: ___  
- Any receiver issues: (none / brownout / reset)  
- Notes: ___

---

## Decision Rules (How Results Drive Design Changes)

### If peak current is too high:
- Reduce prop pitch first
- Consider smaller diameter within 16–17 envelope
- Re-check motor Kv match and ESC rating

### If connectors or wiring run hot:
- Improve mechanical strain relief and contact quality
- Shorten high-current loop where possible
- Upgrade connector implementation (ensure genuine XT90/XT90S)
- Re-evaluate fuse holder rating and mounting

### If ESC or motor overheats:
- Improve cooling (ducting, airflow)
- Reduce sustained throttle or prop load (pitch)
- Confirm ESC timing and settings

### If receiver brownout occurs:
- Increase receiver battery capability
- Reduce servo voltage drop (shorter leads, better distribution)
- Verify BEC truly disabled and no unintended coupling

---

## Exit Criteria (Bench Test “Pass” for Flight Readiness)
Bench testing is considered sufficient to proceed toward initial taxi/flight tests when:
- Peak propulsion current shows margin to rule limit
- No critical hotspots at connectors/fuse holder/wiring during sustained run
- Throttle failsafe confirmed
- Receiver power remains stable under servo stress test
- XT90S arming plug workflow is repeatable and safe

---

Ownership: Chun Hsien Tseng – bench test planning and integration validation
