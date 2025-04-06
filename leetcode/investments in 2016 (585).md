=======================================================
### 585. Investments in 2016 (https://leetcode.com/problems/investments-in-2016/description)
=======================================================

### Table Schema

#### Table: Insurance

|-------------|-------|
| Column Name | Type  |
|-------------|-------|
| pid         | int   |
| tiv_2015    | float |
| tiv_2016    | float |
| lat         | float |
| lon         | float |

### Question

Write a solution to report the sum of all total investment values in 2016 tiv_2016, for all policyholders who:

have the same tiv_2015 value as one or more other policyholders, and
are not located in the same city as any other policyholder (i.e., the (lat, lon) attribute pairs must be unique).

### Solution

```sql
        SELECT ROUND(SUM(tiv_2016)::DECIMAL,2) AS tiv_2016 FROM
        (
            SELECT *,
                COUNT(*) OVER (PARTITION BY tiv_2015) as tiv_count,
                COUNT(*) OVER (PARTITION BY lat, lon) as loc_count
            FROM Insurance
        ) sub
        WHERE sub.tiv_count >1 AND loc_count = 1
```

### Concepts

The query uses concepts of `SUBQUERIES, WINDOW FUNCS` and `COUNT` Aggregate funcs to find sum of all total investment values