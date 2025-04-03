=======================================================
### 619. Biggest Single Number (https://leetcode.com/problems/biggest-single-number/description)
=======================================================

### Table Schema

#### Table: MyNumbers

| Column Name | Type |
|-------------|------|
| num         | int  |

### Question

Find the largest single number. If there is no single number, report null.

### Solution

```sql
        SELECT MAX(num) AS num
        FROM (
            SELECT num
            FROM MyNumbers
            GROUP BY num
            HAVING COUNT(num) = 1
        ) AS unique_numbers
```

### Concepts

The query uses concepts of `MAX` and `COUNT` Aggregate funcs to find largest single number