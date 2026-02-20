# Entity 3: Individual Flame Effect

A reusable entity for apparatus-based flame effects. Artists save one record per distinct flame effect device/appliance. Multiple effects can be included in a single submission.

**Peer entity:** Entity 8 (Fire Performance) covers performer-based effects with props/wicks. Each submission is one type — either flame effects or fire performances, not mixed.

**Note:** Chapter 9 control system requirements apply to flame effects but do NOT apply to fire performances (Chapter 14). [9.1]

## 3.1 Effect Identity & Classification

| Field | Required | Section | Guidance |
|---|---|---|---|
| Effect name / identifier (user-defined) | Recommended | — | For internal tracking and reference in site plan |
| Flame effect classification (Group I–VII) | Yes | [5.3.2(4)] | See classification table below |
| Narrative description of the flame effect | Yes | [5.3.2(5)(a)] | Plain-language description of what the effect does |
| Control type: Automatic or Manual | Yes | [3.3.13.1], [3.3.13.3] | Drives control system requirements (Chapter 9) |
| Portable: Yes/No | Yes | [3.3.13.4] | If yes, requires storage and security plan [7.11.2] |
| Is this a hybrid flame effect? (Y/N) | Yes | [3.3.13.2], [5.2.1.1] | If yes, must identify NFPA 160 vs 1126 portions |
| If hybrid: description of portions governed by NFPA 160 | Conditional | [5.2.2.3] | |
| If hybrid: description of portions governed by NFPA 1126 | Conditional | [5.2.2.3] | |

### Classification Reference (for form selection help)

| Group | Attended? | Control | Typical Examples | Section |
|---|---|---|---|---|
| I | Yes | Manual | Hand-held torches, lighters, candles, juggling batons, fire rings | [3.3.20.1], [A.3.3.20(1)] |
| II | No | Unattended, outdoor | Unattended torches, burning urns, small outdoor flames | [3.3.20.2], [A.3.3.20(2)] |
| III | Yes | Temporary, specific production | Traveling shows, concerts, limited-duration special events, single-venue events | [3.3.20.3], [A.3.3.20(3)] |
| IV | No | Permanent, no main show control | Burning cabin, bonfire, large flaming braziers for atmosphere | [3.3.20.4], [A.3.3.20(4)] |
| V | No (tech) | Main show control, no full-time technician | Simulated explosions in theme attractions | [3.3.20.5], [A.3.3.20(5)] |
| VI | Yes | Main show control + technical director, cast in proximity | Live-action stunt shows | [3.3.20.6], [A.3.3.20(6)] |
| VII | Varies | Unique | Does not fit other classifications (e.g., illusion effects) | [3.3.20.7], [A.3.3.20(7)] |

---

## 3.2 Fuel Specification

| Field | Required | Section | Guidance |
|---|---|---|---|
| Primary fuel type | Yes | [3.3.16] | Select: Gaseous, Liquid, Prepackaged Single-Use, Gel, or Solid |
| Specific fuel name / product | Yes | [5.3.2(5)(e)] | |
| Estimated fuel consumption (quantity + time period) | Yes | [5.3.2(5)(e)] | |
| Safety Data Sheet (SDS) — current | Yes | [5.3.2(6)] | Reference from global SDS library (Entity 9.1); one per distinct fuel |

### 3.2.1 Gaseous Fuel Additional Fields (Chapter 10)

| Field | Required | Section | Guidance |
|---|---|---|---|
| Gas piping compliance: conforms to applicable gas codes | Yes | [10.1.1] | NFPA 54 for natural gas, NFPA 58 for LP-Gas, or equivalent |
| Minimum tank size and basis for sizing (surface area for fuel delivery rate) | Yes | [10.1.2] | Minimum determined by surface area required to prevent reduced delivery during effect |
| Purge cycle description: purge before each ignition attempt, duration per manufacturer specification or as acceptable to AHJ | Yes | [10.1.3] | Required for gaseous fuel systems |
| If LPG: confirmation that container is positioned with relief valve in communication with vapor space | Conditional | [9.2.2.3] | Required for LPG. See [A.9.2.2.3] — liquid relief creates significantly greater hazard |

### 3.2.2 Liquid Fuel Additional Fields (Chapter 12)

