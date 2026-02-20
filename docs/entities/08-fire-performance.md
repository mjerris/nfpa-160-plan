# Entity 8: Fire Performance (Chapter 14)

A reusable entity for performer-based fire effects. Artists save one record per distinct fire performance routine. Multiple performances can be included in a single submission.

**Peer entity:** Entity 3 (Flame Effect) covers apparatus-based effects with control systems. A submission can include fire performances, flame effects, or both.

**Note:** Chapter 9 control system requirements do NOT apply to fire performances [9.1]. This entity contains the Chapter 14 requirements instead, which govern performers, props, spotters, and fueling procedures.

## 8.1 Performers

Performers are linked to a fire performance through Role Assignment records in Entity 2. Each person assigned to this submission who participates in this performance must have a Person Record (Entity 2.1) on file.

| Validation | Required | Section | Guidance |
|---|---|---|---|
| All performers meet operator competency requirements (experience/training or AHJ-acceptable license) | Yes | [14.1], [8.1.2] | Validated from Person Record (Entity 2.1) |
| All performers have substance abuse acknowledgment signed | Yes | [14.1.1.1] | Validated from Person Record (Entity 2.1) |
| Each performer physically capable of executing their performance | Yes | [14.1.1.2] | UI confirmation during role assignment |
| At least one cast member designated as flame effect operator | Yes | [14.1.1.3.1] | At least one Role Assignment for this submission must have Role = Flame Effect Operator; new in 2026 edition |
| Designated flame effect operator complies with Chapter 8 requirements | Yes | [14.1.1.3.2] | Validated from Person Record: age ≥21, competency docs, substance acknowledgment |

## 8.2 Rehearsal

| Field | Required | Section | Guidance |
|---|---|---|---|
| Each routine rehearsed in costume with fire prior to initial audience performance | Yes | [14.1.2.1] | Also required after any change to performance |
| Flame effects operator confirms cast and routine are ready for audience performance | Yes | [14.1.2.2] | |

## 8.3 Safety Personnel — Spotters

| Field | Required | Section | Guidance |
|---|---|---|---|
| At least one spotter for each performance and rehearsal with fire | Yes | [14.2.1] | |
| Spotter responsible for onstage and backstage fire safety (including wick extinguishment) | Yes | [14.2.1.1] | |
| Spotter aware of aspects of fire performance and familiar with the routine | Yes | [14.2.1.2] | |
| Spotter trained in: flame extinguishing, reaction time, equipment control, audience control | Yes | [14.2.1.3] | Reaction time = time to react to fires and hazards [A.14.2.1.3] |
| Spotter attentive with clear view and unobstructed access to their assigned hazard | Yes | [14.2.1.4] | |
| Spotter clothing compliant with Section 7.10 (protective clothing) | Yes | [14.2.1.5] | |
| Spotter carries safety towel at all times | Yes | [14.2.1.6] | |
| Spotter has unobstructed access to fire extinguishers (per 16.3.2) | Yes | [14.2.1.7] | |

## 8.4 Fire Props

### 8.4.1 General

| Field | Required | Section | Guidance |
|---|---|---|---|
| Fire props tested prior to each use to verify intended operation | Yes | [14.3.1.1] | |
| Any defect found shall be repaired or replaced | Yes | [14.3.1.2] | |

### 8.4.2 Wicks

| Field | Required | Section | Guidance |
|---|---|---|---|
| Wick material: fire-resistant, absorbent | Yes | [14.3.2.1] | Intended to temporarily store and convey fuel during performance |
| Wicks attached so they cannot be forcibly removed | Yes | [14.3.2.2] | |
| Wick material prevents loss of any part during use | Yes | [14.3.2.3] | Typically achieved using fireproof materials [A.14.3.2.3] |

### 8.4.3 Handles

