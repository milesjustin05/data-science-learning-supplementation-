Topic Having Clause
Tags: #sql #having

What it does
HAVING filters *grouped/aggregated* results, whereas WHERE filters raw rows.
WHERE runs before GROUP BY, so it can't reference aggregate functions like AVG() or SUM() — 
trying to do so throws an error. HAVING runs after aggregation, so it can.

Syntax
```sql
SELECT gender, AVG(age)
FROM employee_demographics
GROUP BY gender
HAVING AVG(age) > 40
;
```

When to use it in data science
- When using GROUP BY, to filter groups down to only those meeting a specific aggregate threshold
  (e.g. "departments with more than 5 employees", "regions with total sales over $10k")

Gotchas
- Trying to use WHERE with an aggregate function (e.g. `WHERE AVG(age) > 40`) → throws an error
- WHERE and HAVING *can* coexist in the same query — WHERE filters raw rows first, 
  HAVING filters the resulting groups. Order in the query: WHERE always before GROUP BY, 
  HAVING always after.
- Some databases (MySQL, Postgres, SQLite) let HAVING reference a SELECT alias; 
  others (SQL Server, Oracle) don't — safest to repeat the full aggregate expression.

Linked notes
[[00 Group By]]
[[7-7 Having Clause Practice]]