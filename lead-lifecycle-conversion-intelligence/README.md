# Lead Lifecycle & Conversion Intelligence System
A business analytics project focused on analyzing closed-deal trends, lead types, business segments, business types, and sales representative performance using Python, SQL, and Power BI.

## Project Overview
This project explores the Olist closed-deals dataset to understand the distribution of closed deals across business categories, identify monthly trends, and examine sales representative performance. The analysis combines data cleaning, SQL-based querying, exploratory data analysis, and interactive Power BI dashboards to generate actionable business insights.

## Objectives
- Analyze closed deals across business segments and lead types.
- Examine monthly closed-deal trends and identify peak periods.
- Compare reseller and manufacturer business types.
- Evaluate closed-deal distribution across sales representatives.
- Build interactive dashboards to communicate key findings.
- Validate data quality and prepare a cleaned dataset for further analysis.

## Tools & Technologies
- **Python** — data processing and analysis
- **Pandas** — data cleaning and exploratory data analysis
- **SQL & SQLite** — querying and aggregating closed-deal records
- **Power BI** — interactive dashboard development
- **DAX** — measures and KPI calculations
- **Google Colab** — Python-based analysis environment

## Dataset
The project uses the Olist closed-deals dataset.

- **Total records:** 842
- **Unique lead identifiers:** 842
- **Business segments:** 34
- **Lead types:** 9
- **Sales representatives:** 22
- **Period analyzed:** December 2017 – November 2018

The dataset includes lead identifiers, sales representative identifiers, business segments, lead types, business types, deal dates, and declared business information.

## Project Workflow

1. **Data Cleaning:** Standardized categorical values, handled missing categorical fields, converted dates, and checked for duplicates.
2. **Exploratory Data Analysis:** Examined distributions across lead types, business segments, business types, and sales representatives.
3. **SQL Analysis:** Used SQLite queries to aggregate closed deals and compare category-level performance.
4. **Trend Analysis:** Analyzed monthly closed-deal counts to identify peak and declining periods.
5. **Power BI Dashboard:** Developed visualizations and KPI cards to communicate findings.
6. **Validation:** Checked record counts, unique identifiers, duplicate records, and missing dates.

## Key Findings

- **842 closed deals** were analyzed across the dataset.
- **Resellers accounted for 587 deals (69.71%)**, while manufacturers accounted for 242 deals (28.74%).
- **Online medium was the largest lead type**, representing 332 closed deals (39.43%).
- **Home decor was the leading business segment**, with 105 closed deals.
- **April 2018 was the peak month**, recording 207 closed deals.
- The monthly closed-deal count declined after April 2018, reaching 6 deals in November 2018.

These figures describe the distribution of recorded closed deals; they do not represent lead-conversion rates.

## Power BI Dashboard
The Power BI report contains two pages:

### Page 1 — Executive Overview
- Total closed deals
- Number of sales representatives
- Number of business segments and lead types
- Monthly closed-deal trend
- Closed deals by lead type
- Top business segments by closed deals
- Monthly date-range slicer

### Page 2 — Lead & Business Intelligence
- Closed deals by business type
- Closed deals by business segment and business type
- Top 10 sales representatives by closed deals
- Closed deals by lead type and business type
- KPI cards for reseller deals, manufacturer deals, top lead type, and top business segment

## Repository Contents
- `Lead Lifecycle & Conversion Intelligence System Dashboard.pbix` — Power BI dashboard
- `Lead Lifecycle Conversion Intelligence Project Report.pdf` — project report
- `Lead Lifecycle_cleaned data (1).csv` — cleaned dataset
- `Lead_Lifecycle_Conversion_Intelligence_colab.ipynb` — Google Colab notebook
- `README.md` — project documentation

## Business Value
This analysis helps explore which business segments and lead types contribute the largest shares of closed deals, how deal counts change over time, and how closed deals are distributed across sales representatives. These findings can support further investigation and data-informed business planning.

## Limitations
The available dataset contains closed deals only. It does not include all leads that failed to convert or a complete history of lead lifecycle stages. Therefore, actual conversion rates, funnel drop-off rates, and conversion efficiency cannot be calculated from this dataset alone.

Declared monthly revenue fields are also not treated as revenue earned from these deals.

## Future Improvements
- Integrate lead-level data that includes both converted and non-converted leads.
- Calculate actual conversion rates when suitable lead and lifecycle-stage data become available.
- Add more detailed time-based and sales performance analysis.
- Improve dashboard filtering and drill-down capabilities.
- Extend the analysis with additional business and revenue data.

## Author
**Mallikarjun**  
B.Tech — Computer Science & Engineering

**Project focus:** Data Analytics | SQL | Python | Power BI | Business Intelligence
