# Product Brief & Context

## Overview

This project is a **questionnaire-based plan submission tool** for fire artists who use flame effects before audiences. It helps users build complete, NFPA 160-compliant plan documents for submission to their local Authority Having Jurisdiction (AHJ) by walking them through structured forms, saving reusable components, and assembling everything into a final output document.

## Problem Statement

NFPA 160 requires a comprehensive plan submission before flame effects can be used before an audience. The requirements are scattered across 16 chapters and multiple annexes, with significant conditional branching based on fuel type, installation type, control system type, and whether fire performers are involved. For independent fire artists — especially those in the burn/festival community — assembling a complete and compliant plan is a significant barrier. Many artists are technically capable operators but lack familiarity with navigating code documents and translating requirements into structured submissions.

## Target Users

**Primary:** Fire artists and flame effect operators in the burn and festival community who need to submit plans to local fire marshals or other AHJs. These are generally non-technical users relative to code compliance — they understand their equipment and performances but may not know how to structure a formal plan document.

**Secondary:** Event organizers who coordinate flame effect submissions across multiple artists for a single event (e.g., regional burns, festivals, concerts).

**Not the primary target:** Theme park engineers, permanent installation designers, or professional pyrotechnics companies — though the data model supports their use cases as well.

## System Vision

### Core Workflow

1. **Artist creates an account** and begins defining their flame effects, personnel, and procedures as saved records
2. **For each event**, the artist creates a new submission and selects which saved effects, personnel, and procedures apply
3. **The questionnaire system walks them through** any event-specific fields (venue, schedule, site plan, fire protection)
4. **Conditional logic** shows only the fields relevant to their selections (fuel type, installation type, indoor/outdoor, etc.)
5. **Validation rules** check for completeness before allowing document generation
6. **The system generates a plan document** combining all entities into the format required by NFPA 160 Section 5.3
7. **The artist submits** the generated document (plus attachments like SDS sheets and drawings) to the AHJ

### Reusability Model

A key design goal is that artists **define things once and reuse them**. An artist who builds a propane poofer and documents it thoroughly should be able to include that same effect record in submissions for multiple events without re-entering data. Similarly, a fire performer who documents their poi routine can reuse that record across events.

**Reusable across submissions:**
- Entity 3: Individual Flame Effect (apparatus-based effects with control systems — Chapter 9 applies). Design drawings and test records are stored on the effect and travel with it.
- Entity 8: Fire Performance (performer-based effects with props/wicks — Chapter 14 applies)
- Entity 2: Personnel — person records are saved once and assigned to roles per submission via Role Assignment records; the same person can hold multiple roles (e.g., flame effect operator + spotter). Competency documents are stored on the person record.
- Entity 4: Site Plan — reusable for the same venue across submissions; diagrams stored via Active Storage
- Entity 5: Procedures — each sub-entity is independently reusable:
  - Operating Procedures
  - Rehearsal / Pre-Show Procedures
  - Show Operations
  - Post-Show Procedures
  - Emergency Response Procedures
  - Maintenance Procedures
  - Housekeeping
  - Protective Clothing

**Global shared data:**
- Entity 9.1: SDS Library — Safety Data Sheets are stored once globally and shared across all users and submissions. The system pre-populates common SDS sheets; users can add more. Flame Effects and Fire Performances reference SDS records from this library.

**Entity 3 and Entity 8 are peer-level core entities.** Each submission is one type:
- One or more flame effects (Chapter 9), OR
- One or more fire performances (Chapter 14)

Flame effects and fire performances cannot be mixed in a single submission. An artist who needs both must create separate submissions.

**Per-submission (event-specific):**
- Entity 1: Production/Event
- Entity 6: Fire Protection Plan — except Fire Extinguisher Plan (§6.2), which is reusable
- Entity 7: Holding/Storage Areas
- Entity 9: Attachment Requirements — defines what attachments are required per entity; attachments are stored on their parent entities via Active Storage
- Entity 10: Review & Coordination
- Entity 11: Inspection Schedule

### Document Generation