| Field | Required | Section | Guidance |
|---|---|---|---|
| Ignition source type (appropriate for fuel type and pressures) | Yes | [12.1.2] | |
| Confirmation: all components compatible with fuel and operating pressures | Yes | [12.1.3] | |
| Container design standard (ASME / DOT / EU PED) | Yes | [12.1.4(1)] | For containers storing or using fuel under pressure |
| Confirmation: all container materials compatible with liquid fuel | Yes | [12.1.4(2)] | |
| Rated working pressure of containers | Yes | [12.1.4(3)] | |
| Overpressure protection description | Yes | [12.1.4(4)] | Must handle maximum possible overpressure event |
| Manual shutoff valve locations: fill, charging, and burner output | Yes | [12.1.4(5)] | |
| Confirmation: all valves closed at time of transport | Yes | [12.1.4(6)] | |
| Spill containment plan for refilling | Yes | [12.1.6] | Subject to AHJ approval |
| Approved refilling/pressurizing location for refillable containers | Yes | [12.1.7] | |
| If external pressure source: method of isolating pressure source from system | Conditional | [12.1.8] | |
| Manual method for controlled depressurization of containers | Conditional | [12.1.8.1] | Required if external pressure source |
| Method to remove unused liquid fuel from system | Yes | [12.1.9] | |
| If fuel pressure outside normal parameters: pressure supervisory control system description | Conditional | [12.1.5] | |

### 3.2.3 Prepackaged Single-Use Fuel Receptacle Additional Fields (Chapter 11)

| Field | Required | Section | Guidance |
|---|---|---|---|
| Confirmation: fuel is expressly manufactured for burner/combustion applications AND specified by the appliance manufacturer | Yes | [11.1.2] | Paint, starting fluid, air fresheners, lubricants, hairsprays, insecticides are prohibited [A.11.1.2] |
| Quantity of receptacles supplying the appliance: limited to manufacturer's design specification | Yes | [11.1.3] | |
| Backflow prevention: means to prevent backflow from appliance at each receiver | Yes | [11.1.4] | |
| Protection: receptacles protected from direct heat of flame effect | Yes | [11.1.5] | |
| Inspection: receptacles inspected for damage or leakage prior to installation | Yes | [11.1.6] | |
| Confirmation: damaged or leaking cylinders will not be used | Yes | [11.1.6.1] | |
| Expiration date check: receptacles with expiration dates will not be used after expiration | Yes | [11.1.7] | |
| Confirmation: handled and used per appliance manufacturer's instructions | Yes | [11.1.8] | |
| Confirmation: receptacles will not be refilled | Yes | [11.1.9] | |
| Disposal plan: in accordance with manufacturer's instructions, venue, and local regulations | Yes | [11.1.10] | |

**Definition reference for form help text:**
Prepackaged single-use fuel receptacles are non-refillable, factory-filled, typically classified as UN 2037 or UN 1950, limited to <34 oz (1000 ml), with protected internal self-closing valves. Built to DOT 2P, 2Q, or 2Q1 standards or EU PED. [3.3.27], [A.3.3.27]

### 3.2.4 Gel and Solid Fuel Additional Fields (Chapter 13)

| Field | Required | Section | Guidance |
|---|---|---|---|
| Surface, holder, or device: constructed from noncombustible material | Yes | [13.1.1] | Must prevent unintended fuel migration to undesired locations |
| Means of extinguishment description | Yes | [13.1.2] | e.g., fire extinguisher, snuff box, fire blanket, or other AHJ-approved method [A.13.1.2] |

**Definition reference for form help text:**
Gel and solid fuels include gelled alcohol, colored flame gels and pastes, handheld fuel-pellet-based torches, lycopodium powder, wood, coal, organic materials, and finely ground dusts/powders. Most fall into Group I effects. [A.13.1], [3.3.16.3], [A.3.3.16.3]

---

## 3.3 Appliance / Device Description

| Field | Required | Section | Guidance |
|---|---|---|---|
| Drawings, manuals, or written descriptions of the device | Yes | [6.1.1] | Stored on effect record via Active Storage; must describe type of item |
| Performance specifications of the flame effect produced | Yes | [6.1.1] | |
| Flame effect burner description (size and configuration of flames) | Recommended | [3.3.15] | |
| Min/max ambient temperature rating (if critical to operation) | Conditional | [7.6.1.1] | Manufacturer must specify if critical. Fuels may not properly ignite outside specified ranges [A.7.6.1.1] |
| Documentation that combustible materials used in construction are rendered flame retardant | Yes | [5.3.2(7)] | |

