# F1 Cost Cap Variance Tracker — OBU Autonomous Racing 2024/25

A Formula SAE budget compliance workbook built on the **FIA Financial Regulations cost cap framework** — demonstrating cost engineering, sub-component variance analysis, and financial reporting methodology applicable to professional motorsport finance roles.

---

## Quick Start

1. Download [`OBU_FSAE_Cost_Tracker_2024-25.xlsx`](./OBU_FSAE_Cost_Tracker_2024-25.xlsx)
2. Open in Microsoft Excel or Google Sheets
3. Navigate to the **Data** sheet — all blue cells are editable inputs
4. Dashboard and Variance Analysis sheets update automatically

> All figures are simulated for portfolio demonstration purposes.

---

## What This Is

This project applies the **FIA Financial Regulations Article 2 cost cap structure** to a OBU team, scaled to a realistic ~40,000 seasonal budget. The workbook models the core workflow of an F1 Cost Engineer:

- Breaking total spend into regulated categories with sub-component line-item detail
- Tracking budget vs actual with automatic RAG compliance status
- Attributing variances to specific root causes
- Generating corrective action recommendations

The data structure, threshold logic, and reporting format intentionally mirror professional cost cap practice — not generic finance templates.

---

## Workbook Structure

```
OBU_FSAE_Cost_Tracker_2024-25.xlsx
│
├── Dashboard          ← KPIs, category summary, compliance status
├── Data               ← 28 sub-component line items (edit here)
├── Variance Analysis  ← Decomposition, metrics, budget share
└── Assumptions & Notes ← Methodology, FIA mapping, usage guide
```

### Sheet 1 — Dashboard

Live KPI tiles pulling directly from the Data sheet:

| Metric | Value |
|---|---|
| Total Budget | £38,680 |
| Total Actual | £41,070 |
| Variance | +£2,390 |
| Cap Utilisation | 106.2% |

Category breakdown table with auto-colour RAG status and root cause / corrective action summaries per category. All values are formula-driven — no hardcoded outputs.

### Sheet 2 — Data

28 sub-component line items across 7 FIA-mapped categories. **Blue cells are editable inputs.** Black cells are formulas — do not edit. Category totals aggregate via `SUM`. RAG status is calculated automatically:

```
Variance > 5%   →  RED
Variance 0–5%   →  AMBER
Variance ≤ 0%   →  GREEN
```

### Sheet 3 — Variance Analysis

Per-category variance in £ and %, budget share percentage, and key metrics: worst overspend category, largest saving, gross overspend and savings totals — all formula-driven.

### Sheet 4 — Assumptions & Notes

Methodology documentation, FIA category mapping rationale, colour coding guide, and step-by-step usage instructions.

---

## FIA Category Mapping

The seven FIA Financial Regulation categories are adapted to FSAE scale. Power Unit costs and driver compensation are excluded, consistent with FIA convention.

| FSAE Category | FIA Article 2 Equivalent | Budget | Actual | RAG |
|---|---|---|---|---|
| Chassis & Aero Components | Chassis & Aerodynamic Parts | £11,750 | £14,200 | 🔴 RED |
| Drivetrain & Suspension | Listed Parts (Gearbox & Suspension) | £9,200 | £8,750 | 🟢 GREEN |
| Manufacturing & Workshop | Manufacturing Operations | £6,800 | £7,600 | 🔴 RED |
| Team Training & Development | Personnel (Capped Employees) | £1,100 | £1,060 | 🟢 GREEN |
| Travel & Competition Logistics | Travel & Freight | £5,200 | £5,410 | 🟡 AMBER |
| Testing & Shakedown | Testing & Track Operations | £3,380 | £3,100 | 🟢 GREEN |
| Equipment & Tooling | Depreciation & Capital Equipment | £1,250 | £950 | 🟢 GREEN |
| **TOTAL** | | **£38,680** | **£41,070** | |

---

## Season Narrative

The team ended 2024/25 **£2,390 over the seasonal budget target**, driven by two RED categories:

**Chassis & Aero (+£2,450 / +20.9%)** — A monocoque layup failure in Week 6 required full re-lamination, adding £1,400 in unbudgeted CFRP materials. A post-CFD aero geometry revision added two outsourced laser-cut iterations at £1,300. Together these account for the majority of the season's gross overspend.

**Manufacturing & Workshop (+£800 / +11.8%)** — Two unplanned CNC rework sessions on upright geometry added £500. Resin consumable prices rose 18% mid-season, adding a further £300 across 3D printing line items.

Gross overspend of £3,460 was partially offset by £1,070 in savings across four GREEN categories — notably deferred equipment purchases (£300 underspend) and lower-than-budgeted testing costs (£280 underspend).

---

## Key Concepts Demonstrated

**FIA cost cap knowledge** — Category definitions, excluded items, and RAG threshold logic are modelled on the real FIA Financial Regulations, not generic finance frameworks. Understanding the difference between listed and non-listed parts, and why Power Unit costs sit outside the cap, reflects domain-specific awareness that goes beyond spreadsheet skills.

**Sub-component root cause analysis** — Variance is attributed at line-item level (e.g. "monocoque re-lamination added £1,400 in Week 6") rather than category level. This mirrors the granularity a Cost Engineer uses to explain variances to the Chief Designer or Finance Director.

**Formula-driven compliance** — RAG status, category totals, dashboard KPIs, and all variance metrics are live Excel formulas. Changing any input cell recalculates the full model instantly. No hardcoded outputs.

**Corrective action framing** — Every variance includes a specific, actionable recommendation for the following season, demonstrating the analytical cycle: identify → attribute → recommend.

---

## Potential Extensions

- **Monthly phasing columns** — track cumulative spend by month against a phased budget
- **Rolling forecast** — project year-end position from mid-season actuals using a burn rate model
- **Multi-season overlay** — compare 2022/23, 2023/24, 2024/25 category trends
- **Scenario modelling** — simulate impact of material price changes or exchange rate moves on total spend
- **ERP integration** — connect to a SAP/Oracle CSV export for live actuals feed

---

## Author

**Wolfgang Guio**
MSc Motorsport Engineering — Distinction, Oxford Brookes University


[LinkedIn](https://www.linkedin.com/in/wolfgangguio) · [GitHub](https://github.com/wguio07) · ukwolfangguio@gmail.com

---

*All budget figures are simulated for portfolio demonstration. FIA cost cap category structure is based on publicly available Financial Regulations documentation (2025). No confidential Williams Racing or Oxford Brookes Racing data is used or referenced.*
