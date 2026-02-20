# Entity 2: Personnel

Personnel records are **reusable person profiles**. Artists save individual people once, then assign them to roles within each submission. The same person can be assigned to multiple roles (e.g., an operator who is also a spotter).

## 2.1 Person Record (Reusable)

Each person is saved once with their core information:

| Field | Required | Section | Guidance |
|---|---|---|---|
| Name | Yes | [5.3.2(8)] | |
| Date of birth / age confirmation | Yes | [8.4] | Used to verify age requirements for specific roles |
| Competency documents (uploaded files: certificates, licenses, training records) | Conditional | [8.1.2] | Required if person will be assigned as operator; stored via Active Storage |
| Substance abuse acknowledgment signed (date tracked) | Conditional | [8.3] | Required if person will be assigned as operator or performer |

## 2.2 Role Assignment Record (Per Submission)

Each role assignment is a join record linking a saved person to a role within a specific submission. One person can have multiple role assignments in the same submission (e.g., operator and spotter).

| Field | Required | Notes |
|---|---|---|
| Person (FK → Person Record) | Yes | Which saved person is being assigned |
| Submission (FK → Entity 1) | Yes | Which submission this assignment belongs to |
| Role | Yes | One of: Flame Effect Operator, Assistant, Spotter, Standby Fire Safety Personnel |
| Fire Performance (FK → Entity 8) | Conditional | Required for Spotter role; identifies which performance they are assigned to |

**Note:** At least one person must be assigned as Flame Effect Operator per submission.

### Assignment UI Confirmations

When assigning a person to a role, the UI presents role-specific confirmations that must be acknowledged before the assignment is saved. These are acceptance gates in the assignment flow, not stored data fields:

- **Flame Effect Operator:** Confirm familiarity with this submission's effects
- **Assistant:** Confirm this person will work under operator supervision
- **Spotter:** Confirm training in flame extinguishing, reaction time, equipment control, and audience control
- **Standby Fire Safety Personnel:** Confirm working knowledge of supplemental equipment

## 2.3 Role-Specific Validation Rules

These rules are checked at document generation time by validating the Person Record against the assigned role.

### Flame Effect Operator

| Validation | Section | Source |
|---|---|---|
| Age ≥ 21 years (from Person Record date of birth) | [8.4] | Person Record |
| At least one competency document on file | [8.1.2] | Person Record |
| Substance abuse acknowledgment signed | [8.3] | Person Record |

**Operator Responsibilities Note (for system guidance text):**
The operator is responsible for storage, setup, operations, teardown of all flame effect materials, devices, equipment, systems, and supervision of assistants. [8.2]

### Assistant

| Validation | Section | Source |
|---|---|---|
| At least one Flame Effect Operator also assigned in same submission | [3.3.4] | Role Assignment |

Assistants may be under 21. [A.8.4]

### Spotter (Fire Performance)

Required when fire performance (Entity 8) is included. See [08-fire-performance.md](08-fire-performance.md), Section 8.3 for full spotter requirements.

| Validation | Section | Source |
|---|---|---|
| Assigned to a specific fire performance in this submission | [14.2.1.3] | Role Assignment |

### Standby Fire Safety Personnel

| Validation | Section | Source |
|---|---|---|
| Required if fire hazards evaluation or AHJ requires it | [16.4.1] | Submission context |
| Communication methods documented in operating procedures (Entity 5.1) and emergency response procedures (Entity 5.5) | [16.4.3] | Entity 5 |

## 2.4 Support Personnel Awareness

This applies to all personnel assigned to any role:

| Field | Required | Section | Guidance |
|---|---|---|---|
| Plan for advising all performers and support personnel of hazardous exposure | Yes | [7.5.1] | Must be advised they are exposed to a potentially hazardous situation |
| Confirmation that performers/support personnel participate voluntarily and in performance of duties | Yes | [7.5.2] | Only those familiar and experienced with the effects |
