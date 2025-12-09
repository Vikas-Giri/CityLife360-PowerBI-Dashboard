---

📊 CityLife 360 – Power BI Dashboard

🚀 End-to-End Business Intelligence Project

A complete 360° analytical dashboard for Wealth & Insurance business units, designed for the VP of Sales at CityLife.

This Power BI report provides a consolidated and interactive view of business performance, using DAX time-intelligence, dynamic KPIs, and rich visual insights.


---

📁 Project Structure

CityLife360-PowerBI-Dashboard/
│── CityLife360_Project.pbix
│── CityLifeData.xlsx
│── README.md
└── images/
     ├── overview.png
     ├── sales_by_advisor.png
     ├── sales_by_product.png

---

🎯 Project Objectives

✔ Build an interactive multi-page Power BI dashboard
✔ Enable executives to track Sales, Withdrawals, Net Contribution
✔ Analyze performance across products, advisors, and risk levels
✔ Implement DAX time intelligence (CY, PY, YoY%)
✔ Create professional, clean UI using shapes & layouting
✔ Provide insights into Wealth and Insurance business units


---

📌 Dashboard Overview

⭐ Executive Summary Page

🔹 KPIs Included:

CY Sales

PY Sales

YoY % Growth

Total Withdrawals

Net Contribution

Total Products

Total Advisors


🔹 High-level visual insights:

Sales performance trend over time

Product category sales contribution

Advisor-wise performance

Risk level analysis


🖼 Screenshot




---

📈 Sales Trend Analysis

Shows daily/monthly movement in Sales using a line chart.




---

📦 Sales by Product

Highlights top and bottom performing products.




---

👨‍💼 Sales by Advisor

Ranks advisors by sales contribution.




---

⚠ Risk Level Distribution

Breaks down product risk categories (Low, Moderate, Variable, etc.)




---

🧠 DAX Measures Used

CY Sales

CY Sales = CALCULATE([Total Sales], YEAR('Sales'[record_date]) = YEAR(MAX('Sales'[record_date])))

PY Sales

PY Sales = CALCULATE([Total Sales], YEAR('Sales'[record_date]) = YEAR(MAX('Sales'[record_date])) - 1)

YoY Sales %

YoY Sales % = DIVIDE([CY Sales] - [PY Sales], [PY Sales])

Net Contribution

Net Contribution = [Total Sales] - [Total Withdrawals]

Current Date Fix (CONST Table)

Used to solve dynamic date issues for YoY calculations.


---

🛠 Tools & Skills Demonstrated

Microsoft Power BI

Power Query (data cleaning)

DAX (Time Intelligence, Measures)

Data Modeling

Business Analytics

Dashboard Design & UX

GitHub project documentation



---

👨‍💻 Developer

Vikas Giri
📌 GitHub: https://github.com/Vikas-Giri
🔗 LinkedIn: https://linkedin.com/in/vikasgiri

---

⭐ Summary

This project demonstrates real-world BI reporting skills by creating a polished, business-ready Power BI dashboard with advanced DAX metrics and clean UI design. It serves as a strong portfolio piece for Data Analyst / BI roles.


---
