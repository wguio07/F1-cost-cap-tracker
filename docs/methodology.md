[methodology.md](https://github.com/user-attachments/files/26256081/methodology.md)
# Methodology — FIA Cost Cap Framework Applied to Formula SAE

This document explains how the FIA Financial Regulations cost cap structure is adapted for a university Formula SAE team, and describes the analytical methodology used throughout the workbook.

---

## Why FIA Categories?

The FIA Financial Regulations (introduced 2021, updated annually) define a structured cost cap framework that forces F1 teams to categorise every item of spend. This categorisation logic — which separates chassis from listed parts, manufacturing from testing, capital from operations — is directly relevant to any cost-controlled motorsport programme.

Applying this framework to a FSAE team achieves two things:

1. It produces a more rigorous and comparable budget structure than ad-hoc team spreadsheets
2. It demonstrates domain-specific financial awareness to hiring teams in professional motorsport

---

## Category Mapping

### Chassis & Aerodynamic Parts
**FIA scope:** All parts designed to generate aerodynamic load or form the primary structure of the car, including monocoque, bodywork, wings, diffusers, and associated materials.

**FSAE adaptation:** CFRP materials, GRP bodywork, aero package (wings, diffuser, sidepods), roll hoop, structural adhesives, and chassis consumables. Does not include powertrain mounting provisions, which sit in Listed Parts.

### Listed Parts (Gearbox & Suspension)
**FIA scope:** Components appearing on the FIA Listed Parts list — standardised or homologated parts where cost is regulated at source.

**FSAE adaptation:** Engine and intake system, gearbox internals, chain drive, suspension wishbones, uprights, steering components, wheel hubs, brakes, and differential. These are the primary mechanical assemblies whose cost drives competitive parity decisions in FSAE.

### Manufacturing Operations
**FIA scope:** Direct cost of manufacturing activities — machine hire, tooling, consumables, finishing — excluding depreciation of owned capital equipment.

**FSAE adaptation:** CNC machine hire, 3D printing consumables, welding materials and gas, workshop consumables, outsourced waterjet and laser cutting, and surface finishing (anodising, powder coating).

### Personnel (Capped Employees)
**FIA scope:** Salary costs for employees within the cost cap (excludes top earners above a threshold and certain senior roles).

**FSAE adaptation:** As team members are unpaid students, this category covers structured learning and development spend — online course subscriptions (Coursera, Udemy, LinkedIn Learning) and internal workshop materials. This reflects the intent of the category: investment in the human capability delivering the programme.

### Travel & Freight
**FIA scope:** Transportation of people, parts, and equipment to and from events and testing.

**FSAE adaptation:** Van hire for both competition events, fuel, team accommodation, competition entry fees, parts shipping/freight, and miscellaneous travel. Cross-channel travel (FS Germany) included with appropriate contingency.

### Testing & Track Operations
**FIA scope:** Circuit hire, tyre consumption during testing, and operational costs of on-track sessions outside of competition.

**FSAE adaptation:** Circuit hire at Bicester and Silverstone MIRA, skidpad session costs, test tyre set, data logging consumables, and driver equipment hire for test sessions.

### Depreciation & Capital Equipment
**FIA scope:** Depreciation charges on owned capital equipment and facilities used in the programme.

**FSAE adaptation:** Tooling purchases, safety equipment, workshop organisation, and data acquisition hardware. Equipment borrowed from university departments (oscilloscope, DAQ system) is recorded at zero cost with the loan arrangement documented — consistent with how in-kind contributions are treated in cost cap submissions.

---

## RAG Status Logic

RAG status is calculated automatically in the workbook using the following Excel formula applied to each sub-component and category:

```
=IF(variance% > 5%,  "RED",
 IF(variance% > 0%,  "AMBER",
                     "GREEN"))
```

This threshold is consistent with how Cost Engineers typically set early-warning triggers in professional F1 team reporting: anything above 5% overspend at category level requires a formal corrective action review.

---

## Variance Attribution

Each of the 28 line items carries a root cause and corrective action written to a consistent standard:

**Root cause format:** Named event or decision + quantified impact where possible + timing context
> *"Unplanned rework of upright geometry after simulation data review required two additional CNC sessions, adding £500 to hire cost."*

**Corrective action format:** Specific process change + measurable target + owner/timing where applicable
> *"Lock CNC geometry sign-off to Week 8. Add £300 rework contingency to CNC budget."*

This format mirrors the root cause analysis documentation used in F1 finance teams when presenting variance reports to the Technical Director.

---

## Exclusions

The following items are excluded from the budget model, consistent with FIA Financial Regulations:

- **Power Unit costs** — engines, fuel, and power unit development are excluded from the F1 cost cap entirely and are treated similarly here (engine is a fixed-spec unit and its replacement cost is not modelled as a variable)
- **Driver compensation** — all team members are unpaid students; no salary or stipend costs are included
- **University facility overhead** — workshop space, utilities, and university-provided equipment (lathes, mills, etc.) are not charged to the budget, consistent with how certain infrastructure costs are excluded from the FIA cap

---

## Colour Coding Convention

This workbook follows the standard financial modelling colour convention:

| Colour | Meaning |
|---|---|
| **Blue text** | Hardcoded input — edit freely |
| **Black text** | Formula — do not edit |
| **Red / Amber / Green fills** | RAG status cells only |

This convention is used universally in professional financial modelling (investment banking, corporate finance, motorsport finance) and is recognised immediately by any finance professional reviewing the workbook.
