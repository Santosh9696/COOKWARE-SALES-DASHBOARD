[README.md](https://github.com/user-attachments/files/28084621/README.md)
# 📊 Sales & Inventory Dashboard — Cookware Business (Power BI)

![Dashboard Preview](dashboard_screenshot.png)

## 🧩 Problem Statement

A family-owned cookware business was managing all sales operations manually — tracking orders, customer purchases, and product performance through raw Excel files. There was no visibility into:

- Which products were selling the most (and which were sitting idle)
- Which customers were driving the most revenue
- How sales were trending month over month
- Whether payments were being collected on time

Decisions were being made on gut feeling rather than data. The goal was to fix that.

---

## 💡 Solution

Built an **interactive Power BI dashboard** that transforms raw sales transaction data into clear, actionable business insights — enabling the business owner to make faster, data-driven decisions without touching a single spreadsheet manually.

---

## 📁 Dataset Overview

| Field | Description |
|---|---|
| Date | Transaction date |
| Customer Name | Name of the buyer |
| Product | Cookware product sold (KD, DT, CT, F.Pan, T.Pan, Appam, Grill Pan etc.) |
| Category | Product category (Ceramic) |
| Size | Product size (220mm, 240mm, 2LTR etc.) |
| Thickness | Product thickness (2.6mm, 4mm) |
| Quantity | Units sold per transaction |
| Amount | Unit price |
| Line Total | Total value of the transaction |

**Total Records:** 1,100+ rows of real transaction data spanning 8+ months

---

## 🔧 Tools & Technologies

| Tool | Usage |
|---|---|
| **Power BI Desktop** | Dashboard development & visualization |
| **Power Query** | Data cleaning & transformation |
| **DAX** | Custom KPI measures & calculations |
| **Microsoft Excel** | Source data format |

---

## 🧹 Data Cleaning (Power Query)

- Standardized inconsistent date formats (Excel serial numbers → proper dates)
- Normalized customer name casing (e.g. "Subodh Ji", "SUBODH JI" → unified)
- Removed duplicate and incomplete transaction rows
- Split payment data from sales data into separate structured tables
- Created calculated columns for Month, Year, and Quarter for time-based analysis

---

## 📐 DAX Measures

```dax
Total Revenue = SUM('sales data(Sheet1) (2)'[Line_Total])
```

```dax
Total Orders = COUNTROWS('sales data(Sheet1) (2)')
```

```dax
Total Customers = DISTINCTCOUNT('sales data(Sheet1) (2)'[Customer_Name])
```

```dax
Monthly Growth = 
VAR CurrentMonth = SUM('sales data(Sheet1) (2)'[Line_Total])
VAR LastMonth = 
    CALCULATE(
        SUM('sales data(Sheet1) (2)'[Line_Total]),
        DATEADD('sales data(Sheet1) (2)'[Date], -1, MONTH)
    )
RETURN DIVIDE(CurrentMonth - LastMonth, LastMonth) * 100
```

---

## 📊 Dashboard Features

### KPI Cards
- **Total Revenue** — ₹1.40M+ revenue tracked
- **Total Customers** — 28 unique buyers
- **Total Orders** — 1,000+ transactions

### Visualizations
- **Sales by Product** — Horizontal bar chart ranking all products by revenue (DT leads)
- **Sales by Month** — Line chart showing monthly sales trends with Month-over-Month growth
- **Sales by Top Customer** — Bar chart identifying highest-value customers (Amrit Ji, Subodh Ji)
- **Month Slicer** — Interactive filter to drill into any specific month

---

## 📈 Business Impact

| Insight | Action Taken |
|---|---|
| DT (Deep Tawa) was the top-selling product | Increased stock priority for DT |
| Appam & Grill Pan had lowest sales volume | Identified as slow-moving inventory |
| Amrit Ji & Pankaj Ji were top customers | Prioritized relationship management |
| Monthly Growth measure revealed seasonal dips | Helped plan restocking and promotions |

> **Result:** Replaced manual Excel-based reporting with an automated, interactive dashboard — reducing reporting time from hours to minutes and giving the business owner real-time visibility into performance.

---

## 🚀 How to Run

1. Download the `.pbix` file from this repository
2. Open with **Power BI Desktop** (free download from Microsoft)
3. The dashboard loads with all data pre-connected
4. Use the **Month slicer** to filter by specific time periods

---

## 👤 Author

**Santosh Jaiswal**  
Data & Business Analyst | Mumbai, India  
[LinkedIn](https://linkedin.com/in/your-profile) • [GitHub](https://github.com/Santosh9696)
