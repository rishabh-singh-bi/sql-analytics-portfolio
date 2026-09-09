# SQL Analytics Portfolio

A practical SQL portfolio focused on business data extraction, analytical querying, KPI analysis, and problem-solving for Business Intelligence and Operations Analytics.

This repository documents my progression from SQL fundamentals to more advanced analytical patterns using PostgreSQL-style SQL.

## Career Focus

**Rishabh Singh Chauhan**  
Business Analyst / Operations Data Analyst

New Delhi, India — Open to relocation to Helsinki, Finland 🇫🇮

Focus areas:
- Business Intelligence
- Operational analytics
- KPI reporting
- Customer and funnel analysis
- Process improvement
- Business data analysis

## Technical Competencies

### SQL Fundamentals
- SELECT
- WHERE
- DISTINCT
- ORDER BY
- LIMIT
- Filtering
- CASE statements

### Aggregation & Analysis
- COUNT
- SUM
- AVG
- MIN / MAX
- GROUP BY
- HAVING

### Relational Data
- INNER JOIN
- LEFT JOIN
- Multi-table JOINs
- JOIN-based filtering

### Advanced SQL
- CTEs / WITH clauses
- Subqueries
- Window functions
- ROW_NUMBER()
- RANK()
- PARTITION BY

## Repository Structure

```text
sql-analytics-portfolio/
├── README.md
├── hackerrank-challenges/
│   ├── basic-select/
│   ├── advanced-joins/
│   └── aggregations-and-subqueries/
├── sqlbolt-exercises/
│   ├── lessons-1-to-5-selects.sql
│   └── lessons-6-to-12-joins-and-aggregates.sql
└── case-studies/
    ├── 01_customer_churn_analysis.sql
    └── 02_attribution_and_funnel_metrics.sql
```

## Practice Areas

- [HackerRank — Basic Select](./hackerrank-challenges/basic-select/)
- [HackerRank — Advanced JOINs](./hackerrank-challenges/advanced-joins/)
- [HackerRank — Aggregations & Subqueries](./hackerrank-challenges/aggregations-and-subqueries/)
- [SQLBolt — SELECT exercises](./sqlbolt-exercises/lessons-1-to-5-selects.sql)
- [SQLBolt — JOINs & aggregates](./sqlbolt-exercises/lessons-6-to-12-joins-and-aggregates.sql)
- [Customer Churn Analysis](./case-studies/01_customer_churn_analysis.sql)
- [Attribution & Funnel Metrics](./case-studies/02_attribution_and_funnel_metrics.sql)

## Business Question → SQL

```text
Business Question
       ↓
Data Requirements
       ↓
SQL Query
       ↓
Result
       ↓
Business Interpretation
       ↓
Decision / Action
```

## Example: Customer Tiering with CTE + Window Function

```sql
WITH customer_revenue AS (
    SELECT
        customer_id,
        region,
        SUM(revenue) AS total_revenue
    FROM customer_transactions
    GROUP BY customer_id, region
),
ranked_customers AS (
    SELECT
        customer_id,
        region,
        total_revenue,
        RANK() OVER (
            PARTITION BY region
            ORDER BY total_revenue DESC
        ) AS regional_rank
    FROM customer_revenue
)
SELECT
    customer_id,
    region,
    total_revenue,
    regional_rank,
    CASE
        WHEN regional_rank <= 10 THEN 'Tier 1'
        WHEN regional_rank <= 50 THEN 'Tier 2'
        ELSE 'Tier 3'
    END AS customer_tier
FROM ranked_customers
ORDER BY region, regional_rank;
```

## SQL Development Roadmap

| Stage | Focus | Status |
|---|---|---|
| SQL Fundamentals | SELECT, WHERE, ORDER BY | 🔄 Learning |
| Aggregations | GROUP BY, HAVING | 🔄 Learning |
| JOINs | Multi-table querying | 🔄 Learning |
| Subqueries | Nested analytical logic | 🔄 Learning |
| CTEs | Structured analytical queries | 🔄 Learning |
| Window Functions | RANK, ROW_NUMBER | 🔄 Learning |
| Business Case Studies | Real-world analysis | ⬜ Planned |
| SQL Basic Certification | HackerRank | 🔄 In Progress |

## Tools

- PostgreSQL
- HackerRank
- SQLBolt
- GitHub
- Power BI
- Apache Superset

## Related BI Portfolio

```text
Data
 ↓
SQL / Querying
 ↓
Transformation
 ↓
KPI Analysis
 ↓
BI Dashboard
 ↓
Business Decision
```

## Author

**Rishabh Singh Chauhan**  
**BI & Analytics Specialist | Business Analyst / Operations Data Analyst**

New Delhi, India  
Open to relocation to Helsinki, Finland 🇫🇮

## Certifications

- Microsoft Power BI Data Analyst — PL-300 *(In progress)*
- SQL Basic Certification — HackerRank *(In progress)*
- Azure Data Fundamentals — DP-900 *(Planned)*

## Data & Portfolio Integrity

All datasets are for learning, demonstration, or portfolio purposes. No confidential, proprietary, personal, or employer-restricted data is included.

