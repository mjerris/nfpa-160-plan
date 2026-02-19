# Entity Model Overview

## Data Model Diagram

```
SUBMISSION (Production/Event)
├── PRODUCTION INFO (one per submission)
│   └── Installation Classification (Temporary or Permanent)
├── SITE PLAN (one per submission, includes diagrams)
│   ├── Outdoor Additions
│   └── Indoor Additions
├── PERSONNEL
│   ├── Responsible Party
│   ├── Flame Effect Operator(s)
│   ├── Assistants / Support Personnel
│   ├── Spotters (fire performance)
│   └── Standby Fire Safety Personnel
├── FLAME EFFECTS (one or more per submission)
│   ├── Effect Identity & Classification
│   ├── Fuel Specification
│   │   ├── Gaseous Fuel Fields
│   │   ├── Liquid Fuel Fields
│   │   ├── Prepackaged Single-Use Fuel Fields
│   │   └── Gel / Solid Fuel Fields
│   ├── Appliance / Device Description
│   ├── Control System Description
│   │   ├── Emergency Stop Plan
│   │   ├── Fuel Management
│   │   ├── Enable Sequence
│   │   ├── Arming Procedure
│   │   └── Firing Procedure
│   ├── Hazard Area Definition
│   └── Post-Operation Securing
├── FIRE PERFORMANCE (Chapter 14 — optional entity)
│   ├── Performer Records
│   ├── Safety Personnel (Spotters)
│   ├── Fire Props
│   ├── Fueling Plan
│   ├── Performance Plan
│   └── Post-Performance Procedures
├── PROCEDURES (reusable across submissions)
│   ├── Operating Procedures
│   ├── Rehearsal / Pre-Show Procedures
│   ├── Show Operations
│   ├── Post-Show Procedures
│   ├── Emergency Response Procedures
│   ├── Maintenance Procedures
│   ├── Housekeeping
│   └── Protective Clothing
├── FIRE PROTECTION PLAN
│   ├── Fire Extinguisher Plan (Temporary)
│   ├── Fire Hazards Evaluation (Permanent)
│   └── Standby Personnel
├── HOLDING / STORAGE AREAS
├── REQUIRED ATTACHMENTS / DOCUMENTS
├── REVIEW & COORDINATION RECORDS
└── INSPECTION SCHEDULE
    ├── Temporary: Daily, Weekly/Monthly
    └── Permanent: Daily, Monthly, Quarterly, Annual
```

## Entity Relationships

| Entity | Cardinality | Relationship |
|---|---|---|
| Production/Event → Flame Effect | 1 : many | A submission contains one or more flame effects |
| Production/Event → Site Plan | 1 : 1 | One site plan per submission |
| Production/Event → Personnel | 1 : many | One or more operators, assistants, spotters |
| Production/Event → Procedures | 1 : many | Multiple procedure types per submission |
| Production/Event → Fire Protection Plan | 1 : 1 | One fire protection plan per submission |
| Production/Event → Fire Performance | 1 : 0..1 | Optional; included when fire performers are part of the production |
| Production/Event → Holding/Storage | 1 : many | One or more holding/storage areas |
| Production/Event → Attachments | 1 : many | Multiple required documents |
| Production/Event → Review/Coordination | 1 : 1 | One review record per submission |
| Production/Event → Inspection Schedule | 1 : 1 | One schedule, type determined by installation classification |
| Flame Effect → Fuel Specification | 1 : 1 | Each effect has one primary fuel type |
| Flame Effect → Control System | 1 : 1 | Each effect describes its control system |
| Fire Performance → Performers | 1 : many | Multiple performers per fire performance |
| Fire Performance → Spotters | 1 : many | At least one spotter required |
| Fire Performance → Fire Props | 1 : many | Multiple props per performance |

## Reusability

The following entities are designed to be **saved independently** and reused across multiple submissions:

- **Flame Effect** (Entity 3) — an artist's saved effect can be included in multiple event submissions
- **Personnel** (Entity 2) — operator profiles, assistant records
- **Procedures** (Entity 5) — operating, emergency, maintenance procedures
- **Fire Performance** (Entity 8) — performer records, prop specifications

The following entities are **per-submission** and not typically reused:

- Production/Event (Entity 1)
- Site Plan (Entity 4)
- Fire Protection Plan (Entity 6)
- Holding/Storage (Entity 7)
- Attachments (Entity 9)
- Review/Coordination (Entity 10)
- Inspection Schedule (Entity 11)
