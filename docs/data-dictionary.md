[data-dictionary.md](https://github.com/user-attachments/files/26256104/data-dictionary.md)
# Data Dictionary

Field-by-field reference for the Data sheet, which is the single source of truth for the entire workbook.

---

## Data Sheet — Column Reference

| Column | Header | Type | Description |
|---|---|---|---|
| A | Cat | Reference code | Two-letter category code: CH, DS, MF, TR, TL, TS, EQ |
| B | # | Integer | Sub-component number within category (blank on category header rows) |
| C | Sub-Component / Line Item | Text | Description of the part, service, or activity |
| D | FIA Category | Text | FIA Financial Regulations Article 2 category this item maps to |
| E | Budget (£) | £ input | Planned spend set at season start — **blue, editable** |
| F | Actual (£) | £ input | Year-end actual spend — **blue, editable** |
| G | RAG | Formula | Auto-calculated: RED / AMBER / GREEN based on variance % |
| H | Root Cause | Text input | Explanation of what drove the variance — **blue, editable** |
| I | Corrective Action | Text input | Recommended process change for next season — **blue, editable** |

---

## Category Header Rows

Category header rows (where column B is blank and column C starts with ▸) are formula rows — their Budget and Actual values are `SUM` aggregates of the sub-component rows below. Do not enter values directly into these rows.

---

## Category Codes

| Code | Category |
|---|---|
| CH | Chassis & Aero Components |
| DS | Drivetrain & Suspension |
| MF | Manufacturing & Workshop |
| TR | Team Training & Development |
| TL | Travel & Competition Logistics |
| TS | Testing & Shakedown |
| EQ | Equipment & Tooling |

---

## RAG Formula Logic

The RAG column uses a nested IF formula applied at both sub-component and category level:

```excel
=IF(E_row=0, "N/A",
 IF((F_row-E_row)/E_row > 0.05, "RED",
  IF((F_row-E_row)/E_row > 0,   "AMBER",
                                 "GREEN")))
```

- Returns `N/A` when budget is zero (prevents division-by-zero errors)
- Returns `RED` when actual exceeds budget by more than 5%
- Returns `AMBER` when actual exceeds budget by 0–5%
- Returns `GREEN` when actual is at or below budget

---

## Dashboard Sheet — KPI Reference

| Cell | Label | Formula |
|---|---|---|
| C6 | Total Budget | `=SUM(C11:C17)` — sum of all 7 category budgets |
| D6 | Total Actual | `=SUM(D11:D17)` — sum of all 7 category actuals |
| E6 | Headroom | `=C6-D6` — positive means under budget |
| F6 | Cap Utilisation | `=D6/C6` — formatted as % |

---

## Variance Analysis Sheet — Metrics Reference

| Row | Metric | Formula |
|---|---|---|
| Worst Overspend Category | Category name with highest positive variance | `INDEX/MATCH` on variance column |
| Largest Saving Category | Category name with most negative variance | `INDEX/MATCH` on variance column |
| Total Gross Overspend | Sum of all positive variances only | `=SUMIF(E3:E9,">0",E3:E9)` |
| Total Gross Savings | Absolute sum of all negative variances only | `=ABS(SUMIF(E3:E9,"<0",E3:E9))` |
| Net Position | Total actual minus total budget | `=D10-C10` |
| Biggest Overspend % | Highest positive variance % among categories | `=MAXIFS(...)` |

---

## Season Summary — 2024/25 Actuals

| Category | Budget | Actual | Variance | Var % | RAG |
|---|---|---|---|---|---|
| Chassis & Aero Components | £11,750 | £14,200 | +£2,450 | +20.9% | RED |
| Drivetrain & Suspension | £9,200 | £8,750 | -£450 | -4.9% | GREEN |
| Manufacturing & Workshop | £6,800 | £7,600 | +£800 | +11.8% | RED |
| Team Training & Development | £1,100 | £1,060 | -£40 | -3.6% | GREEN |
| Travel & Competition Logistics | £5,200 | £5,410 | +£210 | +4.0% | AMBER |
| Testing & Shakedown | £3,380 | £3,100 | -£280 | -8.3% | GREEN |
| Equipment & Tooling | £1,250 | £950 | -£300 | -24.0% | GREEN |
| **GRAND TOTAL** | **£38,680** | **£41,070** | **+£2,390** | **+6.2%** | |
