# Entity 1: Production / Event

One record per submission. Describes the overall production context.

## 1.1 Responsible Party

| Field | Required | Section | Guidance |
|---|---|---|---|
| Name of person, group, or organization responsible for the production | Yes | [5.3.2(1)] | Legal entity or individual taking responsibility |
| Contact information | Recommended | — | Not explicitly required by code, but practical for AHJ communication |

## 1.2 Schedule

| Field | Required | Section | Guidance |
|---|---|---|---|
| Date(s) of production | Yes | [5.3.2(2)] | |
| Time(s) of production | Yes | [5.3.2(2)] | |

### Temporary Installation Schedule Fields

| Field | Required | Section | Guidance |
|---|---|---|---|
| Requested permit date(s) and time(s) of use | Yes | [5.1.3.2.1] | Temporary permits must specify dates and times of use |
| Requested permit expiration date | Yes | [5.1.3.2.1] | |

### Permanent Installation Schedule Fields

| Field | Required | Section | Guidance |
|---|---|---|---|
| Requested permit duration | Yes | [5.1.3.2.2] | Must specify duration |
| Requested permit expiration date | Yes | [5.1.3.2.2] | |

## 1.3 Location

| Field | Required | Section | Guidance |
|---|---|---|---|
| Venue name / location of production | Yes | [5.3.2(3)] | |
| Indoor or outdoor | Recommended | [B.1.1.1], [B.1.1.2] | Drives conditional requirements (ventilation, weather, etc.) |
| Venue description (property, facility, building, or room) | Recommended | [3.3.34], [A.3.3.34] | Per definition — specify exact area where effects are permitted. Some venue configurations may be safe for effects while others are not. |

## 1.4 Installation Classification

| Field | Required | Section | Guidance |
|---|---|---|---|
| Term of installation | Yes | [5.1.2] | Select one: Temporary or Permanent |

| Classification | Definition | Section |
|---|---|---|
| Temporary | ≤180 days within a 12-month period at a single venue | [5.1.2.2], [3.3.22.2] |
| Permanent | >180 days | [5.1.2.1], [3.3.22.1] |

System should auto-calculate classification based on permit dates and flag if it crosses the 180-day threshold. [A.5.1.2]

## 1.5 Submission Status & Review Workflow

### Status

| Field | Required | Notes |
|---|---|---|
| Status | Yes | Current submission status (see workflow below) |
| Submitted date | Conditional | Set when artist first submits; updated on each resubmission |
| Decision date | Conditional | Set when inspector approves or rejects |

### Status Workflow

```
Draft → Submitted → Under Review → Approved
                                 → Rejected
                                 → Changes Requested → (artist edits) → Submitted
```

| Status | Who acts | Description |
|---|---|---|
| **Draft** | Artist | Submission is being built. Artist can edit all fields freely. Not visible to inspectors. |
| **Submitted** | Artist → Inspector | Artist marks submission complete. Validation rules (Appendix B) run at this transition. Submission becomes visible to inspectors and read-only to the artist. |
| **Under Review** | Inspector | Inspector has picked up the submission and is actively reviewing it. |
| **Changes Requested** | Inspector → Artist | Inspector provides feedback notes. Submission returns to an editable state for the artist to address feedback. |
| **Approved** | Inspector | Submission is approved. Decision date and any approval conditions are recorded. |
| **Rejected** | Inspector | Submission is fundamentally unacceptable. Decision date and rejection reason are recorded. |

**Resubmission:** When an artist resubmits after changes are requested, validation rules run again and the status returns to **Submitted**. The inspector can pick it up for another review cycle.

### Review History

Each status change is recorded with notes, creating an audit trail of the review process.

| Field | Required | Notes |
|---|---|---|
| Author | Yes | Name of the person (artist or inspector) who made the entry |
| Date | Yes | When the entry was created |
| Action | Yes | The status transition (e.g., Submitted, Under Review, Changes Requested, Resubmitted, Approved, Rejected) |
| Notes | Conditional | Feedback, response, or decision rationale; required for Changes Requested and Rejected |

**Example review history:**

| Date | Author | Action | Notes |
|---|---|---|---|
| 2025-06-01 | Jane (artist) | Submitted | Initial submission |
| 2025-06-03 | Marshal Smith | Under Review | |
| 2025-06-04 | Marshal Smith | Changes Requested | Site plan missing extinguisher placement on south side; SDS for denatured alcohol is expired (2019) |
| 2025-06-05 | Jane (artist) | Resubmitted | Updated site plan with extinguisher placement; replaced SDS with current version (2024) |
| 2025-06-06 | Marshal Smith | Under Review | |
| 2025-06-06 | Marshal Smith | Approved | All requirements satisfied |
