# 📐 DAX Measures

This document lists all DAX measures used in the **Sales Analytics Power BI Report**, grouped by category.  
All measures are based on the `'Sales Original'` fact table and the `'Calendar'` date table for time intelligence.

---

## 🧮 1. Core KPIs

```DAX
Sales Value = SUM ( 'Sales Original'[Total Revenue] )

Sales Profit = SUM ( 'Sales Original'[Total Profit] )

Sales Cost = SUM ( 'Sales Original'[Total Cost] )

Sales Qty = SUM ( 'Sales Original'[Units Sold] )

Sales Profit per Item = 
DIVIDE ( [Sales Profit], [Sales Qty] )

Profit % = 
DIVIDE ( [Sales Profit], [Sales Value], 0 )

---

## 📆 2. Previous Year (LY) Calculations

```Sales Value LY =
CALCULATE (
    [Sales Value],
    DATEADD ( 'Calendar'[Date], -1, YEAR )
)

Sales Profit LY =
CALCULATE (
    [Sales Profit],
    DATEADD ( 'Calendar'[Date], -1, YEAR )
)

Sales Cost LY =
CALCULATE (
    [Sales Cost],
    DATEADD ( 'Calendar'[Date], -1, YEAR )
)

Sales Qty LY =
CALCULATE (
    [Sales Qty],
    DATEADD ( 'Calendar'[Date], -1, YEAR )
)

Profit perc LY =
CALCULATE (
    [Profit %],
    DATEADD ( 'Calendar'[Date], -1, YEAR )
)

---

## 📊 3. Year-over-Year (YoY) Comparisons

---Sales vs LY % =
DIVIDE (
    [Sales Value] - [Sales Value LY],
    ABS ( [Sales Value LY] )
)

Profit vs LY % =
DIVIDE (
    [Sales Profit] - [Sales Profit LY],
    ABS ( [Sales Profit LY] )
)

Cost vs LY % =
DIVIDE (
    [Sales Cost] - [Sales Cost LY],
    ABS ( [Sales Cost LY] )
)

Qty vs LY % =
DIVIDE (
    [Sales Qty] - [Sales Qty LY],
    ABS ( [Sales Qty LY] )
)

Profit perc vs LY % =
DIVIDE (
    [Profit %] - [Profit perc LY],
    ABS ( [Profit perc LY] )
)
