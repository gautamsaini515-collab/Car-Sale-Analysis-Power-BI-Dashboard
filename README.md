# Car Sales Analysis Dashboard | Power BI

An interactive **Car Sales Analysis Dashboard** built with **Microsoft Power BI** to explore vehicle sales, brand and model performance, pricing, fuel types, vehicle segments, launch years, and other product-level insights.

The project is organized into four report views: **Car Sales Dashboard**, **Brand & Sales Analysis**, **Advanced Sales Analysis**, and **Car Sales Performance**.

> **Note:** The figures displayed in the screenshots are examples from the report at the time the screenshots were captured. They can change when slicers and filters are applied.

---

## Dashboard Preview

### 1. Car Sales Dashboard

![Car Sales Dashboard](images/01-car-sales-dashboard.png)

This page provides a high-level view of the car dataset. It includes:
- Fuel Type, Segment, and Launch Year filters.
- Brand logo/image navigation or selection area.
- Monthly Sales (Units) by Segment.
- Total Monthly Sales view for selected models.
- Price range display.
- Model/variant comparison.

### 2. Brand & Sales Analysis

![Brand and Sales Analysis](images/02-brand-sales-analysis.png)

This page focuses on comparing manufacturers and their models. It includes:
- Total Units Sold KPI.
- Brand slicer.
- Fuel Type slicer.
- Launch Year slicer.
- Average Car Price by Brand.
- Brand-wise Sales Distribution.
- Model-level sales comparison.
- Top 10 Brands by Units Sold.

### 3. Advanced Sales Analysis

![Advanced Sales Analysis](images/03-advanced-sales-analysis.png)

This page explores relationships and category-level performance. It includes:
- Launch Year and Brand comparison.
- Brand and Fuel Type comparison.
- Brand and Segment comparison.
- Average Price by Brand.
- Fuel Type, Brand, Launch Year, and Segment slicers.

### 4. Car Sales Performance

![Car Sales Performance](images/04-car-sales-performance.png)

This page combines KPI cards and performance charts. It includes:
- Total Units Sold, Brands, and Models.
- Average Price (Lakhs).
- Average Units per Record.
- Average Variants per Model.
- Total Units Sold by Launch Year.
- Segment Trend by Launch Year.
- Units Sold by Segment.
- Fuel Type Share of Units.
- Fuel Type Mix by Launch Year.
- Top 5 and Bottom 5 Models by Units Sold.
- Price vs Volume scatter plot.
- Units Sold by Brand.

---

## Project Objectives

The main objectives of this project are to:

1. Summarize car sales using key performance indicators (KPIs).
2. Compare sales performance across brands and models.
3. Understand how sales are distributed across fuel types and vehicle segments.
4. Explore the relationship between vehicle price and sales volume.
5. Compare vehicle records across launch years.
6. Provide interactive filters so users can explore different parts of the dataset.

## Key Business Questions

The dashboard is designed to help explore questions such as:

- How many brands and models are represented in the dataset?
- What is the total recorded monthly sales volume?
- Which brands have the highest and lowest sales?
- Which models have the highest and lowest sales?
- Which vehicle segment contributes the most units?
- Which fuel type has the largest share of recorded units?
- How do average vehicle prices compare across brands?
- What is the price range of the vehicles?
- How do sales records vary by launch year?
- Which models appear among the top 5 and bottom 5 by units sold?
- Is there an observable relationship between average price and sales volume?
- How do brand sales differ across fuel types and segments?

The answers depend on the current filter selection and the data available in the report.

## Tools & Technologies

- **Microsoft Power BI Desktop** — report creation and interactive visualizations.
- **Power Query** — data loading and preparation (where applied in the PBIX).
- **DAX** — measures and calculated fields used for KPIs and aggregations.
- **CSV / tabular source data** — vehicle attributes and sales-related fields.

## Data Fields Used

The report visuals indicate the use of fields including:

