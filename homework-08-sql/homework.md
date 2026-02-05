# Homework 8 - SQL

## Database
**Parch & Posey**

**Instructions**.
- Choose the exact answer or the closest option provided.
- Run query in any workspace in the Udacity sql course
  
<img width="812" height="560" alt="erd" src="https://github.com/user-attachments/assets/8d5ba74c-3485-401c-931b-d00bb354ce81" />


---


## Question 1
Which query correctly calculates the **average number of events per day per channel**?

```sql
A
SELECT channel, AVG(COUNT(*))
FROM web_events
GROUP BY channel;

B
SELECT channel, AVG(events)
FROM (
  SELECT DATE_TRUNC('day', occurred_at), channel, COUNT(*) events
  FROM web_events
  GROUP BY 1,2
) sub
GROUP BY channel;

C
SELECT AVG(events)
FROM web_events;

D
SELECT channel, COUNT(*)
FROM web_events
GROUP BY channel;
```
---

### Question 2
Which SQL concept allows complex logic to be written once and reused?
```sql
WITH tbl1_region_salesrep_with_total_sales AS (...)
```
A. View

B. Temporary table

C. CTE

D. Stored procedure

---
## Question 3
Which SQL query correctly compares each order’s total revenue to the next order’s total revenue using a window function?

The output must include:

- occurred_at
- total_amt_usd
- lead
- lead_difference

```sql
A
SELECT occurred_at,
       total_amt_usd,
       LEAD(total_amt_usd) OVER () AS lead,
       LEAD(total_amt_usd) OVER () - total_amt_usd AS lead_difference
FROM orders;

B
SELECT occurred_at,
       SUM(total_amt_usd) AS total_amt_usd,
       LEAD(SUM(total_amt_usd)) OVER (ORDER BY occurred_at) AS lead,
       LEAD(SUM(total_amt_usd)) OVER (ORDER BY occurred_at) - SUM(total_amt_usd) AS lead_difference
FROM orders
GROUP BY occurred_at;

C
SELECT occurred_at,
       total_amt_usd,
       LEAD(total_amt_usd) OVER (ORDER BY occurred_at) AS lead,
       LEAD(total_amt_usd) OVER (ORDER BY occurred_at) - total_amt_usd AS lead_difference
FROM (
    SELECT occurred_at,
           SUM(total_amt_usd) AS total_amt_usd
    FROM orders
    GROUP BY occurred_at
) sub;

D
SELECT occurred_at,
       total_amt_usd,
       total_amt_usd - LAG(total_amt_usd) OVER (ORDER BY occurred_at) AS lead_difference
FROM orders;
```
---

## Question 4
Which SQL query correctly calculates a running total of standard_amt_usd over time, without truncating dates?

The output must include:

The value added per row

The cumulative running total ordered by time
```sql
A
SELECT standard_amt_usd,
       SUM(standard_amt_usd)
FROM orders
GROUP BY occurred_at;

B
SELECT standard_amt_usd,
       SUM(standard_amt_usd) OVER () AS running_total
FROM orders;

C
SELECT standard_amt_usd,
       SUM(standard_amt_usd) OVER (ORDER BY occurred_at) AS running_total
FROM orders;

D
SELECT standard_amt_usd,
       SUM(standard_amt_usd) OVER (PARTITION BY occurred_at ORDER BY occurred_at) AS running_total
FROM orders;
```
---
## Question 5
For the region with the highest total sales (total_amt_usd), how many total orders were placed?

```sql

A
SELECT r.name, COUNT(o.id) AS total_orders
FROM orders o
JOIN accounts a ON o.account_id = a.id
JOIN region r ON r.id = a.region_id
GROUP BY r.name
ORDER BY SUM(o.total_amt_usd) DESC
LIMIT 1;

B
SELECT r.name, COUNT(o.total) AS total_orders
FROM sales_reps s
JOIN accounts a ON a.sales_rep_id = s.id
JOIN orders o ON o.account_id = a.id
JOIN region r ON r.id = s.region_id
GROUP BY r.name
HAVING SUM(o.total_amt_usd) = (
    SELECT MAX(SUM(total_amt_usd))
    FROM orders
);

C
WITH t1 AS (
    SELECT r.name AS region_name,
           SUM(o.total_amt_usd) AS total_amt
    FROM sales_reps s
    JOIN accounts a ON a.sales_rep_id = s.id
    JOIN orders o ON o.account_id = a.id
    JOIN region r ON r.id = s.region_id
    GROUP BY r.name
),
t2 AS (
    SELECT MAX(total_amt)
    FROM t1
)
SELECT r.name,
       COUNT(o.total) AS total_orders
FROM sales_reps s
JOIN accounts a ON a.sales_rep_id = s.id
JOIN orders o ON o.account_id = a.id
JOIN region r ON r.id = s.region_id
GROUP BY r.name
HAVING SUM(o.total_amt_usd) = (SELECT * FROM t2);

D
SELECT r.name, COUNT(o.id) AS total_orders
FROM region r
JOIN orders o ON r.id = o.region_id
WHERE o.total_amt_usd = (
    SELECT MAX(total_amt_usd)
    FROM orders
)
GROUP BY r.name;
```
---

