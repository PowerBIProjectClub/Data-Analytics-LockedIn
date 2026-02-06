# Junior Business Intelligence Analyst
## Take-Home Assignment: Product Demand Analytics

---

## Purpose of This Assignment

This exercise simulates the type of work you would do as a **Junior Business Intelligence Analyst** in this role.

There is **no single correct answer**.

We are evaluating:

- How you think through business problems
- How you work with ambiguity and imperfect data
- How you reason with data to find meaningful patterns
- How clearly you communicate insights that inform real decisions

> **Note:**  
> This is **not** a test of advanced Excel formulas or visualization skills.  
> This **is** a test of judgment, analytical thinking, and business intelligence.

---

## Business Context

You have joined a **B2B software company** that sells productivity tools and business intelligence solutions to enterprise clients across the United States.

The company operates a **multi-warehouse distribution model** for physical product deliveries (hardware devices, installation kits, and training materials).

### Leadership has observed:

- Significant **month-over-month revenue volatility**
- **Inconsistent demand patterns** across warehouses and regions
- Concerns about **inventory planning** and **warehouse utilization**
- Questions around **product performance** and overall **portfolio health**
- Uncertainty about **geographic expansion priorities**

---

## Data Overview

You have been given access to **two years of order data (2018–2019)** covering:

- Product categories and individual SKUs
- Warehouse fulfillment locations
- Customer delivery ZIP codes
- Order timestamps (date and time)
- Order demand (units ordered)
- Transaction values (revenue per order)

Your task is to help leadership understand:

> **What is happening, why it is happening, and what should be done next.**

---

## Your Task

Using the provided data, please address the following:

### 1. Understand What Is Happening

- What trends or patterns stand out across **time**, **geography**, or **product categories**?
- Which products, warehouses, or regions are **performing well**? Which are **underperforming**?
- Are there **seasonal patterns** or time-based trends?
- What surprised you in the data?

---

### 2. Diagnose Why It’s Happening

- What factors appear to be driving **demand volatility**?
- Are there meaningful differences by:
  - Product category or individual product
  - Warehouse location
  - Geographic region (ZIP code)
  - Time period (seasonality, day of week, time of day)
- What relationships exist between **order size**, **transaction value**, and other variables?
- Where does the data limit your conclusions?
- What questions **cannot** be answered with the current dataset?

---

### 3. Provide Business Intelligence

- What are the **top 3–5 insights** leadership should care about right now?
- What **risks or opportunities** require immediate attention?
- What **actions** would you recommend leadership consider next?
- If you could request additional data, what would it be and **why**?

> You are encouraged to **challenge assumptions** if the data does not support them.

---

## Deliverables

Please submit the following:

### 1. Executive Dashboard (Excel)

Create an executive dashboard that provides leadership with an at-a-glance view of the business.

The dashboard should answer:

- What’s the current state of the business?
- Where are the biggest opportunities or risks?
- What trends should leadership be aware of?

---

### 2. Analysis Workbook (Excel)

Your working Excel file should include:

- **Dashboard sheet** (your primary deliverable — should be the first sheet)
- **Data preparation / cleaning sheets** (clearly documented)
- **Analysis sheets** with formulas, pivot tables, or calculations supporting the dashboard
- Clear labels and comments explaining logic and assumptions

**Suggested Organization:**

- Sheet 1: `Executive_Dashboard`
- Sheet 2: `Data_Cleaning`
- Sheets 3+: Supporting analysis  
  - `Time_Analysis`
  - `Product_Analysis`
  - `Geography_Analysis`

> Keep raw data in a separate sheet if modified.

---

### 3. Insight Summary (Maximum 2 Pages)

A concise document written for a **non-technical executive audience** that includes:

- **Executive Summary:** Top 3–5 insights (bullet points)
- **Key Findings:** Supporting analysis and context (1–1.5 pages)
- **Recommendations:** Specific actions leadership should consider
- **Dashboard Guide:** Brief explanation of how to use the dashboard
- **Limitations:** What the data cannot tell us

**Format:** PDF  
**Tone:** Professional but accessible — avoid Excel jargon or technical formulas

> The summary should **complement** the dashboard, not repeat it.

---

## Data Access

You will access the Excel file in the repo:


---

## Dataset Structure

| Field        | Description                                   | Type    |
|--------------|-----------------------------------------------|---------|
| Category     | Product category (Worksuite 1000, BI Stack, TBOX) | Text    |
| Product      | Specific product name / SKU                   | Text    |
| Warehouse    | Fulfillment warehouse location                | Text    |
| Zip          | Customer delivery ZIP code                    | Integer |
| Date         | Order date                                    | Date    |
| Time         | Order time (HH:MM:SS format)                  | Time    |
| Order Demand | Quantity ordered (units)                      | Integer |
| Value        | Transaction value per order (USD)             | Decimal |

---
