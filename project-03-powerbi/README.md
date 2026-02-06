# Junior Business Intelligence Analyst
## Take-Home Assignment: Credit Risk Analytics in Power BI

---

## Purpose of This Assignment

This exercise simulates the type of work you would do as a **Junior Business Intelligence Analyst** in this role.

There is **no single correct answer**.

We are evaluating:

- How you approach data and build **Power BI** reports
- How you identify patterns and insights from customer data
- How you communicate findings through visualizations
- How you handle real-world data quality issues

> **Note:**  
> This is **not** a test of advanced Power BI features or DAX expertise.  
> This **is** a test of your analytical thinking and ability to **tell a story with data**.

---

## Business Context

You have joined a **consumer finance company** that provides personal loans and credit products to individual customers.

The company is focused on improving its **credit risk assessment** and **customer understanding** in order to make better lending decisions.

### The Risk Management team has observed:

- Inconsistent customer credit performance
- Uncertainty around which factors drive **delinquency**
- Need for better visibility into **customer segments**
- Questions about how to prioritize **portfolio management efforts**

---

## Data Overview

You have been given access to a dataset containing **45,000+ customers**, including:

- **Demographic information** (age, dependents)
- **Financial profile** (monthly income, debt ratio)
- **Credit behavior** (late payments and delinquencies)
- **Credit worthiness assessment** (serious delinquency indicator)

Your task is to build a **Power BI report** that helps the Risk Management team understand their customer portfolio and identify patterns related to **credit risk**.

---

## Your Task

Using **Power BI Desktop**, create a report that addresses the following:

### 1. Understand the Portfolio

- What does the customer base look like?
- What are the key characteristics of customers?
- How is credit risk distributed across the portfolio?

---

### 2. Identify Risk Patterns

- What factors are associated with **serious delinquency**?
- Are there clear customer segments based on risk?
- Which customer characteristics predict credit problems?

---

### 3. Provide Actionable Insights

- What are the **top 3–5 insights** the Risk team should know?
- Where should the team focus its attention?
- What recommendations would you make based on the data?

---

## Deliverables

Please submit the following:

---

### 1. Power BI Report File (`.pbix`)

Create a **multi-page Power BI report**.

#### Report Requirements:

- Professional, clean design
- Consistent color scheme and formatting
- Clear titles and labels on all visuals
- Interactive filters and slicers where appropriate
- No more than **4 pages** (quality over quantity)

---

### 2. Insight Summary (Maximum 2 Pages)

A brief document in **PDF format** that includes:

- **Executive Summary:** Top 3–5 key insights
- **Findings:** What you discovered in the data
- **Recommendations:** Specific actions for the Risk team
- **Data Quality Notes:** Issues encountered and how they were handled
- **Next Steps:** Additional data or analysis that would be helpful

**Audience:** Non-technical business stakeholders  
**Tone:** Professional and concise — avoid technical jargon

---

### 3. README File (Plain Text or Word)

Include the following:

- Brief description of your approach
- Any assumptions you made
- How to navigate the Power BI report
- Data transformations or calculations performed
- Time spent on the assignment

---

## Data Access

You will can access excel file in the repo:

Finance-Credit_Worthiness.xlsx
---

## Dataset Structure

| Field                     | Description                                                       | Type    |
|---------------------------|-------------------------------------------------------------------|---------|
| Person ID                 | Unique customer identifier                                        | Integer |
| Person Name               | Customer name                                                     | Text    |
| Age                       | Customer age in years                                             | Integer |
| Serious 2 Year Delinquency| Serious delinquency in last 2 years (0 = No, 1 = Yes)             | Binary  |
| 30-59 Days Past Due       | Number of times 30–59 days past due in last 2 years               | Integer |
| Debt Ratio                | Monthly debt payments / monthly gross income                     | Decimal |
| 90 Days Late              | Number of times 90+ days late in last 2 years                     | Integer |
| 60-89 Days Past Due       | Number of times 60–89 days past due in last 2 years               | Integer |
| Monthly Income            | Customer monthly income (USD)                                     | Decimal |
| Number Of Dependents      | Number of financial dependents                                    | Integer |

---