The output is a single assembled plan document that follows the structure defined in [appendices/A-document-generation.md](appendices/A-document-generation.md). The format should be acceptable to AHJs — likely PDF, though the system could also support DOCX or print-formatted HTML. The assembled document must include or reference all attachments (SDS sheets, drawings, test documentation).

## Key Design Decisions

These decisions were made during the initial requirements extraction and should be carried forward:

1. **Entity 3 (Flame Effect) and Entity 8 (Fire Performance) are peer-level core entities, but cannot be mixed in a single submission.** The system supports two distinct types of fire art: apparatus-based flame effects (Chapter 9 control systems) and performer-based fire performance (Chapter 14 props/wicks). Users select one submission type at the start of their workflow. This simplifies conditional logic — all Chapter 9 fields are hidden for fire performance submissions and vice versa. An artist who needs both types must create separate submissions.

2. **Conditional form branching is driven by Appendix C.** The conditional logic map defines every show/hide condition for the questionnaire. When a user selects "Liquid" as their fuel type, only liquid fuel fields appear. When they check "Hybrid = Yes," the NFPA 1126 portion identification fields appear. This keeps the forms from being overwhelming.

3. **Validation runs at submission and document generation time** (Appendix B), not during data entry. Artists should be able to save partial records and come back to them. Validation is enforced when an artist submits for review (Draft → Submitted) and again at document generation. A "check completeness" action is also available at any time.

4. **AHJ approval is handled through the submission review workflow.** Fields throughout the entities that reference "approved by AHJ" or "acceptable to AHJ" are satisfied through the inspector review process (Entity 1.5), not through a separate per-item approval entity. Inspectors review the complete plan holistically and can request changes via the review history. The one exception is fire/life safety system interruption (Section 5.5), which requires documented three-party sign-off and is captured as conditional fields in Entity 6.

5. **Annex material is included as guidance, not requirements.** The spec distinguishes between mandatory (`[5.3.2]`) and informational (`[A.5.3]`) references. In the UI, annex material should appear as help text, tooltips, or expandable guidance sections — not as required fields. However, annex-recommended items (like the fire hazards evaluation checklist in A.16.2.1) are practically expected by most AHJs.

6. **The inspection schedule (Entity 11) is informational.** Annex C is non-mandatory. It's included because most AHJs expect to see an inspection plan, and providing a pre-built schedule template based on installation type is a significant value-add for the user.

## NFPA 160 (2026 Edition) — Notable Changes

The spec is based on the 2026 edition. Key changes from the 2021 edition that are reflected in the requirements:

| Change | Section | Impact |
|---|---|---|
| Post-show defueling requirements now apply universally to **all fuels** (previously gas-focused) | [7.7.3] | Affects all fuel types in Entity 3 and post-show procedures in Entity 5 |
| **Flame effect operator** (not production management) determines post-show defueling time | [7.7.3.1] | UX should make clear this is the flame effect operator's responsibility to define |
| Fire performers must designate **at least one cast member as flame effect operator** | [14.1.1.3.1] | New required field in Entity 8; that designated person must meet all Chapter 8 flame effect operator requirements |
| Emergency stop control stations must **maintain actuated state until manually reset** | [9.2.1.6.1.1] | New explicit requirement for control system description in Entity 3 |

## Source Standard

**NFPA 160, Standard for the Use of Flame Effects Before an Audience, 2026 Edition**
- Issued: April 12, 2025
- Effective: May 2, 2025
- Published by: National Fire Protection Association
- ISBN: 978-145593216-0 (Print)

