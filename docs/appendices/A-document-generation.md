# Appendix A: Document Generation Logic

Assembly order and logic for generating the final submission document from saved entities.

## Assembly Order

When the system assembles a final submission document from saved entities, it should combine sections in the following order. The submission type (Flame Effects or Fire Performances) determines which core entity section is included.

1. **Production/Event header** ([Entity 1](../entities/01-production-event.md)) — including installation classification and submission type
2. **Personnel section** ([Entity 2](../entities/02-personnel.md)) — flame effect operator(s), assistants, support personnel
3. **Site Plan with diagram(s)** ([Entity 4](../entities/04-site-plan.md)) — referencing all saved effects or performances, with indoor/outdoor additions as applicable
4. **If Flame Effects submission:** Individual Flame Effect descriptions ([Entity 3](../entities/03-flame-effect.md), one or more) — each with fuel, appliance, control system, and hazard area subsections. Conditional sections shown based on fuel type selection.
5. **If Fire Performances submission:** Fire Performance section ([Entity 8](../entities/08-fire-performance.md), one or more) — performers, spotters, props, fueling, performance plan
6. **Holding/Storage areas** ([Entity 7](../entities/07-holding-storage.md))
7. **Procedures** ([Entity 5](../entities/05-procedures.md)) — operating, pre-show, show, post-show, emergency, maintenance, housekeeping, protective clothing
8. **Fire Protection Plan** ([Entity 6](../entities/06-fire-protection.md)) — extinguishers (temporary) or fire hazards evaluation (permanent), standby personnel
9. **Attachment references** ([Entity 9](../entities/09-attachments.md)) — SDS sheets (from global library), drawings, test docs, manufacturer instructions
10. **Review & Coordination records** ([Entity 10](../entities/10-review-coordination.md))
11. **Inspection schedule** ([Entity 11](../entities/11-inspection-schedule.md)) — temporary or permanent schedule as applicable

## Conditional Section Inclusion

| Condition | Sections Included |
|---|---|
| Submission Type = Flame Effects | Entity 3 descriptions; Chapter 9 procedures and validation |
| Submission Type = Fire Performances | Entity 8 descriptions; Chapter 14 procedures and validation; fire performance site plan additions |
| Installation = Temporary | Temporary permit fields, extinguisher requirements, temporary inspection schedule |
| Installation = Permanent | Permanent permit fields, fire hazards evaluation, permanent inspection schedule |
| Indoor venue | Ventilation and combustion air sections in site plan |

## Per-Effect Rendering (Flame Effects submissions)

Each saved flame effect (Entity 3) should render as a self-contained subsection in the final document, with:

- Effect identification and classification
- Fuel specification (only the fields for the selected fuel type)
- Appliance description
- Control system description (only manual OR automatic fields as applicable)
- Hazard area definition
- If portable: storage and security plan
- Post-operation securing procedure
- Testing and evaluation records

## Per-Performance Rendering (Fire Performances submissions)

Each saved fire performance (Entity 8) should render as a self-contained subsection in the final document, with:

- Performers (linked from Entity 2 role assignments)
- Rehearsal confirmation
- Spotters (linked from Entity 2 role assignments)
- Fire props (general, wicks, handles, connectors, extinguishment)
- Fueling plan
- Performance plan (separation, performance area)
- Performer clothing
- Post-performance procedures

## Cross-Entity References

The generated document should automatically cross-reference:

- Each effect or performance listed on the site plan diagram links to its full description
- Personnel named in Entity 2 are referenced in operating procedures
- SDS documents from the global library are linked to the fuels declared in each Entity 3 or Entity 8 record
- Fire extinguisher locations on the site plan match the fire protection plan
- Holding area capacities on the site plan match Entity 7 declarations
