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
