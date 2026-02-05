# Homework 7 - SQL

## Database
**Parch & Posey**

**Instructions**.
- Choose the exact answer or the closest option provided.
- Run query in any workspace in the Udacity sql course
- 
<img width="812" height="560" alt="erd" src="https://github.com/user-attachments/assets/1a98a129-81e5-47fb-9b6e-7c23b1db218d" />


---


## Question 1
What is the **total amount of poster paper** ordered across all orders?

- A. 204,395  
- B. 723,646  
- C. 887,535  
- D. 391,611  

---

##  Question 2
What is the **earliest date** an order was placed?

- A. 2013-12-04  
- B. 2014-01-01  
- C. 2015-02-11  
- D. 2013-11-25  

---

##  Question 3
Which query correctly finds the **earliest order date WITHOUT using an aggregation function**?

```sql
A
SELECT MIN(occurred_at)
FROM orders;

B
SELECT *
FROM orders
ORDER BY occurred_at
LIMIT 1;

C
SELECT occurred_at
FROM orders
GROUP BY occurred_at;

D
SELECT *
FROM orders
WHERE occurred_at IS NOT NULL;
```

---

## Question 4
What is the most recent web event date?

A. 2017-01-01

B. 2016-12-31

C. 2017-01-02

D. 2016-11-30

---
## Question 5
Which query correctly returns the account name and date of the earliest order?

```sql
A
SELECT name, MIN(occurred_at)
FROM accounts
JOIN orders ON accounts.id = orders.account_id;

B
SELECT accounts.name, orders.occurred_at
FROM orders
JOIN accounts ON accounts.id = orders.account_id
ORDER BY occurred_at
LIMIT 1;

C
SELECT name, occurred_at
FROM accounts;

D
SELECT occurred_at
FROM orders
GROUP BY occurred_at;
```
---
## Question 6
Which account placed the earliest order?

A. Walmart

B. Staples

C. Exxon Mobil

D. Costco

---
## Question 7
Which query correctly finds total sales per account?

```sql
A
SELECT name, total_amt_usd
FROM accounts
JOIN orders;

B
SELECT name, SUM(total_amt_usd)
FROM accounts
JOIN orders ON accounts.id = orders.account_id
GROUP BY name;

C
SELECT SUM(total_amt_usd)
FROM orders;

D
SELECT name, COUNT(*)
FROM orders;
```
---

## Question 8
Which query correctly finds accounts with more than 20 orders?
```sql
A
WHERE COUNT(*) > 20;

B
GROUP BY accounts.id
HAVING COUNT(*) > 20;

C
HAVING total_amt_usd > 20;

D
WHERE orders > 20;
```
---

## Question 9
How many accounts have more than 20 orders?

A. 100

B. 120

C. 70

D. 15
---

## Question 10
Which query correctly returns channel usage counts, ordered from highest to lowest?

```sql
A
SELECT channel
FROM web_events;

B
SELECT channel, COUNT(*)
FROM web_events
GROUP BY channel
ORDER BY COUNT(*) DESC;

C
SELECT DISTINCT channel
FROM web_events;

D
SELECT channel, SUM(channel)
FROM web_events;
```
---

## Question 11
Which channel is used most frequently overall?

A. facebook

B. organic

C. adwords

D. direct

---
### Question 12
Which query correctly labels orders as Large (≥ 3000) or Small (< 3000)?
```sql
A
CASE
  WHEN total_amt_usd > 3000 THEN 'Large'
  
B
CASE
  WHEN total_amt_usd >= 3000 THEN 'Large'
  ELSE 'Small'
END

C
IF total_amt_usd > 3000

D
WHERE total_amt_usd > 3000;
```