| Field | Required | Section | Guidance |
|---|---|---|---|
| Shafted props: fire-resistant materials OR fire-resistant covering extending ≥4 in. (100 mm) beyond anticipated flame contact zones | Yes | [14.3.3.1] | Shafted props include clubs or staffs [A.14.3.3.1] |
| Handles attached so they cannot be forcibly removed | Yes | [14.3.3.2] | |
| Chain grips: noncombustible material | Yes | [14.3.3.3] | |

### 8.4.4 Connectors

| Field | Required | Section | Guidance |
|---|---|---|---|
| Connectors prevent inadvertent separation from wick and handle | Yes | [14.3.4] | Heat-exposed connectors should be heat-resistant. Do not use: plastics, drop forged metal, spring metal [A.14.3.4] |

### 8.4.5 Fire Prop Extinguishment

| Field | Required | Section | Guidance |
|---|---|---|---|
| Extinguishment materials or methods described | Yes | [14.3.6] | In addition to Section 16.3 requirements. Suitable: safety towel, damp cloth, flame-treated cloth, high-heat material [A.14.3.6] |

## 8.5 Fueling Plan

| Field | Required | Section | Guidance |
|---|---|---|---|
| Fueling takes place in approved area | Yes | [14.3.5.1] | Away from unauthorized personnel, well ventilated, free of ignition sources [A.14.3.5.1] |
| All fueling in approved fueling area | Yes | [14.4.2.1] | |
| Fueling area located outside or in approved area | Yes | [14.4.2.4] | |
| Unobstructed path from fueling area to performance area | Yes | [14.4.2.4.1] | |
| Fuel-soaked wicks not moved through audience without at least one spotter | Yes | [14.4.2.4.2] | |
| Audience prohibited within 25 ft (7.6 m) of fueling area | Yes | [14.4.2.4.3] | |
| Smoking and ignition sources prohibited within 25 ft (7.6 m) of fueling area | Yes | [14.4.2.4.4] | |
| Fuel stations attended by operator or spotter until hazard removed | Yes | [14.4.2.2] | |
| Fuel containers and dip buckets sealed when not in use | Yes | [14.4.2.3] | |
| Fire props cooled to ambient temperature before fueling | Yes | [14.3.5.3] | |
| Excess fuel removed and stored per NFPA 1 or NFPA 30 | Yes | [14.3.5.2] | |
| Safety Data Sheets (SDS) available for all fuels and hazardous chemicals | Yes | [14.4] | |
| Fuel stored per NFPA 1 or NFPA 30 | Yes | [14.4.1] | |

## 8.6 Performance Plan

| Field | Required | Section | Guidance |
|---|---|---|---|
| Separation between performer and audience: prevents fuel or flame contact with audience (approved by AHJ) | Yes | [14.5.1] | |
| Performance area free of flammable/combustible materials, OR materials treated with approved fire-retarding chemicals and tested | Yes | [14.5.2] | Approved testing method may be per NFPA 705 [A.14.5.2] |

## 8.7 Performer Clothing

| Field | Required | Section | Guidance |
|---|---|---|---|
| Compliance with Section 7.10 (protective clothing) | Yes | [14.1.3] | Cotton, wool, leather, or similar natural fiber clothing is appropriate [A.14.1.3] |
| If bare skin: illusion of danger is implicit in visual effect | Conditional | [7.10.2] | |

## 8.8 Post-Performance Procedures

| Field | Required | Section | Guidance |
|---|---|---|---|
| All procedures from Sections 14.1–14.5 completed | Yes | [14.6.1] | |
| Fire props cooled to ambient temperature before storage or transportation | Yes | [14.6.2] | |
| Fuel residue removed immediately following performance | Yes | [14.3.5.2.1] | |
| Fuel-soaked waste stored and disposed per manufacturer's instructions, venue, and local regulations | Yes | [14.3.5.2.2] | |

## 8.9 Fire Breather Specific Guidance (Informational)

| Item | Section | Guidance |
|---|---|---|
| Ethanol absorption warning: alcohols may be absorbed through mouth leading to possible intoxication | [A.14.1.1.1] | Multiple performances should be spaced appropriately to ensure sobriety |
