Practice Goal: [[00 Group By]]

Practice problems by Claude.

Data Table
``` sql
orders    (order_id, customer_id, amount, status, created_at)
products  (product_id, name, category, price)
order_items (order_id, product_id, quantity)
```
---

Problem 1: **How many orders has each customer placed?**

***Attempt:***
```sql
select order_id, customer_id
from orders
group by customer_id;
```

***Correct:***
```sql
select customer_id, COUNT(order_id)
from orders
group by customer_id
```

***What went wrong:***
- Forgot the aggregate 

---
Problem 2: **What is the amount spent per customer**

***Attempt:***
```sql
select amount, customer_id
from orders
group by amount;
```

***Correct:***
```sql
SELECT customer_id, SUM(amount)
FROM orders
GROUP BY customer_id;
```

***What went wrong:***
- Forgot the aggregate 
---
Problem 3: **How many orders are there for each status (pending, shipped, delivered)**

***Attempt:***
```sql
select SUM(order_id), status
from orders
group by status;
```

***Correct:***
```sql
SELECT status, COUNT(order_id)
FROM orders
GROUP BY status;
```

***What went wrong:***
- Used the sum aggregate and got the total added not the COUNT
---

Problem 4: **What is the average order amount per customer**

***Attempt/Correct:***
```sql
select AVG(amount), customer_id
from orders
group by customer_id;
```

---
Problem 5: **How many orders were placed each month**

***Attempt:***
```sql
select SUM(order_id), EXTRACT(MONTH FROM created_at)
from orders
group by MONTH
```

***Correct:***
```sql
SELECT EXTRACT(MONTH FROM created_at), COUNT(order_id)
FROM orders
GROUP BY EXTRACT(MONTH FROM created_at);
```

***What went wrong:***
- Used the sum aggregate and got the total added not the COUNT
- Did not keep the extract statement when going to the group by statement
---

**Problem 6: How many products are in each category?**

***Attempt/Correct:***
```sql
SELECT category, COUNT(product_id)
FROM products
GROUP BY category
```
---

**Problem 7: What is the total quantity sold per product?**

***Attempt/Correct:***
```sql
SELECT product_id, SUM(quantity)
FROM order_items
GROUP BY product_id
```
---

**Problem 8: What is the average price of products in each category?**

***Attempt/Correct:***
```sql
SELECT category, AVG(price)
FROM products
GROUP BY category
```
---

**Problem 9: How many orders were placed each year?**

***Attempt:***
```sql
SELECT EXTRACT(YEAR FROM created_at), SUM(amount)
FROM orders
GROUP BY EXTRACT(YEAR FROM created_at)
```

Correct:
```sql
SELECT EXTRACT(YEAR FROM created_at), COUNT(order_id)
FROM orders
GROUP BY EXTRACT(YEAR FROM created_at);
```

***What went wrong:***
- Used the sum aggregate and got the total added not the COUNT
---

**Problem 10: What is the total amount of orders for each status?**

***Attempt:***
```sql
SELECT status, COUNT(order_id)
FROM orders
GROUP BY status
```

Correct:
```sql
SELECT status, SUM(amount)
FROM orders
GROUP BY status;
```

***What went wrong:***
- Used the sum aggregate and got the total added not the COUNT