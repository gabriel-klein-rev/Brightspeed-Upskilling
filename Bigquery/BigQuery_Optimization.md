
# BigQuery Optimization Techniques

This document provides explanations and examples for the following BigQuery topics:

1. Common Table Expressions (CTEs)
2. Temporary Tables
3. Query Optimization Techniques
4. Cost Reduction Strategies

---

## 1. Common Table Expressions (CTEs) in BigQuery

### Definition:
A **Common Table Expression (CTE)** is a temporary result set that you can reference within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. It helps simplify complex queries and improve readability.

### Syntax:
```sql
WITH cte_name AS (
  SELECT ...
)
SELECT * FROM cte_name;
```

### Example:
```sql
WITH region_sales AS (
  SELECT region, SUM(sales_amount) AS total_sales
  FROM `project.dataset.sales_data`
  GROUP BY region
)
SELECT * FROM region_sales
WHERE total_sales > 10000;
```

---

## 2. Temporary Tables in BigQuery

### Definition:
**Temporary tables** exist only during the session in which they are created. They are useful for breaking complex queries into stages or for debugging intermediate results.

### Syntax:
```sql
CREATE TEMP TABLE temp_table_name AS
SELECT ...
```

### Example:
```sql
CREATE TEMP TABLE top_customers AS
SELECT customer_id, SUM(purchase_amount) AS total
FROM `project.dataset.transactions`
GROUP BY customer_id
HAVING total > 1000;

SELECT * FROM top_customers
ORDER BY total DESC;
```

---

## 3. Query Optimization in BigQuery

### Goal:
Improve performance and reduce resource usage of queries.

### Techniques:

#### a. Avoid SELECT *
```sql
-- Inefficient
SELECT * FROM `project.dataset.table`;

-- Efficient
SELECT customer_id, purchase_amount FROM `project.dataset.table`;
```

#### b. Filter Early with WHERE
```sql
SELECT order_id, total_price
FROM `project.dataset.orders`
WHERE order_date >= '2024-01-01';
```

#### c. Use EXPLAIN to Analyze Execution Plan
```sql
EXPLAIN
SELECT customer_id, COUNT(*) FROM `project.dataset.transactions` GROUP BY customer_id;
```

#### d. Use Approximate Functions
```sql
-- Instead of COUNT(DISTINCT)
SELECT APPROX_COUNT_DISTINCT(user_id) FROM `project.dataset.events`;
```

#### e. Use Partitioned and Clustered Tables
```sql
-- Create a partitioned and clustered table
CREATE TABLE `project.dataset.partitioned_sales`
PARTITION BY DATE(sale_date)
CLUSTER BY region
AS
SELECT * FROM `project.dataset.sales_data`;
```

---

## 4. Cost Reduction Strategies in BigQuery

### Pricing Model:
- **On-Demand**: Charged per amount of data processed.
- **Flat-Rate**: Fixed monthly price for dedicated slots.

### Tips to Reduce Costs:

#### a. Use --dry_run to Estimate Costs
```bash
bq query --use_legacy_sql=false --dry_run 'SELECT customer_id FROM `project.dataset.customers`'
```

#### b. Select Only Needed Columns
```sql
SELECT customer_id FROM `project.dataset.customers`; -- Better than SELECT *
```

#### c. Filter Data with WHERE Clauses
```sql
SELECT * FROM `project.dataset.logs`
WHERE timestamp >= '2024-01-01';
```

#### d. Use Approximate Aggregations
```sql
SELECT APPROX_COUNT_DISTINCT(session_id) FROM `project.dataset.sessions`;
```

#### e. Use Partitioned Tables
```sql
SELECT * FROM `project.dataset.partitioned_logs`
WHERE DATE(timestamp) = '2024-01-01';
```

#### f. Cluster Tables on Common Filter Columns
```sql
CREATE TABLE `project.dataset.clustered_sales`
CLUSTER BY product_id
AS
SELECT * FROM `project.dataset.sales_data`;
```

#### g. Materialized Views
```sql
CREATE MATERIALIZED VIEW `project.dataset.mv_sales_summary` AS
SELECT region, SUM(sales_amount) AS total_sales
FROM `project.dataset.sales_data`
GROUP BY region;
```

---

## Summary

| Topic | Purpose | Key Syntax |
|-------|---------|------------|
| CTEs | Simplify and organize complex queries | `WITH cte AS (...) SELECT * FROM cte` |
| Temp Tables | Store intermediate results temporarily | `CREATE TEMP TABLE ... AS SELECT ...` |
| Optimization | Improve query performance | Avoid SELECT *, use WHERE, EXPLAIN |
| Cost Reduction | Minimize query costs | dry_run, partitioning, clustering |

