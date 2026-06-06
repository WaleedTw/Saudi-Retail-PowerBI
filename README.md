# Saudi Retail & E-commerce Analytics Portfolio

An interactive, data-driven Business Intelligence solution built to evaluate the digital transformation, financial performance, and e-commerce adoption of 6 leading listed Saudi retail corporations (Jarir, Nahdi, Cenomi Retail, Alsaif Gallery, Al Majed Oud, and SACO) from 2022 to 2025.

The platform features a dynamic frontend interface with bilingual support (Arabic/English) and integrates a live-embedded Power BI dashboard. By utilizing complex DAX computations and custom star-schema data modeling, it tracks over SAR 113 Billion in corporate revenues. It also features a dynamic forecasting engine (What-If simulations) that enables executives to stress-test future digital growth targets and compound annual growth rates dynamically.

## 🌐 Live Portfolio Showcase
👉 **[View the Live Website & Interactive Dashboard](https://zesty-pothos-487471.netlify.app/)**

---

## 🧮 Key DAX Measures

### 1. Projected E-commerce Revenue (What-If Forecasting)

This measure dynamically estimates future e-commerce revenue based on the growth percentage selected through the What-If parameter slider.

```DAX
Projected_Ecom_Revenue =
VAR CurrentEcom = SUM('sh2'[Ecom_Revenue])
VAR SelectedGrowth = [Target Growth Value]
RETURN
    CurrentEcom * (1 + SelectedGrowth)
```

### 2. Year-over-Year E-commerce Growth

This measure calculates the annual percentage growth of e-commerce revenue compared to the previous year.

```DAX
Ecom_YoY_Growth =
VAR CurrentYear = SELECTEDVALUE('sh2'[Year])
VAR CurrentYearEcom = SUM('sh2'[Ecom_Revenue])
VAR PreviousYearEcom =
    CALCULATE(
        SUM('sh2'[Ecom_Revenue]),
        'sh2'[Year] = CurrentYear - 1
    )
RETURN
    DIVIDE(CurrentYearEcom - PreviousYearEcom, PreviousYearEcom, 0)
```

---
