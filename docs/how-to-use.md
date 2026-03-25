[how-to-use.md](https://github.com/user-attachments/files/26256109/how-to-use.md)
# How to Use the Workbook

Step-by-step guide for updating and extending the cost tracker.

---

## Opening the File

Download `OBU_FSAE_Cost_Tracker_2024-25.xlsx` and open in **Microsoft Excel 2016 or later**. The workbook uses standard Excel formulas (`SUM`, `IF`, `SUMIF`, `COUNTIF`, `INDEX/MATCH`) — no macros, no add-ins required.

> **Google Sheets users:** The file is compatible. Conditional formatting and formulas carry over. Minor visual differences in cell shading may appear.

---

## Navigating the Sheets

Use the tabs at the bottom:

1. **Dashboard** — start here for the summary view. Do not edit this sheet.
2. **Data** — all input happens here. Edit blue cells only.
3. **Variance Analysis** — formula-driven breakdown. Do not edit.
4. **Assumptions & Notes** — reference documentation.

---

## Updating Actuals (Most Common Task)

1. Go to the **Data** sheet
2. Find the sub-component row you want to update (column C)
3. Enter the new actual spend in **column F** (blue cell)
4. The category total in the header row above updates automatically
5. The Dashboard and Variance Analysis sheets recalculate instantly

---

## Updating Budgets

1. Go to the **Data** sheet
2. Find the relevant sub-component row
3. Update the budget value in **column E** (blue cell)
4. All dependent formulas recalculate automatically

> Do not enter values in category header rows (rows where column C starts with ▸). These are formula rows that sum the sub-components below them.

---

## Adding a New Sub-Component

1. Go to the **Data** sheet
2. Find the category where the new item belongs
3. Insert a new row within the category block (between the header row and the next category header)
4. Enter the category code in column A, a sequential number in column B, and fill in all blue columns
5. **Important:** Check that the category header row's `SUM` range still covers your new row. Extend the range if necessary (e.g. `=SUM(E4:E8)` → `=SUM(E4:E9)`)

---

## Changing RAG Thresholds

The RAG thresholds are currently set at >5% = RED, 0–5% = AMBER, ≤0% = GREEN.

To change thresholds, find any RAG formula cell (column G in the Data sheet) and update the `0.05` value:

```excel
=IF(E4=0,"N/A",IF((F4-E4)/E4 > 0.05,"RED",IF((F4-E4)/E4 > 0,"AMBER","GREEN")))
```

Change `0.05` to your desired RED threshold (e.g. `0.10` for 10%). Apply the same change to all sub-component rows in column G and to the category header rows.

---

## Colour Coding Rules

| Text colour | Meaning | Can I edit? |
|---|---|---|
| Blue | Hardcoded input | ✅ Yes |
| Black | Formula | ❌ No |

Do not retype formula cells — if you accidentally overwrite one, press `Ctrl+Z` to undo immediately.

---

## Common Issues

**Dashboard shows £0 for all values**
The Dashboard pulls from specific cells in the Data sheet. Check that no rows have been inserted above the Data header row (row 2), which would shift the cell references.

**RAG shows N/A instead of RED/AMBER/GREEN**
This happens when the Budget cell (column E) for that row is zero. Enter a budget value or leave the row intentionally at zero if the item has no planned cost.

**Total on Dashboard doesn't match sum of categories**
The Dashboard totals use `SUM(C11:C17)` — if you've added categories beyond row 17, extend the range accordingly.
