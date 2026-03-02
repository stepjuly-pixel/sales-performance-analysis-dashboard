# Sales Performance Analysis Dashboard

## Project Overview

This project analyzes transactional sales data and presents key business metrics in an interactive Tableau dashboard.
The dataset was built by joining order, product, session, and geographic data in BigQuery, creating an aggregated reporting dataset.

The objective was to:

- Monitor revenue and order trends over time

- Identify top-performing product categories and individual products

- Compare geographic sales distribution

- Analyze device-level performance

## Tools & Technologies

- SQL (BigQuery)

- Tableau Public

## Database Structure

The analysis is based on four core tables from a relational database:

- `order` – transactional data (session ID, item ID)

- `session` – session ID and date

- `product` – product details (name, category, price)

- `session_params` – session-level attributes (country, device)

### Database Schema

<img src="docs/database_schema.png" width="800" />

## Data Preparation (SQL Layer)

[View SQL Query](sql/sales_aggregation_query.sql)

The reporting dataset was created using a SQL aggregation query that:

- Linked orders to sessions via `ga_session_id`

- Enriched with product information (category, name, price) via `item_id`

- Added geographic and device attributes from `session_params`

- Calculated revenue as `SUM(price)` and order volume as `COUNT(ga_session_id)`

- Aggregated by date, country, device, category, and product

## Dashboard

<img src="screenshots/dashboard_preview.png" width="800" />

The dashboard includes:

- **KPI Overview** — Total Revenue ($31,971,731) and Total Orders (33,538)

- **Time Series** — revenue and order trends over time

- **Category Performance** — revenue and order count by product category

- **Geographic Analysis** — country-level revenue distribution (world map)

- **Device Analysis** — revenue and order count by device type (desktop, mobile, tablet)

- **Product Ranking** — Top 20 products by order volume and Top 20 by revenue

🔗 [Interactive dashboard on Tableau Public](https://public.tableau.com/shared/6K54D5RBK?:display_count=n&:origin=viz_share_link)

## Key Insights

- Total Revenue: **$31,971,731** across **33,538** orders

- Top category by revenue: **Sofas & armchairs** ($8,388,255 / 4,301 orders), followed by **Chairs** ($6,147,749) and **Beds** ($4,919,725)

- Top product by revenue: **GRÖNLID** ($2,299,190), top by orders: **BESTÅ** (1,257)

- Revenue and order trends move consistently, indicating stable conversion patterns

- Sales are geographically concentrated in **North America** and **Europe**

- Desktop generates higher total revenue compared to mobile and tablet

- Some products rank high in order volume but lower in revenue (e.g. BESTÅ), suggesting price positioning differences

## How to Run

1. Clone this repository

2. Open [`sql/sales_aggregation_query.sql`](sql/sales_aggregation_query.sql) to review the BigQuery query

3. Explore the [interactive dashboard on Tableau Public](https://public.tableau.com/shared/6K54D5RBK?:display_count=n&:origin=viz_share_link) or download the [`.twbx` file](dashboard/sales_dashboard.twbx) to open in Tableau

## Project Structure

```
sales-performance-analysis-dashboard/
├── sql/
│   └── sales_aggregation_query.sql
├── docs/
│   └── database_schema.png
├── dashboard/
│   └── sales_dashboard.twbx
├── screenshots/
│   └── dashboard_preview.png
└── README.md
```
