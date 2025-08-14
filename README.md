# Ecommerce-Customer-Spending-Analysis

[![Excel](https://img.shields.io/badge/Excel-2019-darkgreen)](https://www.microsoft.com/en-in/microsoft-365/previous-versions/microsoft-office-2019)
[![Python Version](https://img.shields.io/badge/Python-3.9-blue)](https://www.python.org/)
[![MySQL](https://img.shields.io/badge/Database-MySQL-informational)](https://www.mysql.com/)
[![Power BI](https://img.shields.io/badge/Visualization-Power_BI-yellow)](https://www.microsoft.com/en-us/power-platform/products/power-bi)
[![License](https://img.shields.io/badge/License-MIT-blue)](https://github.com/PalakJain-Analytics/Ecommerce-Customer-Spending-Analysis/tree/main?tab=MIT-1-ov-file)

An end-to-end E-commerce Customer Spending Analysis project leveraging **Excel**, **Python**, **MySQL**, and **Power BI** to transform raw data into business insights.
The process covers data cleaning, preprocessing, exploratory analysis, SQL-based querying, and interactive Power BI dashboards to identify spending trends and customer behavior for informed decision-making.

The project demonstrates expertise in data wrangling, SQL analysis, and business intelligence reporting. It serves as a strong portfolio example for aspiring and professional data analysts.

---

## 📘 Project Framework

- [🎯 Project Objective](#-project-objective)
- [📌 Business Objective](#-business-objective)
- [📊 Tools & Stacks](#-tools--stacks)
- [🔁 End-to-End Workflow](#-end-to-end-workflow)
- [🧹 Excel + Python Processing](#-excel--python-processing)
- [🗃 SQL-Based Exploration](#-sql-based-exploration)  
- [📈Power BI Interactive Dashboard](#-power-bi-interactive-dashboard)  
- [⚙ How to Use This Project](#-how-to-use-this-project)
- [📂 Repository Structure](#-repository-structure)
- [📝 License](#-license)
- [📬 About Me](#-about-me)

---

## 🎯 Project Objective

This project analyzes customer spending behavior on an e-commerce platform.   to identify top customers, best product categories, and payment preferences.
It covers **Excel preprocessing, Python data analysis, MySQL queries, and Power BI dashboards** to create actionable business insights.


---

## 📌 Business Objective

- Understand **spending patterns** across customer segments.  
- Understanding **product category performance**.
- Detecting **payment method preferences** by groups.
- Creating **interactive visual tools** for quick decision-making.

---

## 📊 Tools & Stacks

| Tool        | Purpose                                                                  |
|-------------|-----------------------------------------------------------------         |
| **Excel**   | Initial cleaning, date splitting (Year, Month), and Age Group creation.  |
| **Python**  | EDA and visualization                                                    |
| **MySQL**   | Data storage and advanced queries                                        |
| **Power BI**| Interactive dashboard design and data storytelling                       |

---

## 🔁 End-to-End Workflow

```mermaid
graph LR
    A[Raw Excel] --> B[Excel Formulas]
    B --> C[Python Script]
    C --> D[MySQL Database]
    D --> E[Power BI Dashboard]
```

Each stage seamlessly builds upon the previous one, resulting in a streamlined, production-ready pipeline that transforms raw, unstructured data into meaningful, actionable insights.

---

## 🧹 Excel + Python Processing
**Excel Processing:**

### ✅ Step 1: Raw Data (Raw_data.xlsx)
- Contains columns like `Transaction_Id`, `User_Name`, `Age`, `Country`, `Product_Category`, etc.
- This is the simulated export from Ecommerce.

![Raw Excel Data](Images/Ecommerce%20raw%20data.jpg)

### ✅ Step 2: Split Transaction_Date & created Age group column 
- Split `Transaction_Date` into **Year** and **Month** columns.
- Converted numeric month to month names.
- Created **Age Group** categories (Youth, Adult, Senior) based on `Age`.

  
These were calculated using **Excel formulas**:


| Formula | Purpose |
|--------|---------|
| `Year(Transaction_Date)` | Split Transaction_date into year |
| `Month(Transaction_Date)` | Split Transaction_date into month (in date) |
| `Text(date,''mmmm'')` | Split Transaction_date into month (in text) |
| `=IF(B2<25, "Youth", IF(B2<45, "Adult", "Senior"))` | Assign Age group |


![Cleaned Excel Data](Images/Cleaned_ecommerce.jpg)

---

## 🧹 EDA in Python 

**Python Processing:**
- Checked for missing values and outliers.
- Verified data types and formatting.
- Generated exploratory visualizations for quick insights.

[Click here to view the PDF](https://github.com/PalakJain-Analytics/Ecommerce-Customer-Spending-Analysis/blob/main/python%201.pdf)

---

## 🗃 SQL Based Exploration
Key queries performed in MySQL:

select * from cleaned_ecommerce;

1. **Top Spending Age Group by Country**
```sql
SELECT Age_group, Country, SUM(Purchase_Amount) AS Total_Spend
FROM cleaned_ecommerce
GROUP BY Age_group, Country
ORDER BY Total_Spend DESC;
```
2. **Preferred Payment Method by Age Group**
```sql
SELECT Age_group, Payment_Method, COUNT(*) AS Preference
FROM cleaned_ecommerce
GROUP BY Age_group, Payment_Method;
```
3. **Top Product Categories by Country**
```sql
SELECT Country, Product_Category, SUM(Purchase_Amount) AS Total_Spent
FROM cleaned_ecommerce
GROUP BY Country, Product_Category
ORDER BY Total_Spent DESC
LIMIT 3;
```

4. **Seasonal Trends**
```sql
SELECT Year, Month_in_text, SUM(Purchase_Amount) AS Total_purchase
FROM cleaned_ecommerce
GROUP BY Year, Month_in_text
ORDER BY Total_purchase DESC;
```

5. **Top 5 Customers by Lifetime Purchase**
```sql
SELECT User_Name, SUM(Purchase_Amount) AS Total_Spent
FROM cleaned_ecommerce
GROUP BY User_Name
ORDER BY Total_Spent DESC
LIMIT 5;
```

6. **Category-wise Monthly Trend**
```sql
SELECT Month_in_text, Product_Category, SUM(Purchase_Amount) as Total_Spent
FROM cleaned_ecommerce
GROUP BY Month_in_text, Product_Category
ORDER BY Month_in_text desc;
```

7. **Age Group that Spends the Most (in average)**
```sql
SELECT Age_group, AVG(Purchase_Amount) as Avg_Spend
FROM cleaned_ecommerce
GROUP BY Age_group
ORDER BY Avg_Spend DESC;
```
### 📘 Schema Screenshot

![Schema Screenshot](Images/MySQL%20(1).jpg)
![Schema Screenshot](Images/MySQL%20(2).jpg)
![Schema Screenshot](Images/MySQL%20(3).jpg)

---

## 📈 Power BI Interactive Dashboard

Connected Cleaned_ecommerce csv file to Power Bi and created an interactive dashboard.

The interactive dashboard includes:

1. **Cards**: Total Spending, Total Customers, Top Country, Top Category.
2. **Filters**: Year, Month, Customer Age Group.
3. **Visuals**:
   - **Top 3 Countries by Spending** (Treemap)
   - **Payment Method Distribution** (Donut Chart)
   - **Age Group vs Spending** (Bar Chart)
   - **Spending Trend Over Months** (Line Chart)
   - **Total Spend by Product Category & Year** (Clustered Column Chart)

![Power BI Dashboard](Images/Ecommerce%20Customer%20Spending%20Data%20Analysis%20.jpg)

These enable filtering, aggregation, and time-based visualizations.

---

## ⚙ How to Use This Project

### 🔹 1. Clone the Repo
```bash
git clone https://github.com/PalakAnalyst/Ecommerce-Customer-Spending-Analysis.git
```

### 🔹 2. Open Excel Files
- View and understand `Ecommerce_raw data.xlsx`, CSVs
- Optionally edit and export again using Excel formulas

### 🔹 3. Open Jupyter Notebook
- Execute the Python notebook for EDA

### 🔹 4. Set Up MySQL
- Import all `.csv` using MySQL Workbench
- Run the MySQL scripts against your database

### 🔹 5. Open Power BI Dashboard
- Use `Ecommerce.pbix` to view interactive report
- Or connect manually via: `Home → Get Data → Excel Workbook`

---

## 📂 Repository Structure

```
📦 Ecommerce-Customer-Spending-Analysis
 ┣ 📄 Ecommerce_raw data.csv
 ┣ 📄 Cleaned_ecommerce.csv
 ┣ 📄 Age group.csv
 ┣ 📄 Years and months.csv
 ┣ 📄 Ecommerce.ipynb
 ┣ 📄 python 1.pdf
 ┣ 📄 Ecommerce.sql
 ┣ 📄 MYSQL(1).pdf
 ┣ 📄 Ecommerce.pbix
 ┣ 📁 images
 ┃ ┣ 📷 Ecommerce raw dat.jpg
 ┃ ┣ 📷 Cleaned ecommerce.jpg
 ┃ ┣ 📷 Age group.jpg
 ┃ ┣ 📷 Years and months.jpg
 ┃ ┣ 📷 Python 1.jpg
 ┃ ┣ 📷 Python 2.jpg
 ┃ ┣ 📷 Python 3.jpg
 ┃ ┣ 📷 Python 4.jpg
 ┃ ┣ 📷 Python 5.jpg
 ┃ ┣ 📷 Python 6.jpg
 ┃ ┣ 📷 Python 7.jpg
 ┃ ┣ 📷 Python 8.jpg
 ┃ ┣ 📷 Python 9.jpg
 ┃ ┣ 📷 Python 10.jpg
 ┃ ┣ 📷 MySQL (1).jpg
 ┃ ┣ 📷 MySQL (2).jpg
 ┃ ┣ 📷 MySQL (3).jpg
 ┃ ┣ 📷 Ecommerce Customer Spending Data Analysis.jpg
 ┣ 📄 LICENSE
 ┗ 📄 README.md
```
---

## 📝 License

This project is licensed under the **MIT License** — you are free to use, modify, and share with attribution.

---

## 📬 About Me

I'm **Palak Jain**, an enthusiastic and detail-oriented data analyst with strong academic knowledge and hands-on internship experience.
experience in data analysis, visualisation, and reporting. Proficient in SQL, Excel, Python, Tableau, and
Power BI. 

- [LinkedIn](https://www.linkedin.com/in/palakjainanalyst/)
- [GitHub](https://github.com/PalakJainAnalyst)

If you found this project helpful, consider giving it a ⭐ to show your support!