---

## 3.4 Control System Description

**Note:** Chapter 9 requirements do NOT apply to Chapter 14 (Fire Performers). [9.1] Fire performer effects use Entity 8 requirements instead.

Per [9.1.4.2]: *"The flame effect plan submitted for approval to the AHJ shall indicate the means of providing for these requirements."*

### 3.4.1 General Control System Info

**Note:** This section applies to flame effects only. Fire performances (Entity 8) do not use Chapter 9 control systems.

| Field | Required | Section | Guidance |
|---|---|---|---|
| Description of how control system prevents accidental firing and unintentional fuel release | Yes | [9.1.1] | |
| For automatic systems: description of removable activator, keyswitch, or coded arming system | Yes | [9.1.2] | Must require deliberate application of control power AND enabling/arming |
| Control system component listing status (listed devices, or if unlisted: approved devices) | Yes | [9.1.5], [9.1.5.1] | |
| Description of physical protection of control components against damage and tampering | Yes | [9.1.6] | Must also be accessible for service and maintenance |
| Control system attendance plan: not left unattended while connected to fuel unless disconnected from power or de-energized by removable activator/keyswitch/coded arming | Yes | [9.1.3] | |
| Means of rendering system inoperative when not in use | Yes | [7.11.1] | Security requirement |
| If portable: storage and security plan when not in use | Conditional | [7.11.2] | |

### 3.4.2 Emergency Stop Plan

The plan must specify one of two approaches [9.2.1.1]:

**Option A — Manual Effects [9.2.1.4]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Plan for emergency stop via one or more of: manual fuel shutoff valve(s), manual turn-off of control power, fire containment devices, other devices acceptable to AHJ | Yes | [9.2.1.4] | |

**Option B — Automatic Effects [9.2.1.5]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Description of how system cannot operate unless emergency stop is reset | Yes | [9.2.1.5(1)] | |
| Description of how emergency stop brings system to safe state | Yes | [9.2.1.5(2)] | |
| Confirmation: emergency stop requires manual reset | Yes | [9.2.1.5(3)] | |
| Description of both manual and automatic actuation (including power failure) | Yes | [9.2.1.5(4)] | |
| Confirmation: emergency stop is fail-safe | Yes | [9.2.1.5(5)] | |
| Description of monitored conditions that auto-actuate emergency stop | Yes | [9.2.1.5(6)] | Examples [A.9.2.1.5(6)]: loss of purge airflow, loss of ventilation, flammable gas detection, loss of vacancy proof, detection of unsafe person/environment/equipment, wind conditions, system errors |
| Location(s) of manual emergency stop control stations | Yes | [9.2.1.6.1] | Must be clearly identified and accessible |
| Confirmation: manual stations maintain actuated state until manually reset | Yes | [9.2.1.6.1.1] | |

**For both options:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Description of interrelated system safety considerations (allied equipment, proximate equipment) | Yes | [9.2.1.2] | |
| If interrelated hazards exist: description of direct validated means of confirming status before enable/trigger | Conditional | [9.2.1.3] | |

### 3.4.3 Fuel Management

| Field | Required | Section | Guidance |
|---|---|---|---|
| Description of how fuel supply is available only during operation | Yes | [9.2.2.1] | |
| Quantity limitation: fuel supplied limited to amount necessary for operation | Yes | [9.2.2.2] | |

**If fuel is delivered through a central distribution system [9.2.2.4.1]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Manual fuel shutoff valve location (accessible, at point of delivery, upstream of all other components) | Yes | [9.2.2.4.1(1)] | |
| Low fuel pressure supervision (if low pressure could cause malfunction) | Conditional | [9.2.2.4.1(2)(a)] | |
| High fuel pressure supervision (if high pressure could cause malfunction) | Conditional | [9.2.2.4.1(2)(b)] | |
| Supervisor station description: location (downstream of manual shutoff), shutoff function, held open by maintained signal | Yes | [9.2.2.4.1(3)] | See [A.9.2.2.4.1(3)] for detailed examples including dual safety valves and zone stations |
| Supervisor station seat-tightness test method | Yes | [9.2.2.4.2] | |

