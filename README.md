# Retail Sales & Pricing Analytics (Power BI)
### Where discounts help, where they hurt, and which regions earn their sales

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Power Query](https://img.shields.io/badge/Power%20Query-217346?style=flat-square&logo=microsoft&logoColor=white)

**Troy Dela Rosa** | Independent academic project, Data Management (COMP-2702), Red River College Polytechnic | Apr 2026
<!-- [CONFIRM] Course and date for the Power BI report. If the Jan 2026 Orange Data Mining work was a different course, it is described separately below. -->

**Data:** Superstore sample retail dataset (Kaggle): 9,994 order lines, 2014 to 2017, four U.S. regions, three product categories.

---

## The business question

A retailer can grow sales by discounting, but discounts come straight out of margin. This report asks:

> **Which regions and categories are earning their sales, and where is discounting costing more than it brings in?**

---

## Key findings

**1. The deepest discounts came with the weakest margin.**
Central gave the highest average discount (24%) and earned the lowest profit margin of any region (7.9%). The West gave the lowest average discount (11%) and earned the best margin (14.9%) on the highest sales ($725K).

| Region | Total sales | Average discount | Profit margin |
|---|---:|---:|---:|
| West | $725K | 10.9% | 14.9% |
| East | $679K | 14.5% | 13.5% |
| Central | $501K | 24.0% | 7.9% |
| South | $392K | 14.7% | 11.9% |
| **Total** | **$2.30M** | | **12.5%** |

**2. Furniture sells, but barely makes money.**
Furniture brought in $739K in sales at a 2.5% margin, compared with about 17% for Office Supplies and Technology. In Central, furniture sales lost money (−1.9% margin).

**3. Sales grew, with a strong end-of-year peak.**
Annual sales rose from $471K (2015) to $733K (2017). Every region's sales peaked in September and again in November or December, and Q4 was the strongest quarter for every category.

![Sales by Region](images/02_sales_by_region.png)

---

## What I'd recommend

1. **Review Central's discounting first, starting with furniture.** It has the deepest discounts, the lowest margin, and the only category-region combination that loses money.
2. **Use the West as the benchmark.** It shows that higher sales don't require deeper discounts in this data.
3. **Plan inventory and staffing around September and Q4,** when sales peak in every region.
4. **Test before changing prices.** These are patterns in historical data, not proof that discounts caused the lower margins. A controlled discount test in one region would confirm it.

---

## The report (5 pages)

| Page | What it answers |
|---|---|
| Dashboard | Overall sales, profit, units and discount; sales by state, year and category |
| Sales by Region | How sales, discount and margin compare across regions and categories |
| Sales Trends | Monthly sales by region with moving averages, filterable by year and region |
| Category Performance | Sales by quarter, category and sub-category |
| Certified Visual | (not shown) |

<details>
<summary><b>More screenshots</b></summary>

<br/>

**Dashboard**
![Dashboard](images/01_dashboard.png)

**Sales Trends by Region**
![Sales trend by region](images/03_sales_trend_by_region.png)

**Category Performance**
![Category performance](images/04_category_performance.png)

</details>

---

## How it was built

- **Data model:** transformed the 9,994-row sales file into a star schema in Power Query, splitting, typing and deduplicating customer, product and location dimensions, with a DAX date table.
- **Measures:** DAX measures for sales, profit, margin, distinct orders and year-over-year growth (`SAMEPERIODLASTYEAR`).
- **Report design:** 5 pages with KPI cards, year and region slicers, and insight-style chart titles that state the finding rather than just the metric.
- **Publishing:** published to Power BI Service.

---

## Earlier exploratory modeling

Before building the report, I explored the same data in **Orange Data Mining**, comparing a Linear Regression baseline with a Random Forest model for predicting sales, and looked at how discount levels relate to profit.

<!-- [NEEDS EVIDENCE] The earlier README claimed ~23% (Linear Regression) vs ~70% (Random Forest) variance explained and r ≈ 0.83. Only add these back if you still have the Orange workflow or output, and check first which features the model used: if Profit was an input, the 70% is leakage (profit is calculated from sales). -->

---

## Limitations

- **Practice dataset.** Superstore is a widely used sample dataset, not a real company's data.
- **Patterns, not causes.** The link between discounts and margin is a correlation across regions and categories.
- **Data quality.** About $9.9K of sales has a blank category, and the year slicers include 2018 although the data ends in 2017. Both are being cleaned up.
- **Report naming.** The "Category Performance" page is titled for the West region, but its totals ($2.30M sales) match the whole company, so it appears to be unfiltered.

---

## Tools

Power BI Desktop, Power BI Service, Power Query, DAX, Orange Data Mining (exploration)
