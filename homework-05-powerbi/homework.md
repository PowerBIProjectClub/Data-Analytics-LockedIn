# Homework 5 - Power BI

## Dataset Overview
You will work with a food delivery orders dataset containing:
* **Order timestamps** (customer order time, restaurant time, driver arrival, delivery time)
* **Financial values** (sub total, fees, discounts, tips, refunds)
* **Operational attributes** (driver, restaurant, customer, delivery area, ASAP flag)

---

## Step 1: Load & Profile the Data

### 1.1 Load the Dataset
1.  Open **Power BI Desktop**.
2.  Select **Get Data** → **Excel / CSV** (depending on file format).

### 1.2 Data Profiling (Power Query)

1.  Click **Transform Data** to open Power Query.
2.  Turn on:
    * Column quality
    * Column distribution
    * Column profile
3.  For each column, identify:
    * Data type
    * Missing values
    * Invalid values
    * Cardinality (unique vs repeated values)

---

## Step 3: Data Modelling (Required Before Answering DAX Questions)
*This section explains how the data should be modelled and why.*

### 3.1 Identify the Fact Table (Orders)
The **Orders** table is your Fact table.
* It must remain at **transaction grain**:
    * One row = one order
    * No aggregation
    * No duplicate records
* The Fact table should contain:
    * Every column **except** Driver Name and Restaurant Name

> **Do NOT:**
> * Aggregate the data
> * Split the fact table into multiple tables
> * Remove rows unless duplicates are proven

### 3.2 Create Dimension Tables (One Purpose Each)
Create the following Dimension tables from the Orders table:

* **DimDriver**
    * Driver ID (Primary Key)
    * Driver Name
* **DimRestaurant**
    * Restaurant ID
    * Restaurant Name

**Each dimension table must:**
* Contain unique values only.
* Have no financial or calculated metrics.
* Use **Remove Duplicates** under Remove Rows in Power Query.

### 3.3 Create a Date Dimension (Mandatory)
Create a dedicated `DimDate` table using DAX.

**Minimum required columns:**
* Date (Primary Key)
* Year
* Month
* Month Number
* Year-Month

**This table must:**
* Cover the full date range of Orders.
* Be marked as a **Date table**.
* **❌ Do NOT** use auto date/time for this assessment.

**DAX Formula:**
```dax
DimDate =
ADDCOLUMNS(
    CALENDAR(DATE(2020, 1, 1), DATE(2020, 4, 30)),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Year-Month", FORMAT([Date], "YYYY-MM"),
    "Quarter", "Q" & FORMAT([Date], "Q"),
    "Day", DAY([Date]),
    "Weekday Number", WEEKDAY([Date], 2),  // 2 = Monday = 1
    "Weekday Name", FORMAT([Date], "dddd")
)
Do not forget to mark DimDate as a Date Table.

```

### 3.4 Build Relationships (Star Schema Rules)
In **Model View**, create the following relationships:

* `DimDriver[Driver ID]` → `Orders[Driver ID]`
* `DimRestaurant[Restaurant ID]` → `Orders[Restaurant ID]`
* `DimDate[Date]` → `Orders[Date]`

**Relationship rules:**
* One-to-Many (1:*), Dimension → Fact
* Single-direction filtering
* No bi-directional filters
* No many-to-many relationships

### 3.5 Model Validation Checklist
Before answering any DAX questions, confirm:

- [ ] Orders is the only fact table
- [ ] All dimensions contain unique keys
- [ ] No calculated columns for KPIs
- [ ] All measures live in a dedicated Measures table
- [ ] Filtering DimArea correctly affects Total Orders
- [ ] Filtering DimDate correctly affects revenue
- [ ] If your answers do not match the MCQ options, check your model first.

> **Why This Matters:** Incorrect modelling will cause wrong Total Orders, incorrect revenue figures, misleading averages, and broken filters.

---

## Step 4: DAX Measures for Business Questions
Create all measures in a dedicated table called `_Measures`. **Do NOT create calculated columns for KPIs.** All calculations must be measures.

### 4.1 Core Metrics (Defined Measures)

