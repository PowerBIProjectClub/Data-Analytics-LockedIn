# Homework 4 - Power BI

**Dataset Context:**  
Food delivery order data containing timestamps, drivers, restaurants, customers, fees, and delivery locations.

---

## Instructions
- Choose the **exact answer** or the **closest correct option**.

---

## QUESTIONS

### QUESTION 1
**Which Power BI component is primarily used to transform and clean this delivery dataset before analysis?**

A. Power BI Service  
B. Power Query Editor  
C. DAX Studio  
D. Power BI Report View  

---

### QUESTION 2
**Which Power BI view is best suited for creating charts showing delivery time trends by date?**

A. Model View  
B. Data View  
C. Report View  
D. Power Query View  

---

### QUESTION 3
**Some rows have missing values for “Time driver arrived at restaurant”. What is the BEST initial approach?**

A. Delete all rows with missing values  
B. Replace missing values with 0  
C. Investigate and flag them as incomplete deliveries  
D. Convert the column to text  

---

### QUESTION 4
**Which transformation is most appropriate to calculate delivery duration later in DAX?**

A. Merge all time columns into one  
B. Ensure all time columns are converted to Date/Time data type  
C. Convert time columns to text  
D. Remove the time columns  

---

### QUESTION 5
**The ASAP column contains values “Yes” and “No”. What is the best practice for modelling this field?**

A. Leave it as text  
B. Convert it to a Boolean (True/False)  
C. Delete the column  
D. Split it into two columns  

---

### QUESTION 6
**Which table should be considered the Fact table in this dataset?**

A. Driver table  
B. Restaurant table  
C. Orders / Deliveries table  
D. Date table  

---

### QUESTION 7
**Which columns are best suited for dimension tables?**

A. Sub Total, Tip, Delivery Fee  
B. Driver ID, Driver Name  
C. Discount, Refunded Amount  
D. Delivery Time, ASAP  

---

### QUESTION 8
**Why is it recommended to create a separate Date table for this dataset?**

A. To reduce file size  
B. To enable time intelligence calculations  
C. To improve data refresh speed  
D. To hide date columns  

---

### QUESTION 9
**What relationship type is MOST appropriate between the Orders table and the Driver table?**

A. One-to-One  
B. Many-to-Many  
C. One-to-Many  
D. Bi-directional  

---

### QUESTION 10
**Which DAX function is best for calculating total delivery time in minutes?**

A. SUM  
B. DATEDIFF  
C. COUNT  
D. IF  

---

### QUESTION 11
**To calculate total revenue, which columns should be combined?**

A. Sub Total + Delivery Fee + Service Fee + Tip  
B. Sub Total – Discount – Refunded Amount  
C. Delivery Fee + Tip  
D. Discount + Refunded Amount  

---

### QUESTION 12
**Which visual is BEST for comparing average delivery time across delivery areas?**

A. Table  
B. Line Chart  
C. Bar Chart  
D. KPI Card  

---

### QUESTION 13
**Which visual is most suitable for showing delivery volume trends over time?**

A. Pie Chart  
B. Line Chart  
C. Matrix  
D. Gauge  

---

### QUESTION 14
**What is the best way to highlight late deliveries in a table visual?**

A. Change the background color manually  
B. Sort by driver name  
C. Apply conditional formatting  
D. Use a slicer only  

---

### QUESTION 15
**Which slicer would be MOST useful for operational analysis?**

A. Customer ID  
B. ASAP  
C. Delivery Area  

---

### QUESTION 16 — Trimming Text Columns
Some restaurant names contain leading spaces (e.g., `" Maple Street Kitchen"`).

**Which Power Query transformation should be applied?**

A. Replace Values  
B. Trim  
C. Uppercase  
D. Split Column  

---

### QUESTION 17 — Data Profiling
You want to quickly view minimum, maximum, and average delivery fees.

**Which Power Query feature supports this?**

A. Column Distribution  
B. Column Quality  
C. Column Profile  
D. Conditional Column  

---

### QUESTION 18 — Filter Direction
**Best practice filter direction in a star schema is:**

A. Both  
B. Single (Dimension → Fact)  
C. Fact → Dimension  
D. None  

---



