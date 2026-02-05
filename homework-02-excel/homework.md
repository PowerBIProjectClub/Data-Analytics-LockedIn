# Homework 2 - Excel
**Dataset:** Maven Analytics – Northwind Traders  (access in the folder)

---

##  Assessment Objective
This assessment evaluates your ability to:
- Build calculated columns
- Apply Excel formulas correctly
- Work with dates and time intervals
- Translate business questions into data logic

---

## Dataset Overview

You will work primarily with **two sheets**.

### Order_Details (Revenue Data)
| Column | Description |
|------|------------|
| OrderID | Unique order identifier |
| UnitPrice | Price per unit |
| Quantity | Units sold |
| Discount | Discount applied (decimal) |

---

### Orders (Order Timing & Delivery)
| Column | Description |
|------|------------|
| OrderID | Unique order identifier |
| OrderDate | Date order was placed |
| RequiredDate | Date order was required |
| ShippedDate | Date order was shipped |

 **Important**
- Revenue calculations come from `Order_Details`
- Date calculations come from `Orders`

---

## Required Setup (Do This First)

### Step 1: Create a Net Revenue Column
In the `Order_Details` table, add a new column called `Net_Revenue`.

This column should calculate the **actual revenue earned per order line after discount**.

---

## QUESTION 1 — Total Net Revenue
**What is the total net revenue generated across all order lines?**

A. $1,102,845  
B. $1,198,430  
C. $1,265,793  
D. $1,340,210  

---

## QUESTION 2 — Correct Net Revenue Formula
**Which Excel formula correctly calculates net revenue per order line?**

A. `=UnitPrice * Quantity - Discount`  
B. `=UnitPrice * (1 - Discount)`  
C. `=UnitPrice * Quantity * (1 - Discount)`  
D. `=(UnitPrice + Quantity) * Discount`  

---

##  Average Order Value (AOV)

Reminder:  
Average Order Value is calculated **per order**, not per order line.

---

## QUESTION 3 — Average Order Value
**What is the correct Average Order Value (AOV) for this dataset?**

A. $412.56  
B. $503.19  
C. $587.38  
D. $641.02  

---

## QUESTION 4 — Discounted Order Lines
**How many order lines have a discount greater than 10%?**

A. 624  
B. 703  
C. 781  
D. 842  

---

## Order Fulfillment Time
Fulfillment time is calculated as the number of days between:

OrderDate → ShippedDate

---

## QUESTION 5 — Typical Fulfillment Time
**What is the typical number of days it takes to ship an order?**

A. 5 days  
B. 7 days  
C. 9 days  
D. 12 days  

---

## Late Order Analysis

An order is considered **late** if:

ShippedDate > RequiredDate

---

## QUESTION 6 — Percentage of Orders Shipped Late
**What percentage of orders were shipped late?**

A. 4%  
B. 9%  
C. 13%  
D. 18%  

---

## QUESTION 7 — Late Order Flag Formula
**Which Excel formula correctly flags late orders?**

A. `=IF(ShippedDate < RequiredDate, 1, 0)`  
B. `=IF(ShippedDate > RequiredDate, 1, 0)`  
C. `=IF(RequiredDate > OrderDate, 1, 0)`  
D. `=IF(ShippedDate = RequiredDate, 1, 0)`  