**Total Orders**
```dax
Total Orders =
COUNTROWS(Orders)
Sub Total Amount


Sub Total Amount =
SUM(Orders[Sub Total])
Delivery Fees


Delivery Fees =
SUM(Orders[Delivery fee])
Service Fees


Service Fees =
SUM(Orders[Service fee])
Total Fees


Total Fees =
[Delivery Fees] + [Service Fees]
Total Discounts


Total Discounts =
SUM(Orders[Discount])
Total Tips


Total Tips =
SUM(Orders[Tip])
Refunded Amount


Refunded Amount =
SUM(Orders[Refunded amount])
Gross Revenue


Gross Revenue =
[Sub Total Amount] + [Total Fees] + [Total Tips]
Net Revenue


Net Revenue =
[Gross Revenue] - [Total Discounts] - [Refunded Amount]
4.2 Operational Performance Measures
ASAP Orders


ASAP Orders =
CALCULATE(
    [Total Orders],
    Orders[ASAP] = "Yes"
)
ASAP Orders %


ASAP Orders % =
DIVIDE(
    [ASAP Orders],
    [Total Orders]
)
```

### 4.3 Business Insight Measures
```dax

Revenue per Order =
DIVIDE(
    [Net Revenue],
    [Total Orders]
)


Refund Rate % =
DIVIDE(
    CALCULATE(
        [Total Orders],
        Orders[Refunded amount] > 0
    ),
    [Total Orders]
)
```

**Business Questions These Measures Answer**
- How many orders are we fulfilling?
- How much revenue are we generating after discounts and refunds?
- Are ASAP orders actually delivered faster?
- Which drivers and areas perform best operationally?
- What percentage of orders meet our delivery SLA?


## Assessment Questions
### Q1. Total Orders
After loading the dataset and removing duplicate records, what is the total number of orders returned by this measure?

A. 50,300

B. 72,314

C. 10,487

D. 72,110


### Q2. Total Orders by Delivery Area
Using the existing measure Total Orders, apply a report-level filter where Delivery Area = “Hayward”. What value does Total Orders return?

A. 24,000

B. 24,229

C. 24,085

D. 24,228


### Q3. Gross Revenue
Create the following measures:

```dax
Sub Total Amount = SUM(Orders[Sub Total])

Total Fees = SUM(Orders[Delivery fee]) + SUM(Orders[Service fee])

Total Tips = SUM(Orders[Tip])

Gross Revenue = [Sub Total Amount] + [Total Fees] + [Total Tips]
```
Using the Gross Revenue measure, what is the total Gross Revenue?

A. 8,129,883.19

B. 1,412,605.88

C. 1,439,774.51

D. 8,462,908.67


### Q4. Net Revenue
Using the previously created Gross Revenue measure, create:

``` dax
Total Discounts = SUM(Orders[Discount])

Refunded Amount = SUM(Orders[Refunded amount])

Net Revenue = [Gross Revenue] - [Total Discounts] - [Refunded Amount]
```
After accounting for discounts and refunds, what is the Net Revenue?

A. 7,802,409.19

B. 1,308,917.29

C. 1,326,402.10

D. 7,349,776.55


### Q5. ASAP Orders Percentage
Create the following measures:

```dax
ASAP Orders =
CALCULATE(
    [Total Orders],
    Orders[ASAP] = "Yes"
)

ASAP Orders % =
DIVIDE(
    [ASAP Orders],
    [Total Orders]
)
```
What percentage of orders were marked as ASAP?

A. 52.3%

B. 58.9%

C. 64.7%

D. 79.85%

### Q6. Area Performance (Net Revenue)
Using the previously defined Net Revenue measure, analyze Net Revenue by Delivery Area. Which delivery area generates the highest Net Revenue, and what is the value?

A. Fremont — 3,412,884.22

B. Hayward — 2,617,914.56

C. Union City — 3,412,884.22

D. Fremont — 458,672.91


### Q7. Refund Rate
Create the following measure:

``` dax
Refund Rate % =
DIVIDE(
    CALCULATE(
        [Total Orders],
        Orders[Refunded amount] > 0
    ),
    [Total Orders]
)
```
What percentage of total orders had refunded amounts greater than zero?

A. 2.74%

B. 3.71%

C. 5.42%

D. 7.93%

**Submission Requirements**
- Select the right options to answer the questions.
- Upload your Power BI (.pbix) file to GitHub or Google Drive and share the link.
