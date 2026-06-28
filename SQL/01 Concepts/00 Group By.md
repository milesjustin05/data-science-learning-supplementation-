# Group By
Tags: #sql #fundamentals #aggregation

## What it does
Collapses rows that share the same value in a column into a  single row, so you can run aggregate calculations on each group.

## Quick Reference
See also: [[01 SQL Cheatsheet]]

| Question contains | Aggregate to use |
|---|---|
| how many, count of | COUNT() |
| total, sum of | SUM() |
| average, mean | AVG() |
| highest, maximum | MAX() |
| lowest, minimum | MIN() |

## Syntax
```sql
SELECT column, AGG_FUNCTION(column)
FROM table
GROUP BY column;
```

## Common aggregate functions
| Function | What it returns |
|----------|----------------|
| COUNT()  | number of rows |
| SUM()    | total of a column |
| AVG()    | mean of a column |
| MAX()    | highest value |
| MIN()    | lowest value |

## Data science use cases
- Summarizing sales by region, category, or time period
- Counting events per user (sessions, clicks, purchases)
- Finding distributions (how many users per cohort)
- Feeding aggregated results into a chart or model

## Gotchas
- Every column in SELECT must either be in GROUP BY 
  or wrapped in an aggregate function — or you get an error
- NULL values get grouped together as their own group
- HAVING vs WHERE is the most common beginner mistake
- ORDER of clauses: WHERE → GROUP BY → HAVING → ORDER BY

## Linked notes
[[SELECT & WHERE]] [[HAVING]] [[Window Functions]] [[CTEs]]