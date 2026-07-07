
| Question contains  | Aggregate to use |
| ------------------ | ---------------- |
| how many, count of | COUNT()          |
| total, sum of      | SUM()            |
| average, mean      | AVG()            |
| highest, maximum   | MAX()            |
| lowest, minimum    | MIN()            |

| Clause     | Purpose                                      | Operates On           | Runs (Logical Order) | Can Use Aggregate Functions? |
|------------|-----------------------------------------------|------------------------|------------------------|-------------------------------|
| `WHERE`    | Filters individual rows *before* grouping      | Raw table rows          | 2nd (after `FROM`)     | ❌ No                          |
| `GROUP BY` | Groups rows into buckets based on column(s)    | Rows → Groups           | 3rd                    | N/A (defines the groups)      |
| `HAVING`   | Filters *groups* after aggregation             | Aggregated groups       | 4th                    | ✅ Yes                         |
| `ORDER BY` | Sorts the final result set                     | Final output rows       | 6th (after `SELECT`)   | ✅ Yes (can sort by aggregate) |

