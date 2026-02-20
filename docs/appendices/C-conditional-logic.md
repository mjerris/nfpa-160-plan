# Appendix C: Conditional Logic Map

Summary of form branching conditions for the questionnaire system. Use this to implement show/hide logic on form fields.

## Submission Type Selection

At the start of a submission, users select one submission type. This is the top-level branch that determines which entity workflows, validation rules, and procedures apply.

| Condition | Shows Entity/Workflow | Hides | Section |
|---|---|---|---|
| Submission Type = Flame Effects | Entity 3 workflow (apparatus-based effects, Chapter 9 control systems), Chapter 9 procedures | All Entity 8 / Chapter 14 fields | [Ch. 9] |
| Submission Type = Fire Performances | Entity 8 workflow (performer-based effects, Chapter 14 props/wicks), Chapter 14 procedures | All Entity 3 / Chapter 9 fields | [Ch. 14] |

A submission must be one type: either flame effects or fire performances. They cannot be mixed in a single submission. At least one effect or performance must be defined.

## Installation Type Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Installation = Temporary | Temporary permit fields, extinguisher requirements, temporary inspection schedule | [5.1.2.2], [16.3], [C.2.1] |
| Installation = Permanent | Permanent permit fields, fire hazards evaluation, permanent inspection schedule | [5.1.2.1], [16.2], [C.2.2] |

## Fuel Type Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Fuel = Gaseous | Gaseous fuel fields (Entity 3, §3.2.1) | [Ch. 10] |
| Fuel = Liquid | Liquid fuel fields (Entity 3, §3.2.2) | [Ch. 12] |
| Fuel = Prepackaged Single-Use | Prepackaged fuel fields (Entity 3, §3.2.3) | [Ch. 11] |
| Fuel = Gel or Solid | Gel/solid fuel fields (Entity 3, §3.2.4) | [Ch. 13] |
| Fuel = LPG (subset of Gaseous) | LPG container orientation confirmation | [9.2.2.3] |

## Effect Type Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Hybrid = Yes | NFPA 160/1126 portion identification fields | [5.2.2.3] |
| Type = Automatic | Automatic control system fields (keyswitch, auto emergency stop, auto arming, auto firing) | [9.1.2], [9.2.1.5], [9.2.4.4], [9.2.5.5.2] |
| Type = Manual | Manual control system fields (manual emergency stop plan, manual arming, manual firing) | [9.2.1.4], [9.2.4.3], [9.2.5.5.1] |

## System Component Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Uses accumulators = Yes | Accumulator fields (design standard, volume, valves, charging, safe removal) | [9.2.2.6] |
| Uses central fuel distribution = Yes | Central distribution fields (shutoff, supervisor station, seat-tightness test) | [9.2.2.4] |
| Uses piping = Yes | Pressure test fields | [15.2] |
| Uses external pressure source = Yes | Isolation and depressurization fields | [12.1.8] |

## Hazard Area Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Cast/set pieces in hazard area = Yes | PME requirement fields | [9.2.4.6] |
| Hazard area not visible to flame effect operator = Yes | Alternative monitoring and enable button fields | [9.2.5.4.2], [9.2.5.4.3] |
| Ignition cannot be directly seen = Yes | Automatic arming confirmation fields | [9.2.4.3.2] |
| Interrelated system hazards exist = Yes | Direct validated status confirmation fields | [9.2.1.3], [9.2.3.1.2] |

## Venue Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Indoor venue = Yes | Ventilation, combustion air fields; indoor site plan additions | [5.3.2(5)(f)], [B.1.1.2] |
| Outdoor venue = Yes | Weather/wind, outdoor site plan additions | [B.1.1.1] |

## Additional Entity Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Standby personnel required = Yes | Standby personnel fields (names, equipment knowledge, communication) | [16.4] |

## Fire Protection Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Fire/life safety interruption requested = Yes | Three-condition documentation (AHJ approval, owner approval, fire watch) | [5.5.1] |
| AHJ requires additional equipment = Yes | Fixed or additional fire protection equipment fields | [16.3.1] |

## Performer Conditions

| Condition | Shows Fields For | Section |
|---|---|---|
| Bare skin in effect = Yes | Illusion of danger documentation | [7.10.2] |
| Smoking in performance = Yes | AHJ approval for performance smoking | [7.4.2] |
| Fire breathing with ethanol = Yes | Ethanol absorption warning and spacing guidance | [A.14.1.1.1] |