**Effect Valve (per effect) [9.2.2.5]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Automatic fuel shutoff valve (effect valve) installed upstream of burner | Yes | [9.2.2.5.1] | |
| Confirmation: shuts off all fuel to burner when closed | Yes | [9.2.2.5.2] | |
| Confirmation: opened only at time of firing, held by maintained signal | Yes | [9.2.2.5.3] | |
| Confirmation: closes on loss of hold-open signal | Yes | [9.2.2.5.4] | |

**If using fuel accumulators [9.2.2.6]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Accumulator tank design standard (ASME / DOT / EU PED) | Yes | [9.2.2.6(1)(a)] | For applications outside US, equivalent national standards permitted [A.9.2.2.6(1)(a)] |
| Volume of fuel stored: no more than required to produce effect | Yes | [9.2.2.6(2)] | See [A.9.2.2.6(2)] for important nuance: round fireballs, rapid bursts, and fuel-rich atmosphere maintenance may require excess fuel |
| Manual fuel shutoff valve at accumulator inlet | Yes | [9.2.2.6(3)] | |
| Accumulator charge valve at inlet | Yes | [9.2.2.6(4)] | |
| Charging timing: as close to arming/firing as practical | Yes | [9.2.2.6(5)] | |
| Safe fuel removal method: fixed = permanently installed path to safe discharge point; portable = movable to safe location | Yes | [9.2.2.6(6)] | |
| Confirmation: no mixing of air/oxidizer with fuel inside accumulator | Yes | [9.2.2.6(7)] | |

### 3.4.4 Enable Sequence

| Field | Required | Section | Guidance |
|---|---|---|---|
| Prescribed sequence of operations for enabling (per the plan) | Yes | [9.2.3] | |
| Description of control power activation as first step | Yes | [9.2.3.2] | See [A.9.2.3.2] for guidance on multiple control power modes |
| Fuel supply and auxiliary services turn-on sequence (after control power) | Yes | [9.2.3.3.1] | Includes compressed air, oxidizers, additives, etc. |
| Positive confirmation / interlock of fuel supply and each auxiliary service before continuing enable | Yes | [9.2.3.3.2] | |
| Description of safety interlocks: what they monitor, responses to condition changes | Yes | [9.2.3.4.1] | Examples [A.9.2.3.4]: wind speed/direction, critical temps, opacity, purge airflow, combustion airflow, position indicators, cast position, audience/vehicle position |
| Confirmation: safety interlocks are fail-safe | Yes | [9.2.3.4.2] | |
| If interrelated systems: direct validated means of confirming status before enable | Conditional | [9.2.3.1.1], [9.2.3.1.2] | |

### 3.4.5 Arming Procedure

| Field | Required | Section | Guidance |
|---|---|---|---|
| Description of arming process (manual or automatic, prior to any firing attempt) | Yes | [9.2.4.1] | |
| Monitoring/confirmation method until effect is fired | Yes | [9.2.4.2] | |

**Manual arming [9.2.4.3]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Confirmation that ignition means can be clearly and directly seen by flame effect operator/assistant for entire enable time | Yes | [9.2.4.3.1] | |
| If ignition cannot be seen: description of automatic arming confirmation | Conditional | [9.2.4.3.2] | |

**Automatic arming [9.2.4.4]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Sensor(s) detecting ignition means via characteristic unique to ignition source | Yes | [9.2.4.4] | Examples [A.9.2.4.4]: UV flame detector, IR flame detector, flame rod, thermocouple, other AHJ-acceptable devices |
| Confirmation: sensors operate in installed environment | Yes | [9.2.4.5] | |
| False sensing prevention: cannot report presence due to other ignition devices, pilots, or effects | Yes | [9.2.4.7.1] | |
| False sensing prevention: cannot report due to non-fire devices (spark effects, UV sources, heat without flame) | Yes | [9.2.4.7.2] | |

**If cast members or moving set pieces in hazard area before/after arming [9.2.4.6]:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Description of PME (Permissive Manual Enable) required during arming and firing | Yes | [9.2.4.6] | See [A.9.2.5.4] for detailed PME design guidance |

### 3.4.6 Firing Procedure

