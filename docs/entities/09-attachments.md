# Entity 9: Attachment Requirements

This entity defines **what attachments are required** for each entity at document generation time. It is not a standalone data entity — attachments are stored on the entities that own them, or in the global SDS library.

## 9.1 Global SDS Library

Safety Data Sheets are maintained as a **shared global library**. One copy of each SDS is stored in the system and can be referenced by any flame effect or fire performance across any user or submission.

- The system can pre-populate common SDS sheets (e.g., propane, isopropyl alcohol, ethanol, white gas)
- Users can add new SDS sheets to the library
- Each SDS is identified by substance name and version/date
- Flame Effects (Entity 3) and Fire Performances (Entity 8) reference SDS records from this library

| Field | Required | Notes |
|---|---|---|
| Substance name | Yes | Identifies the fuel/material |
| SDS document (uploaded file) | Yes | Stored via Active Storage |
| SDS date / revision | Yes | Used to verify currency |
| Manufacturer / supplier | Recommended | For traceability |

## 9.2 Entity-Level Attachments

Attachments are stored directly on their parent entity via Active Storage. They travel with the entity when it is reused across submissions.

### Flame Effect (Entity 3)

| Attachment | Required | Section | Notes |
|---|---|---|---|
| SDS references (from global library) | Yes | [5.3.2(6)] | One per distinct fuel used by this effect |
| Design drawings, manuals, or written descriptions | Yes | [6.1.1] | Stored on the effect record |
| Testing and evaluation documentation | Yes | [7.1.1], [15.1.2] | Stored on the effect record |
| Pressure test records | Conditional | [15.2] | If piping is used |
| Flame retardant documentation | Yes | [5.3.2(7)] | For combustible construction materials |

### Fire Performance (Entity 8)

| Attachment | Required | Section | Notes |
|---|---|---|---|
| SDS references (from global library) | Yes | [14.4] | One per distinct fuel used in performance |

### Person Record (Entity 2)

| Attachment | Required | Section | Notes |
|---|---|---|---|
| Competency evidence: uploaded documents (certificates, licenses, training records) OR signed self-attestation of competency through experience and training | Conditional | [8.1.2] | Required for operators |

### Site Plan (Entity 4)

| Attachment | Required | Section | Notes |
|---|---|---|---|
| Site plan diagram(s) | Yes | [5.3.2(5)] | Uploaded drawings/diagrams |

### Submission-Level (Entity 1)

| Attachment | Required | Section | Notes |
|---|---|---|---|
| Fire hazards evaluation report | Conditional | [16.2.1] | Permanent installations, when AHJ requires |
| Appliance manufacturer instructions | Conditional | [11.1.8] | Prepackaged single-use fuel |
| Prepackaged receptacle disposal instructions | Conditional | [11.1.10] | Prepackaged single-use fuel |

## 9.3 Validation Rules

At document generation time, the system verifies:

| Rule | Section | Source |
|---|---|---|
| Every distinct fuel across all effects and performances has an SDS reference from the global library | [5.3.2(6)] | Entity 3, Entity 8 → SDS Library |
| Every flame effect has design drawings or written descriptions | [6.1.1] | Entity 3 |
| Every flame effect has testing documentation | [7.1.1], [15.1.2] | Entity 3 |
| Flame retardant documentation present for effects with combustible construction materials | [5.3.2(7)] | Entity 3 |
| Site plan diagram(s) uploaded | [5.3.2(5)] | Entity 4 |
| Operators have competency documents or declaration on file | [8.1.2] | Entity 2 |
| If piping: pressure test records present | [15.2] | Entity 3 |
| If permanent: fire hazards evaluation report present (when required) | [16.2.1] | Entity 1 |
| If prepackaged fuel: manufacturer instructions present | [11.1.8] | Entity 1 |