The full text of the standard is required for cross-referencing during development but cannot be committed to the repository. Developers should have a licensed copy of NFPA 160 (2026) available. The standard can be viewed at no cost at [nfpa.org/docinfo](https://nfpa.org/docinfo).

## Technology Stack

### Decided

| Layer | Choice | Notes |
|---|---|---|
| **Framework** | Ruby on Rails 8+ | Convention-over-configuration; strong form/model/validation support for questionnaire workflows |
| **Front-end** | Hotwire (Turbo + Stimulus) | Dynamic form behavior for conditional fields without SPA complexity |
| **CSS** | Tailwind CSS | Utility-first styling for a forms-heavy UI |
| **Database** | PostgreSQL via Cloud SQL | Managed instance (`db-f1-micro`, ~$10/month); native Cloud Run connector |
| **Background Jobs** | Solid Queue | Rails 8 built-in; PostgreSQL-backed, no Redis required |
| **Caching** | Solid Cache | Rails 8 built-in; PostgreSQL-backed |
| **WebSocket** | Solid Cable | Rails 8 built-in; PostgreSQL-backed; for job progress updates during document generation |
| **File Storage** | Active Storage → Google Cloud Storage | Rails built-in; GCS adapter for attachments (SDS sheets, drawings, manuals) |
| **Hosting** | Google Cloud Run | Containerized, scales to zero, no infrastructure management |
| **Authentication** | Google Account (OmniAuth) | Single sign-on via Google; no password management |
| **Authorization** | Lightweight controller scoping | Users see only their own records; inspectors get read-only access to submitted plans |
| **PDF Generation** | Prawn | Ruby-native PDF generation; full programmatic control over document layout |
| **UI Components** | Phlex | Pure-Ruby HTML rendering; reusable components across 11 entity form types |
| **Form Builder** | Simple Form | Declarative form DSL with Tailwind integration; simplifies 20+ conditional form branches |
| **Testing** | Minitest | Rails default; simple, fast, ships with Rails 8 |

### User Roles

| Role | Access |
|---|---|
| **Artist / Operator** | Create and manage their own plans, effects, personnel, procedures |
| **Inspector** | Read-only access to submitted plans (assigned by jurisdiction/AHJ) |


## Open Questions

Items not yet resolved that should be addressed as the project progresses:

- **Multi-artist event submissions:** How should the system handle events where multiple artists each submit their own effects but share a common site plan and event record? Is the event organizer a distinct user role?
- **AHJ-specific customizations:** Different jurisdictions may have additional requirements beyond NFPA 160. Should the system support AHJ-specific field extensions or addenda?
- **Versioning of saved effects:** When an artist modifies a saved flame effect, should previous submissions that referenced the old version retain the original data, or update?
- **Template library:** Should the system provide starter templates for common effect types (propane poofer, liquid fuel mortar, gel torch, etc.) to accelerate onboarding?

## Resolved Questions

- **Output format:** PDF, generated via Prawn (see Technology Stack).
- **Attachment management:** SDS sheets stored in a global shared library; other attachments stored on their parent entities via Active Storage (see Entity 9).
- **NFPA 1126 integration:** Out of scope for this project. The system flags hybrid effects and requires identification of NFPA 160 vs NFPA 1126 portions (Entity 3, Section 3.1), but does not model NFPA 1126 requirements.

## Future Enhancements

Items identified during data model review that are out of scope for the initial build:

- **Inspection and test record entities:** Currently, test records for flame effects are stored as attachments via Active Storage on Entity 3. A future enhancement could introduce structured inspection/test record entities with fields for test type, date, result, and inspector — enabling validation of testing schedules and expiration tracking.
- **Deviation and variance tracking:** The system does not currently model deviations from approved plans or variance requests. A future enhancement could allow artists to document and track AHJ-approved deviations from standard requirements, with an audit trail of what was requested and approved.

## Related Standards

These standards are referenced by NFPA 160 and may be relevant to future scope expansion:

| Standard | Relevance |
|---|---|
| NFPA 1126 | Pyrotechnics before a proximate audience — required for hybrid flame effects |
| NFPA 1 | Fire Code — general fire safety, fuel storage |
| NFPA 10 | Portable fire extinguishers — extinguisher requirements |
| NFPA 30 | Flammable and combustible liquids — liquid fuel storage |
| NFPA 140 | Motion picture/TV production — flame effects without audience |
| NFPA 58 | Liquefied petroleum gas — LPG handling |
| NFPA 55 | Compressed gases and cryogenic fluids |
| NFPA 101 | Life Safety Code — assembly occupancy open flame prohibitions |
| NFPA 705 | Field flame test for textiles — fire retardant testing for performance areas |
