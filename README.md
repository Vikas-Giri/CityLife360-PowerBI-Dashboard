 ___

CityLife 360 – Power BI Dashboard

📊 Learning-Focused Business Intelligence Project (Simulated Executive Reporting)


---

Important Context

This is a learning-focused Power BI project created to practice real-world business intelligence concepts such as data modeling, DAX time intelligence, and dashboard design.

The dashboard, visuals, and documentation are intentionally written in a professional, executive-reporting style to simulate how insights might be presented to business stakeholders.
This project is not used in production and represents hands-on learning and skill development.


---

Table of Contents

Project Overview

Getting Started

Data & Privacy

Key Pages & Dashboard Preview

DAX Measures (Examples)

Recommended Best Practices

Project Structure

License

Contact



---

Project Overview

Objectives:

Build an interactive, multi-page Power BI dashboard

Practice modeling Sales, Withdrawals, Net Contribution, and YoY performance

Analyze metrics across products, advisors, and risk levels

Implement DAX time-intelligence measures (CY, PY, YoY%)

Design a clean, executive-style reporting interface


This repository contains:

A Power BI report file (CityLife360_Project.pbix)

A sample Excel dataset (CityLifeData.xlsx) used for visualization and analysis


The PBIX includes a dedicated Date (Calendar) table used for all time-intelligence calculations.


---

Getting Started

Prerequisites

Power BI Desktop (latest stable version recommended)

Windows or a supported OS for Power BI

(Optional) Git LFS for versioning large .pbix files


Open the Report

1. Download CityLife360_Project.pbix from this repository.


2. Ensure CityLifeData.xlsx is in the same directory, or update the data source in Power BI:

Home → Transform Data → Data Source Settings → Change Source



3. Confirm the Date table is marked correctly:

Model view → Select Date table → Modeling → Mark as Date Table



4. Refresh the report:

Home → Refresh




Notes

If using Git for PBIX files, consider Git LFS or GitHub Releases.

Replace real or sensitive data with anonymized sample data before sharing publicly.



---

Data & Privacy

CityLifeData.xlsx is a sample dataset provided for learning purposes.

Typical tables include:

Sales (date, advisor, product, amount, withdrawals, risk level)

Products (product category, risk profile)

Advisors (advisor, team, region)

Date (Year, Month, Day, Fiscal attributes)



⚠️ Do not commit real client or production data to public repositories.


---

Key Pages & Dashboard Preview

Executive Overview

High-level KPIs and sales trends.



Wealth Dashboard

Performance analysis by product and advisor.



Insurance Dashboard

Insurance-specific insights and trends.




---

DAX Measures (Examples)

This project uses a dedicated Date table marked as the model date table.

Core Measures

Total Sales = SUM('Sales'[amount])

Total Withdrawals = SUM('Sales'[withdrawal_amount])

Net Contribution = [Total Sales] - [Total Withdrawals]

Time Intelligence

CY Sales =
CALCULATE(
    [Total Sales],
    YEAR('Date'[Date]) = YEAR(MAX('Date'[Date]))
)

PY Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR('Date'[Date])
)

YoY Sales % =
DIVIDE([CY Sales] - [PY Sales], [PY Sales], 0)

Using VARs for Readability

YoY Sales % (Clean) =
VAR CY = [CY Sales]
VAR PY = [PY Sales]
RETURN
DIVIDE(CY - PY, PY, 0)


---

Recommended Best Practices

Always create and mark a dedicated Date table

Use DAX variables (VAR) for readability

Apply consistent naming conventions for measures

Document Power Query transformations

Avoid storing large PBIX files directly in Git without LFS or Releases

Keep dashboards simple and focused on key insights



---

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


---

License

This project is licensed under the MIT License.
See the LICENSE file for details.


---

Contact

Developer: Vikas Giri
GitHub: https://github.com/Vikas-Giri
LinkedIn: https://linkedin.com/in/vikasgiri


---

✨ This project reflects my learning process and growing understanding of Power BI, DAX, and dashboard design.


---