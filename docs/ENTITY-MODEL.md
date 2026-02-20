# Entity Model Overview

## Data Model Diagram

```
SUBMISSION (Production/Event)
├── PRODUCTION INFO (one per submission)
│   └── Installation Classification (Temporary or Permanent)
├── SITE PLAN (reusable, one or more per submission)
│   ├── Outdoor Additions
│   └── Indoor Additions
├── PERSONNEL
│   ├── Person Records (reusable) ──────── saved once, assigned to roles
│   │   └── Competency documents / substance acknowledgment
│   └── Role Assignments (per submission)
│       ├── Flame Effect Operator(s)
│       ├── Assistants
│       ├── Spotters (fire performance)
│       └── Standby Fire Safety Personnel
│
├── ══════════════════════════════════════════════════════════
│   CORE ENTITIES (at least one required per submission)
│   ══════════════════════════════════════════════════════════
│
├── FLAME EFFECTS (zero or more — apparatus-based, Chapter 9)
│   ├── Effect Identity & Classification
│   ├── Fuel Specification ─────────────── references Global SDS Library
│   │   ├── Gaseous Fuel Fields
│   │   ├── Liquid Fuel Fields
│   │   ├── Prepackaged Single-Use Fuel Fields
│   │   └── Gel / Solid Fuel Fields
│   ├── Appliance / Device Description ─── design drawings via Active Storage
│   ├── Control System Description
│   │   ├── Emergency Stop Plan
│   │   ├── Fuel Management
│   │   ├── Enable Sequence
│   │   ├── Arming Procedure
│   │   └── Firing Procedure
│   ├── Hazard Area Definition
│   ├── Post-Operation Securing
│   └── Testing & Evaluation Records ──── test docs via Active Storage
│
├── FIRE PERFORMANCES (zero or more — performer-based, Chapter 14)
│   ├── Performers ─────────────────────── linked via Role Assignments (Entity 2)
│   ├── Safety Personnel (Spotters) ────── linked via Role Assignments (Entity 2)
│   ├── Fire Props
│   ├── Fueling Plan ───────────────────── references Global SDS Library
│   ├── Performance Plan
│   └── Post-Performance Procedures
│
│   ══════════════════════════════════════════════════════════
├── PROCEDURES (each sub-entity independently reusable)
│   ├── Operating Procedures ←────────────┐
│   ├── Rehearsal / Pre-Show Procedures ──┤
│   ├── Show Operations ──────────────────┤
│   ├── Post-Show Procedures ─────────────┼── each can be saved
│   ├── Emergency Response Procedures ────┤   and reused across
│   ├── Maintenance Procedures ───────────┤   submissions
│   ├── Housekeeping ─────────────────────┤
│   └── Protective Clothing ──────────────┘
├── FIRE PROTECTION PLAN
│   ├── Fire Extinguisher Plan (Temporary) ── reusable
│   ├── Fire Hazards Evaluation (Permanent)
│   └── Standby Personnel
├── HOLDING / STORAGE AREAS
├── REVIEW & COORDINATION RECORDS
├── INSPECTION SCHEDULE
│   ├── Temporary: Daily, Weekly/Monthly
│   └── Permanent: Daily, Monthly, Quarterly, Annual
│
└── GLOBAL SDS LIBRARY (shared across all users and submissions)
    └── SDS records referenced by Flame Effects and Fire Performances
```

## Entity Relationships

