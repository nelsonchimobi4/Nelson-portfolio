# Retail Electronics Sales Analysis Using SQL (MySQL / XAMPP)

## 📌 Project Overview
This project analyzes sales performance for an electronics retail store using SQL.  
The database (`lighthouse_db`) contains key tables such as `sales`, `products`, `customers`, `branches`, `categories`, and `sales_rep`.  
The objective is to answer critical business questions and generate insights regarding product performance, customer behavior, sales trends, and branch efficiency.

---

## 📊 Business Questions & SQL Queries

###  Q1: What are the Top 5 Best-Selling Products by Total Revenue?
SELECT 
    p.product_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM 
    sales s
JOIN 
    products p ON s.product_id = p.product_id
GROUP BY 
    p.product_name
ORDER BY 
    total_revenue DESC
LIMIT 5;

###  Q2: Which product categories generate the highest revenue? 
SELECT 
    c.category_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM 
    sales s
JOIN 
    products p ON s.product_id = p.product_id
JOIN 
    categories c ON p.category_id = c.category_id
GROUP BY 
    c.category_name
ORDER BY 
    total_revenue DESC;
    
### Q3: Which branch performs the best in terms of revenue? 
SELECT 
    b.branch_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM 
    sales s
JOIN 
    sales_rep sr ON s.srep_id = sr.srep_id
JOIN 
    branches b ON sr.branch_id = b.branch_id
GROUP BY 
    b.branch_name
ORDER BY 
    total_revenue DESC;

### Q4: Who are the top 5 highest-spending customers?
SELECT 
    c.customer_name,
    SUM(s.qty_sold * s.unit_price) AS total_spent
FROM 
    sales s
JOIN 
    customers c ON s.customer_id = c.customer_id
GROUP BY 
    c.customer_name
ORDER BY 
    total_spent DESC
LIMIT 5;

### Q5: Which sales representative generated the most revenue?
SELECT 
    sr.srep_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM 
    sales s
JOIN 
    sales_rep sr ON s.srep_id = sr.srep_id
GROUP BY 
    sr.srep_name
ORDER BY 
    total_revenue DESC
LIMIT 1;

### Q6: What is the revenue distribution by gender? 
SELECT 
    c.gender,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM 
    sales s
JOIN 
    customers c ON s.customer_id = c.customer_id
GROUP BY 
    c.gender
ORDER BY 
    total_revenue DESC;

---

## 🛠 Tools Used
| Tool | Purpose |
|------|---------|
| **MySQL (via XAMPP/phpMyAdmin)** | Query execution and analysis |
| **Notepad / VS Code** | Query documentation |
| **GitHub** | Portfolio hosting and project presentation |

---

## 📁 Files in this Folder
| File | Description |
|------|-------------|
|[View SQL Queries](./Lighthouse_db_queries.sql)|This project contains structured SQL queries for data extraction, cleaning, transformation, and financial performance analysis from the Lighthouse database.|

---

## 📥 Insight Summary 
Insights will be derived from executed queries and may include:
-Phone products generated the highest total revenue, indicating strong demand in that category.
-The Samsung S25 is the top-performing product, contributing the most revenue compared to all other items.
-The VI branch leads in revenue performance, showing stronger sales activity than the other branches.
- Praise Ayomide leads with ₦42.16M spent, showing strong customer value.
-Amaka Joseph tops sales with ₦41.83M revenue, marking her as a key performer.
-Male customers generated twice the revenue of females at ₦148.97M.

---

## 👤 Author
**Chimobi Nelson Ayogu** – Aspiring Data Analyst | Skills: SQL, Power BI, Excel, Tableau