| Field | Purpose |
|---|---|
| Brand | Manufacturer-level analysis |
| Model | Model-level comparison |
| Fuel Type | Fuel category analysis |
| Segment | Vehicle category analysis |
| Launch Year | Year-based comparison |
| Monthly Sales (Units) | Sales volume aggregation |
| Variants | Variant-related analysis |
| Average Price / Price Range | Vehicle price analysis |

The exact field names and data types should be checked in the Power BI model. The README does not assume fields that are not visible in the report.

## KPIs and Calculations

The dashboard displays or supports metrics such as:

- **Total Units Sold** — sum of `Monthly Sales (Units)`.
- **Total Brands** — distinct count of `Brand`.
- **Total Models** — distinct count of `Model`.
- **Average Car Price** — average of the prepared average-price field.
- **Average Units per Record** — average of `Monthly Sales (Units)`.
- **Average Variants per Model** — average of the variants field, if numeric.
- **Top / Bottom Models** — models ranked by the selected sales aggregation.

Example DAX measures (adjust table and column names if your model uses different names):

```DAX
Total Units Sold =
SUM('Sheet1'[Monthly Sales (Units)])

Total Brands =
DISTINCTCOUNT('Sheet1'[Brand])

Total Models =
DISTINCTCOUNT('Sheet1'[Model])

Average Units per Record =
AVERAGE('Sheet1'[Monthly Sales (Units)])
```

If the model contains a numeric `Average Price` column:

```DAX
Average Car Price =
AVERAGE('Sheet1'[Average Price])
```

If price is stored as a text range (for example, `3.50 - 8.50`), it must be cleaned and split into numeric minimum and maximum price values before calculating averages. Do not average the original text range directly.

## Interactivity

The report includes slicers/filters such as:

- Brand
- Fuel Type
- Segment
- Launch Year

Selecting a slicer filters the connected visuals, allowing users to compare brands, models, categories, and years dynamically. Some pages may use different combinations of slicers depending on the analysis.

## How to Open the Project

1. Download or clone this repository.
2. Install **Microsoft Power BI Desktop**.
3. Open `Car-Sales-Dashboard.pbix` in Power BI Desktop.
4. If Power BI asks for the source data, select the correct source file and update the source path in **Transform data → Data source settings**.
5. Select **Refresh** to reload the data.
6. Use the slicers to interact with the report.

> The PBIX file is included in this repository package. The original source dataset is not included here, so you may need to reconnect it on your computer if the PBIX uses a local file path.

## Repository Structure

```text
Car-Sales-Power-BI-Project/
│
├── Car-Sales-Dashboard.pbix
├── README.md
└── images/
    ├── 01-car-sales-dashboard.png
    ├── 02-brand-sales-analysis.png
    ├── 03-advanced-sales-analysis.png
    └── 04-car-sales-performance.png
```

## Current Scope & Limitations

This report analyzes the fields available in the vehicle dataset. It should not be interpreted as a full transaction-level business intelligence system.

Unless the source data contains the required columns and records, the current dataset cannot reliably calculate:
- Actual monthly or quarterly historical revenue trends.
- Profit, profit margin, or operating costs.
- Customer-level purchase behavior.
- City/state/region sales performance.
- Discounts, payment methods, or delivery performance.

Also, `Launch Year` describes the vehicle's launch year; it is not automatically the date on which a sale occurred. A true month-over-month or quarter-over-quarter sales trend requires transaction dates or a properly defined sales-period field.

## Future Improvements

- Add a verified transaction-date table for genuine monthly and quarterly sales trends.
- Add revenue, cost, and profit measures if those fields become available.
- Add geography and customer analysis when suitable data is available.
- Improve tooltip pages and drill-through navigation.
- Add dynamic titles and richer KPI comparisons.
- Publish the report to Power BI Service, subject to workspace and licensing access.

## Author

**Your Name**  
Power BI | Data Analysis | Data Visualization

---

If you use or adapt this project, please update the author details and dataset/source information to match your work.
