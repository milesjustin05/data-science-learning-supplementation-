# Practice Goal: Having Clause
Practice problems by Claude.

**Problem 1:** Given a table `orders(order_id, customer_id, amount)`, write a query to find all customers whose total order amount exceeds $1,000.

Attempt:
```sql
SELECT customer_id, SUM(amount)
FROM ORDERS
GROUP BY customer_id
HAVING SUM(amount) > 1000
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- Mistake here
---

**Problem 2:** Given a table `employees(emp_id, dept_id, salary)`, write a query to find departments with more than 5 employees.

Attempt:
```sql
SELECT dept_id, COUNT(emp_id)
FROM employees
GROUP BY dept_id
HAVING COUNT(emp_id) > 5
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- Mistake here
---

**Problem 3:** Given a table `products(product_id, category, price)`, write a query to find categories where the average product price is greater than $50.

Attempt:
```sql
SELECT category, AVG(price)
FROM products
GROUP BY category
HAVING AVG(price) > 50
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- Mistake here

```sql
table (col1, col2, col3)
```

**Problem 4:** Given a table `sales(sale_id, region, product, amount, sale_date)`, write a query that filters for sales made in 2025 (`WHERE`), groups by region, and returns only regions with total sales over $10,000 (`HAVING`).

Attempt:
```sql
SELECT region, SUM(amount)
FROM sales
WHERE YEAR(sale_date) = 2025
GROUP BY region
HAVING SUM(amount) > 10000
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- Mistake here

**Problem 5:** Given a table `students(student_id, class_id, score)`, write a query to find classes where the average score is above 75 AND the number of students is at least 10.

Attempt:
```sql
SELECT class_id, AVG(score)
FROM students
GROUP BY class_id
HAVING AVG(score) > 75
AND COUNT(student_id) >= 10
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- Mistake here

**Problem 6:** Given a table `transactions(transaction_id, customer_id, product_id)`, write a query to find customers who have purchased more than 3 distinct products.

Attempt:
```sql
SELECT customer_id, COUNT(DISTINCT product_id)
FROM transactions
GROUP BY customer_id
HAVING COUNT(DISTINCT product_id) > 3
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- Mistake here

**Problem 7:** Given a table `orders(order_id, customer_id, amount)`, write a query using `HAVING SUM(amount) > 500` and explain why you can't write `HAVING total > 500` unless you use a subquery or CTE (in most SQL dialects).

Attempt:
```sql
SELECT customer_id, SUM(amount)
FROM orders
GROUP BY customer_id
HAVING SUM(amount) > 500
;
```
The HAVING clause runs at the same time a aggregate function does so using HAVING without an aggregate function would throw an error.

Correct:
```sql
answer if needed
```

The real reason is about _order of operations_ in SQL: `HAVING` is logically evaluated _before_ the `SELECT` clause's column aliases are assigned. So when you write `SELECT SUM(amount) AS total ... HAVING total > 500`, the engine hasn't necessarily created `total` yet when it evaluates `HAVING`.

What went wrong:
- Correct query, but slightly off explanation

**Problem 8:** Explain why the following query is invalid, and rewrite it correctly:
```sql
SELECT dept_id, AVG(salary)
FROM employees
WHERE AVG(salary) > 60000
GROUP BY dept_id
;
```

Attempt:
It will throw an error because it is trying to use the aggregate function before it has been performed, HAVING clause should be used instead.
```sql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id
HAVING AVG(salary) > 60000
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- I forgot a comma whoops, added it back after but actual logic is correct.

**Problem 9:** Given a table `orders(order_id, customer_id, amount)`, write a query to find customers whose total order amount is greater than the overall average total order amount across all customers.

Attempt:
```sql
SELECT customer_id, SUM(amount)
FROM orders
GROUP BY customer_id
HAVING SUM(amount) > (SELECT AVG(amount) FROM orders)
;
```

Correct:
```sql
SELECT customer_id, SUM(amount) AS total
FROM orders
GROUP BY customer_id
HAVING SUM(amount) > (
    SELECT AVG(customer_total)
    FROM (
        SELECT SUM(amount) AS customer_total
        FROM orders
        GROUP BY customer_id
    ) AS sub
);
```

What went wrong:
- MIsunderstanding of the question, literally wanted the average of an average.

**Problem 10:** Given a table `books(book_id, author_id, rating)`, write a query to find authors with more than 2 books, having an average rating above 4.0, and sort the results by average rating in descending order.

Attempt:
```sql
SELECT author_id, COUNT(book_id), AVG(rating)
FROM books
GROUP BY author_id
HAVING AVG(rating) > 4
AND COUNT(book_id) > 2
ORDER BY AVG(rating) DESC
;
```

Correct:
```sql
answer if needed
```

What went wrong:
- Forgot another comma, whoops same as before just fixed with no update.