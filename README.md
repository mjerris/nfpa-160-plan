# NFPA 160 Plan Submission System — Requirements Specification

A structured data model and requirements specification for building a questionnaire-based system that helps artists create complete **Flame Effect Plan** and **Design Plan** submissions compliant with **NFPA 160 (2026 Edition)** — *Standard for the Use of Flame Effects Before an Audience*.

## Purpose

This specification defines every data point required by NFPA 160 to produce a submission-ready plan document for the Authority Having Jurisdiction (AHJ). It is organized as a set of **entities** (logical data objects) that map to forms in a questionnaire system where artists can:

- Define and save **flame effects** (apparatus-based effects with control systems — Chapter 9)
- Define and save **fire performances** (performer-based effects with props/wicks — Chapter 14)
- Save reusable components (procedures, personnel records)
- Combine saved entities to generate a complete plan document for AHJ submission

A submission can include flame effects only, fire performances only, or a combination of both.

## Scope

- **All installation types:** Temporary (≤180 days) and Permanent (>180 days)
- **All fuel types:** Gaseous (Ch. 10), Liquid (Ch. 12), Prepackaged Single-Use (Ch. 11), Gel/Solid (Ch. 13)
- **Fire Performers:** Chapter 14
- **All flame effect classifications:** Groups I–VII

## How to Read These Documents

| Convention | Meaning |
|---|---|
| `[5.3.2(1)]` | Mandatory code section reference |
| `[A.5.3]`, `[B.1.1]`, `[C.2.1]` | Annex (informational, non-mandatory) reference |
| **Required = Yes** | Must be captured for a compliant submission |
| **Required = Conditional** | Required only when a specific condition is met (noted in Guidance) |
| **Required = Recommended** | Not explicitly mandated by code but strongly advised or practical |

## Repository Structure

```
nfpa-160-plan/
├── README.md                          # This file
├── LICENSE                            # MIT License
├── CHANGELOG.md                       # Version history
│
├── docs/                              # Specification documents
│   ├── PRODUCT-BRIEF.md               # System vision, design decisions, open questions
│   ├── ENTITY-MODEL.md                # Entity relationship overview and data model diagram
│   │
│   ├── entities/                      # Entity specifications
│   │   ├── 01-production-event.md     # Production/event-level information
│   │   ├── 02-personnel.md            # Operators, assistants, support personnel, spotters
│   │   ├── 03-flame-effect.md         # Individual flame effect (apparatus-based, Chapter 9)
│   │   ├── 04-site-plan.md            # Site plan diagram requirements
│   │   ├── 05-procedures.md           # Operating, pre/post-show, emergency, maintenance
│   │   ├── 06-fire-protection.md      # Extinguishers, fire hazards eval, standby personnel
│   │   ├── 07-holding-storage.md      # Holding and storage area requirements
│   │   ├── 08-fire-performance.md     # Fire performance (performer-based, Chapter 14)
│   │   ├── 09-attachments.md          # Required documents and file uploads
│   │   ├── 10-review-coordination.md  # AHJ review, demonstrations, plan maintenance
│   │   └── 11-inspection-schedule.md  # Temporary and permanent inspection schedules
│   │
│   └── appendices/                    # Appendix specifications
│       ├── A-document-generation.md   # Assembly logic for final submission document
│       ├── B-validation-rules.md      # System validation rules by category
│       └── C-conditional-logic.md     # Form branching conditions reference
│
└── src/                               # Application source code (future)
```

## Source Standard

**NFPA 160, Standard for the Use of Flame Effects Before an Audience, 2026 Edition**
- Issued: April 12, 2025
- Effective: May 2, 2025
- Published by: National Fire Protection Association

The full text of the standard is required for development cross-referencing but cannot be committed to the repository. See [docs/PRODUCT-BRIEF.md](docs/PRODUCT-BRIEF.md) for system vision, design decisions, and open questions.

## Contributing

When updating this specification:

1. All additions must include the NFPA 160 section reference in brackets
2. Distinguish between mandatory (`[5.3.2]`) and informational (`[A.5.3]`) references
3. Mark fields as Required, Conditional, or Recommended
4. Update the conditional logic map in `docs/appendices/C-conditional-logic.md` for any new branching conditions
5. Update validation rules in `docs/appendices/B-validation-rules.md` for any new enforceable rules
6. Log changes in `CHANGELOG.md`

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

This specification is a derivative work interpreting requirements from NFPA 160 (2026). It does not reproduce the standard and is not a substitute for the official NFPA document. Users must reference the official NFPA 160 standard for authoritative requirements.