## Question 6
Which situation most strongly requires using a CTE instead of a subquery?

A. One-line aggregation

B. Query used once

C. Complex logic reused multiple times

D. Simple filtering

---
## Question 7
Which group of companies is included in:

“Companies that spent more per order on average than the overall average”?

A. Bottom spenders

B. All companies

C. Only above-average spenders

D. Top 10 companies

---
## Question 8
What is the main readability advantage of CTEs?

A. Faster execution

B. Automatic indexing

C. Logical step-by-step breakdown

D. Reduced memory usage

---
## Question 9
Which query correctly computes the running total of standard paper revenue over time?
```sql
A
SELECT standard_amt_usd,
       SUM(standard_amt_usd) OVER() AS running_total
FROM orders;

B
SELECT standard_amt_usd,
       SUM(standard_amt_usd) OVER(ORDER BY occurred_at) AS running_total
FROM orders;

C
SELECT standard_amt_usd,
       SUM(standard_amt_usd) AS running_total
FROM orders;

D
SELECT standard_amt_usd,
       SUM(standard_amt_usd) OVER(PARTITION BY account_id) AS running_total
FROM orders;

```
---

## Question 10
Management wants to know the largest order per account. Which query is correct?
```sql
A
SELECT id, account_id, total,
       RANK() OVER(ORDER BY total DESC) AS total_rank
FROM orders;

B
SELECT id, account_id, total,
       RANK() OVER(PARTITION BY account_id ORDER BY total DESC) AS total_rank
FROM orders;

C
SELECT id, account_id, total,
       DENSE_RANK() OVER(PARTITION BY account_id ORDER BY total ASC) AS total_rank
FROM orders;

D
SELECT id, account_id, total,
       ROW_NUMBER() OVER(ORDER BY total DESC) AS total_rank
FROM orders;

```
---
## Question 11
How can you compare the revenue of an order to the next order?
```sql

A
SELECT occurred_at, total_amt_usd,
       LAG(total_amt_usd) OVER(ORDER BY occurred_at) AS prev_order
FROM orders;

B
SELECT occurred_at, total_amt_usd,
       LEAD(total_amt_usd) OVER(ORDER BY occurred_at) AS next_order
FROM orders;

C
SELECT occurred_at, SUM(total_amt_usd) AS total
FROM orders
GROUP BY occurred_at;

D
SELECT occurred_at, total_amt_usd,
       NTILE(100) OVER(ORDER BY total_amt_usd) AS percentile
FROM orders;
```
---
## Question 12
Which query divides accounts into quartiles based on standard_qty?
```sql
A
SELECT account_id, standard_qty,
       NTILE(4) OVER(ORDER BY standard_qty) AS standard_quartile
FROM orders;

B
SELECT account_id, standard_qty,
       RANK() OVER(PARTITION BY account_id ORDER BY standard_qty) AS standard_quartile
FROM orders;

C
SELECT account_id, standard_qty,
       SUM(standard_qty) OVER(PARTITION BY account_id) AS standard_quartile
FROM orders;

D
SELECT account_id, standard_qty,
       ROW_NUMBER() OVER(ORDER BY standard_qty) AS standard_quartile
FROM orders;

```
---
## Question 13
Which query correctly calculates the difference from the previous order’s revenue?
```sql

A
SELECT occurred_at, total_amt_usd,
       LAG(total_amt_usd) OVER(ORDER BY occurred_at) AS prev_order,
       total_amt_usd - LAG(total_amt_usd) OVER(ORDER BY occurred_at) AS diff
FROM orders;

B
SELECT occurred_at, total_amt_usd,
       LEAD(total_amt_usd) OVER(ORDER BY occurred_at) AS next_order
FROM orders;

C
SELECT account_id, SUM(total_amt_usd) OVER(PARTITION BY account_id) AS total
FROM orders;

D
SELECT account_id, total_amt_usd,
       ROW_NUMBER() OVER(ORDER BY total_amt_usd) AS rn
FROM orders;
```
---

## Question 14
Which query divides each account’s orders into 100 percentile levels based on total revenue?
```sql
A
SELECT account_id, total_amt_usd,
       NTILE(100) OVER(PARTITION BY account_id ORDER BY total_amt_usd) AS total_percentile
FROM orders;

B
SELECT account_id, total_amt_usd,
       RANK() OVER(PARTITION BY account_id ORDER BY total_amt_usd) AS total_percentile
FROM orders;

C
SELECT account_id, total_amt_usd,
       SUM(total_amt_usd) OVER(PARTITION BY account_id) AS total_percentile
FROM orders;

D
SELECT account_id, total_amt_usd,
       ROW_NUMBER() OVER(PARTITION BY account_id ORDER BY total_amt_usd) AS total_percentile
FROM orders;
```


