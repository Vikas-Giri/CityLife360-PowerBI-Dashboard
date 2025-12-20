
# CityLife 360 – Power BI Dashboard

📊 Learning-Focused Business Intelligence Project (Simulated Executive Reporting)

## Important Context
This is a learning-focused Power BI project created to practice business intelligence
concepts such as data modeling, DAX time intelligence, and dashboard design.

The dashboard and documentation are written in a professional, executive-reporting style
to simulate a real-world business scenario. This project is not used in production and
represents hands-on skill development.

---

This repository contains a Power BI report (`CityLife360_Project.pbix`) and a sample data
file (`CityLifeData.xlsx`) used to build a simulated executive-facing 360° sales dashboard.
The report demonstrates time-intelligence DAX, dynamic KPIs, and interactive visual insights.

---

## Table of Contents
- Project overview
- Getting started
- Data & privacy
- Key pages & screenshots
- DAX measures (examples & recommendations)
- Recommended best practices
- Project structure
- License
- Contact

---

## Project Overview

### Objectives
- Build an interactive multi-page Power BI dashboard
- Track Sales, Withdrawals, Net Contribution, and YoY performance
- Analyze metrics across products, advisors, and risk levels
- Implement DAX time intelligence (CY, PY, YoY%)
- Provide a clean, executive-style reporting UI

This repository includes the PBIX report and a sample Excel dataset used to build the
visuals. The PBIX contains a dedicated Date (Calendar) table which is used for all
time-intelligence calculations.

---

## Getting Started

### Prerequisites
- Power BI Desktop (recommended: latest stable release; tested with version 2.149.1429.0)
- Windows or a supported OS for Power BI
- (Optional) Git LFS if version-controlling large `.pbix` files

### Open the Report
1. Download `CityLife360_Project.pbix` from the repository.
2. Place `CityLifeData.xlsx` in the same directory as the PBIX, or re-point the data source:
   - Home → Transform data → Data source settings → Change source
3. In Power BI Desktop, confirm the dedicated Date table is present and marked correctly:
   - Model view → Select Date table → Modeling → Mark as date table
4. Refresh the report:
   - Home → Refresh (ensure data source paths and credentials are configured)

### Notes
- When storing PBIX files in Git, consider using Git LFS or GitHub Releases to avoid
  bloating commit history.
- If the Excel file contains sensitive or production-like data, replace it with an
  anonymized or sample dataset before sharing publicly.

---

## Data & Privacy

- `CityLifeData.xlsx` is included as a **sample dataset** for learning purposes.
- Typical tables used (example schema):
  - **Sales** (`record_date`, `advisor_id`, `product_id`, `amount`,
    `withdrawal_amount`, `risk_level`)
  - **Products** (`product_id`, `product_name`, `category`, `risk_level`)
  - **Advisors** (`advisor_id`, `advisor_name`, `team`, `region`)
  - **Date** (`Date`, `Year`, `Month`, `Day`, `FiscalYear`, `IsBusinessDay`)  
    — dedicated Calendar table present in the PBIX

If real client or production data is ever used, it should be removed and replaced with
sample or anonymized data before committing.

---

## Key Pages & Screenshots

### Executive Overview
High-level KPIs and sales trends.

### Wealth Dashboard
Performance analysis across wealth products and advisors.

### Insurance Dashboard
Insurance-focused insights and performance metrics.

(Screenshots are available in the `images/` directory.)

---

## DAX Measures (Examples & Recommendations)

The PBIX uses a dedicated Date/Calendar table named `Date`, which is marked as the model
date table. All time-intelligence measures assume this configuration.

### Core Measures

**Total Sales**
```DAX
Total Sales = SUM('Sales'[amount])
Total Withdrawals
Copy code
DAX
Total Withdrawals = SUM('Sales'[withdrawal_amount])
Net Contribution
Copy code
DAX
Net Contribution = [Total Sales] - [Total Withdrawals]
Time Intelligence Measures
Current Year Sales (CY)
Copy code
DAX
CY Sales =
CALCULATE(
    [Total Sales],
    YEAR('Date'[Date]) = YEAR(MAX('Date'[Date]))
)
Prior Year Sales (PY)
Copy code
DAX
PY Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR('Date'[Date])
)
Year-over-Year Sales %

DAX
YoY Sales % =
DIVIDE([CY Sales] - [PY Sales], [PY Sales], 0)
Using VARs for Readability

DAX
YoY Sales % (Clean) =
VAR _CY = [CY Sales]
VAR _PY = [PY Sales]
RETURN
DIVIDE(_CY - _PY, _PY, 0)
Notes
SAMEPERIODLASTYEAR and DATEADD require a continuous Date table with no gaps.
Use DIVIDE(..., 0) to handle divide-by-zero scenarios.
Consider USERELATIONSHIP when working with multiple date columns.
Optional Snapshot Date Table

DAX
CONST =
DATATABLE(
    "CurrentDate", DATETIME,
    { { DATE(2025, 12, 31) } }
)
This can be used for snapshot-based comparisons if required. Any update logic should be documented clearly.
Recommended Best Practices
Create and mark a dedicated Date/Calendar table
Use DAX variables (VAR) for clarity and maintainability
Apply consistent naming conventions for measures
Avoid committing sensitive or production data
Use Git LFS or Releases for large PBIX files
Document complex Power Query transformations where applicable
Project Structure


CityLife360-PowerBI-Dashboard/
├─ CityLife360_Project.pbix
├─ CityLifeData.xlsx
├─ README.md
├─ LICENSE
└─ images/
   ├─ Executive_Overview.png
   ├─ Wealth_Dashboard.png
   └─ Insurance_Dashboard.png
License
This project is licensed under the MIT License. See the LICENSE file for details.
Contact
Developer: Vikas Giri
GitHub: https://github.com/Vikas-Giri
LinkedIn: https://linkedin.com/in/vikasgiri