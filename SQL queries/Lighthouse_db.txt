-- Retail Electronics Sales Analysis using MySQL (XAMPP / phpMyAdmin)
-- Database: lighthouse_db

/*=====================================================
 Q1: Top 5 Products by Total Revenue
=====================================================*/
SELECT 
    p.product_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_revenue DESC
LIMIT 5;

/*=====================================================
 Q2: Total Revenue by Product Category
=====================================================*/
SELECT 
    c.category_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
JOIN categories c ON p.category_id = c.category_id
GROUP BY c.category_name
ORDER BY total_revenue DESC;

/*=====================================================
 Q3: Best-Performing Branch by Revenue
=====================================================*/
SELECT 
    b.branch_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM sales s
JOIN sales_rep sr ON s.srep_id = sr.srep_id
JOIN branches b ON sr.branch_id = b.branch_id
GROUP BY b.branch_name
ORDER BY total_revenue DESC;

/*=====================================================
 Q4: Top 5 Customers by Total Spending
=====================================================*/
SELECT 
    c.fullname AS customer_name,
    SUM(s.qty_sold * s.unit_price) AS total_spent
FROM sales s
JOIN customers c ON s.customer_id = c.customer_id
GROUP BY c.fullname
ORDER BY total_spent DESC
LIMIT 5;

/*=====================================================
 Q5: Top Sales Representatives by Total Revenue Generated
=====================================================*/
SELECT 
    CONCAT(sr.first_name, ' ', sr.last_name) AS sales_rep_name,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM sales s
JOIN sales_rep sr ON s.srep_id = sr.srep_id
GROUP BY sales_rep_name
ORDER BY total_revenue DESC;

/*=====================================================
 Q6: Monthly Revenue Trend (Most Recent Year)
=====================================================*/
SELECT 
    DATE_FORMAT(s.sales_date, '%Y-%m') AS month,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM sales
GROUP BY month
ORDER BY month;

/*=====================================================
 Q7: Revenue by Customer Gender
=====================================================*/
SELECT 
    c.gender,
    SUM(s.qty_sold * s.unit_price) AS total_revenue
FROM sales s
JOIN customers c ON s.customer_id = c.customer_id
GROUP BY c.gender
ORDER BY total_revenue DESC;