| Entity | Cardinality | Relationship |
|---|---|---|
| Production/Event → Flame Effect | 1 : 0..many | Zero or more flame effects per submission |
| Production/Event → Fire Performance | 1 : 0..many | Zero or more fire performances per submission |
| Production/Event → Site Plan | 1 : 1..many | One or more site plans per submission; site plans are reusable |
| Production/Event → Person (via role assignment) | 1 : many | Reusable person records assigned to roles; same person can have multiple roles |
| Production/Event → Procedure (each type) | 1 : 0..many | Zero or more of each procedure sub-entity; each independently reusable |
| Production/Event → Fire Protection Plan | 1 : 1 | One fire protection plan per submission |
| Production/Event → Holding/Storage | 1 : many | One or more holding/storage areas |
| Production/Event → Review/Coordination | 1 : 1 | One review record per submission |
| Production/Event → Inspection Schedule | 1 : 1 | One schedule, type determined by installation classification |
| Flame Effect → Fuel Specification | 1 : 1 | Each effect has one primary fuel type |
| Flame Effect → SDS (global library) | 1 : 1..many | Each effect references one or more SDS records for its fuels |
| Flame Effect → Control System | 1 : 1 | Each effect describes its control system |
| Flame Effect → Design Drawings | 1 : 1..many | Stored on effect via Active Storage |
| Flame Effect → Test Records | 1 : 1..many | Stored on effect via Active Storage |
| Fire Performance → SDS (global library) | 1 : 1..many | Each performance references SDS records for its fuels |
| Fire Performance → Performers | 1 : many | Linked via Role Assignments (Entity 2) |
| Fire Performance → Spotters | 1 : many | At least one; linked via Role Assignments (Entity 2) with Fire Performance FK |
| Person → Competency Documents | 1 : 0..many | Stored on person via Active Storage |

**Note:** A submission must include at least one Flame Effect OR at least one Fire Performance. Both can be included.

## Reusability

The following entities are designed to be **saved independently** and reused across multiple submissions:

- **Flame Effect** (Entity 3) — apparatus-based effects with control systems (Chapter 9); an artist's saved effect can be included in multiple event submissions. Design drawings and test records travel with the effect.
- **Fire Performance** (Entity 8) — performer-based effects with props/wicks (Chapter 14); a performer's saved routine can be included in multiple event submissions
- **Personnel** (Entity 2) — person records are saved once and assigned to roles per submission via Role Assignment records (Entity 2.2); the same person can hold multiple roles (e.g., operator + spotter). Competency documents are stored on the person record.
- **Site Plan** (Entity 4) — site plans can be reused across submissions for the same venue; diagrams stored via Active Storage
- **Procedures** (Entity 5) — each sub-entity is independently reusable:
  - Operating Procedures
  - Rehearsal / Pre-Show Procedures
  - Show Operations
  - Post-Show Procedures
  - Emergency Response Procedures
  - Maintenance Procedures
  - Housekeeping
  - Protective Clothing

**Entity 3 and Entity 8 are peer-level core entities.** Both are reusable, and a submission can include either or both types.

## Global Shared Data

- **SDS Library** (Entity 9.1) — Safety Data Sheets are stored once globally and shared across all users and submissions. One SDS per substance. The system pre-populates common SDS sheets and users can add more. Flame Effects and Fire Performances reference SDS records from this library.

## Per-Submission Data

The following entities are **per-submission** and not typically reused:

- Production/Event (Entity 1)
- Fire Protection Plan (Entity 6) — except Fire Extinguisher Plan (§6.2), which is reusable
- Holding/Storage (Entity 7)
- Review/Coordination (Entity 10)
- Inspection Schedule (Entity 11)

## Attachment Storage

Entity 9 defines **attachment requirements** rather than being a standalone data entity. Attachments are stored directly on their parent entities via Active Storage:

| Attachment Type | Stored On | Reusable? |
|---|---|---|
| SDS sheets | Global SDS Library | Yes (shared across all users) |
| Design drawings / manuals | Flame Effect (Entity 3) | Yes (travels with effect) |
| Test records | Flame Effect (Entity 3) | Yes (travels with effect) |
| Competency documents | Person Record (Entity 2) | Yes (travels with person) |
| Site plan diagrams | Site Plan (Entity 4) | Yes (travels with site plan) |
| Fire hazards evaluation | Submission (Entity 1) | No |
| Manufacturer instructions | Submission (Entity 1) | No |
