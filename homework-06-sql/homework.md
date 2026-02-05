# Homework 6 - SQL

## Database
**Parch & Posey**

**Instructions**.
- Choose the exact answer or the closest option provided.
- Run query in any workspace in the Udacity sql course

<img width="812" height="560" alt="erd" src="https://github.com/user-attachments/assets/1815db0e-64c0-463a-b5a4-03aafee435fd" />

---

## Question 1
What is the `account_id` of the earliest order in the `orders` table?

- A. 1001  
- B. 100  
- C. 2861  
- D. 321  

---

## Question 2
Which query correctly returns the **5 smallest orders** by `total_amt_usd`, showing `id`, `account_id`, and `total_amt_usd`, **where `total_amt_usd` is greater than 0**?

```sql
A
SELECT id, account_id, total_amt_usd
FROM orders
LIMIT 5;

B
SELECT id, account_id, total_amt_usd
FROM orders
ORDER BY total_amt_usd DESC
LIMIT 5;

C
SELECT id, account_id, total_amt_usd
FROM orders
WHERE total_amt_usd > 0
ORDER BY total_amt_usd
LIMIT 5;

D
SELECT id, account_id, total_amt_usd
FROM orders
WHERE total_amt_usd < 5;

```
---
## Question 3
How many orders have either gloss_qty or poster_qty exceeding 4000 units?

A. 12

B. 7

C. 14

D. 5

## Question 4
Which query correctly returns all web events that are NOT organic or adwords?

```sql
A
SELECT *
FROM web_events
WHERE channel != 'organic' OR 'adwords';

B
SELECT *
FROM web_events
WHERE channel NOT IN ('organic','adwords');

C
SELECT *
FROM web_events
WHERE channel LIKE '%organic%';

D
SELECT *
FROM web_events
WHERE channel = 'direct';
```

----
## Question 5
What is the primary point of contact for Walmart?

A. Tamara Tuma

B. Mark Stevens

C. Sung Shields

D. Robert Lee

---

## Question 6
Which channel was used in the most recent web event for Walmart?

A. organic

B. adwords

C. direct

D. facebook

---

## Question 7
Which query correctly returns region name, sales rep name, and account name, sorted alphabetically by account name?

```sql
A
SELECT region.name, sales_reps.name, accounts.name
FROM region
JOIN accounts ON region.id = accounts.id
ORDER BY accounts.name;

B

SELECT r.name AS region_name,
       s.name AS sales_rep_name,
       a.name AS account_name
FROM region r
JOIN sales_reps s ON r.id = s.region_id
JOIN accounts a ON a.sales_rep_id = s.id
ORDER BY a.name;

C
SELECT *
FROM accounts
JOIN region;

D
SELECT name
FROM region;
```

---

## Question 8
Which SQL query correctly retrieves orders where:

standard_qty = 0

AND either gloss_qty or poster_qty exceeds 1000

```sql

A
SELECT *
FROM orders
WHERE standard_qty = 0
AND gloss_qty > 1000
OR poster_qty > 1000;

B
SELECT *
FROM orders
WHERE standard_qty = 0
AND (gloss_qty > 1000 OR poster_qty > 1000);

C
SELECT *
FROM orders
WHERE standard_qty = 0
OR gloss_qty > 1000
AND poster_qty > 1000;

D
SELECT *
FROM orders
WHERE standard_qty > 0
AND poster_qty > 1000;
```
---

## Question 9
Which account placed the last order in 2015?

A. Walmart

B. Costco

C. Occidental Petroleum

D. Staples

---

## Question 10
A warehouse manager wants to identify all products with gloss_qty in the range 24 to 29 inclusive.
Which SQL query correctly returns this result?

```sql
A
WHERE gloss_qty > 24 AND gloss_qty < 29;

B
WHERE gloss_qty BETWEEN 24 AND 29;

C
WHERE gloss_qty = 24 OR 29;

D
WHERE gloss_qty IN (25,28);
```
---
## Question 11
Which query finds companies that:

Start with C or W

primary_poc contains ana or Ana

Does NOT contain eana
```sql

A
WHERE name LIKE 'C%' OR 'W%'
AND primary_poc LIKE '%ana%';

B
WHERE (name LIKE 'C%' OR name LIKE 'W%')
AND (primary_poc LIKE '%ana%' OR primary_poc LIKE '%Ana%')
AND primary_poc NOT LIKE '%eana%';

C
WHERE name IN ('C','W');

D
WHERE primary_poc = 'ana';
```