| Field | Required | Section | Guidance |
|---|---|---|---|
| Confirmation: effects only fired after confirmed armed, enable/arm complete, hazard area clear | Yes | [9.2.5.1] | |
| Procedure if arming confirmation lost or hazard area becomes unsafe: immediate termination and securing | Yes | [9.2.5.2] | |
| Description of how control system prevents firing except on deliberate positive action or verified auto sequence | Yes | [9.2.5.5] | |

**Manual firing:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Flame effect operator responsibility to verify enable, arming, and hazard area safety prior to firing | Yes | [9.2.5.5.1] | |

**Automatic firing:**

| Field | Required | Section | Guidance |
|---|---|---|---|
| Operating power originates from control system, supplied only under supervision of all limits/interlocks/monitoring | Yes | [9.2.5.5.2.1] | |
| All effect valves opened only by maintained firing signal, auto-close on loss of signal | Yes | [9.2.5.5.2.2] | |

---

## 3.5 Hazard Area Definition

| Field | Required | Section | Guidance |
|---|---|---|---|
| Definition of area made hazardous by operation of the effect | Yes | [3.3.2.1], [5.3.2(5)(c)] | |
| Definition of accessible hazard area (accessible without additional means) | Yes | [3.3.2.1.1] | |
| Monitoring method: area confirmed clear before firing, OR access supervised by automatic means, OR area made inaccessible | Yes | [9.2.5.3.1] | |
| Other safety-critical parameters monitored or supervised | Yes | [9.2.5.3.2] | |
| Supervision method: direct observation by flame effect operator/assistant for entire enable/fire time | Yes | [9.2.5.4.1] | |
| If hazard area cannot be seen by flame effect operator: alternative monitoring means (approved by AHJ) | Conditional | [9.2.5.4.2] | |
| If all areas of concern cannot be seen by single flame effect operator: number and placement of enable buttons | Conditional | [9.2.5.4.3.1] | |
| Enable buttons monitored separately and verified by control system | Conditional | [9.2.5.4.3.2] | |

---

## 3.6 Post-Operation Securing (Per Effect)

| Field | Required | Section | Guidance |
|---|---|---|---|
| Procedure for removing enable and arming signals after firing | Yes | [9.2.6] | |
| Procedure for securing all fuel and auxiliary services (without going through the normal fire sequence) | Yes | [9.2.6] | |
| Visual inspection of all hazard areas before confirming system secure | Yes | [9.2.6] | |

---

## 3.7 Testing & Evaluation Records

| Field | Required | Section | Guidance |
|---|---|---|---|
| Documentation that effect was tested to verify operation per design | Yes | [7.1.1], [15.1.1] | Stored on effect record via Active Storage |
| Documentation that effect was evaluated: no hazardous exposure to spectators, performers, support personnel, or flame effect operator | Yes | [7.1.2] | Skin surface temp should not exceed 111°F (44°C) as measured by IR thermometer [A.7.1.2] |
| Testing documentation from manufacturer or fabricator | Yes | [15.1.2] | |
| Inspection interval acceptable to AHJ | Yes | [7.1.3] | Effects must be inspected and retested on AHJ-acceptable interval |
| Third-party testing documentation (if applicable, acceptable to AHJ) | Conditional | [7.1.4] | |
| If piping: pressure test results at no less than system operating pressure | Conditional | [15.2.1] | |
| If piping: recorded system pressures, temperature, and atmospheric pressure | Conditional | [15.2.2.1] | |
| If piping reassembled from subassemblies: leak test at reconnected joints | Conditional | [15.2.2.2] | Using noncorrosive leak-detecting solution or AHJ-acceptable means |
| Component temperature verification: does not exceed rated limits during sustained operation | Yes | [15.3.1] | |
| Component temperatures determined at maximum design cycle rate | Yes | [15.3.2] | |
| Temperatures observed until maximum or stable reading attained | Yes | [15.3.2.1], [15.3.2.4] | |
| Confirmation: attained temperatures do not exceed rated temperatures | Yes | [15.3.2.2] | |
| Combustible material temperatures: do not exceed 117°F (47.2°C) above ambient after equilibrium | Yes | [15.3.2.3] | |

**Note:** The AHJ shall be permitted to witness the testing of any flame effect. [7.1.5]
