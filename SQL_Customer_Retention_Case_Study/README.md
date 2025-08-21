
# 📊 SQL Business/Data Analyst Case Study: Customer Retention & Sales Trends

## 🏢 Business Scenario
You’ve been hired by a retail company, **TrendCloth**, that sells apparel online across the U.S. They want to improve customer retention and identify purchasing trends over time. As a Business/Data Analyst, your task is to extract insights from their SQL database to help the marketing and product teams make data-driven decisions.

---

## 📁 Data Tables

### `customers`
| customer_id | first_name | last_name | signup_date | city    | state |
|-------------|------------|-----------|-------------|---------|-------|
| 1001        | Jamie      | Christian | 2023-01-15  | Raleigh | NC    |

### `orders`
| order_id | customer_id | order_date | total_amount | status    |
|----------|-------------|------------|--------------|-----------|
| 5001     | 1001        | 2024-03-20 | 75.50        | Completed |

### `order_items`
| item_id | order_id | product_name     | quantity | unit_price |
|---------|----------|------------------|----------|------------|
| 8001    | 5001     | Graphic T-Shirt  | 2        | 15.00      |

---

## 📌 Objectives

1. **Retention Analysis**
   - How many customers made repeat purchases (more than 1 order)?
   - What’s the average time between a customer’s first and second order?

2. **Sales Insights**
   - What are the top 5 products by sales revenue?
   - What’s the average order value over the past 12 months?

3. **Churn Risk Indicators**
   - Which customers signed up over 6 months ago and have only made one order?
   - Which states have the highest percentage of one-time customers?

---

## 🧠 Sample SQL Queries

### 1. Repeat Customers
```sql
SELECT customer_id, COUNT(*) AS total_orders
FROM orders
GROUP BY customer_id
HAVING COUNT(*) > 1;
```

### 2. Average Order Value
```sql
SELECT AVG(total_amount) AS avg_order_value
FROM orders
WHERE order_date >= DATE_SUB(CURDATE(), INTERVAL 12 MONTH);
```

### 3. Top Products by Revenue
```sql
SELECT product_name, SUM(quantity * unit_price) AS total_revenue
FROM order_items
GROUP BY product_name
ORDER BY total_revenue DESC
LIMIT 5;
```

---

## 📈 Deliverable Summary

After analyzing 12 months of order data, we identified that:
- **28% of customers** made repeat purchases
- **Graphic T-Shirts** were the top-selling product by revenue
- **Average order value** was $58.10
- **37% of one-time customers** were concentrated in Texas and Georgia

### 💡 Recommendations
- Launch targeted retention campaigns for first-time buyers in high-churn states
- Promote bundles including high-performing products to increase repeat purchases
