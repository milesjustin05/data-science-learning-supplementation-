### Group By

#### COUNT vs SUM confusion
Kept reaching for SUM when the question said "how many"
**Rule:** "how many" → COUNT, "total" → SUM

#### Forgetting the aggregate
Was putting raw columns in SELECT without wrapping in COUNT/SUM/AVG
**Rule:** every column in SELECT must be in GROUP BY or an aggregate

#### GROUP BY EXTRACT
Wrote GROUP BY MONTH instead of repeating the full expression
**Rule:** `GROUP BY EXTRACT(MONTH FROM col)` not `GROUP BY MONTH`

