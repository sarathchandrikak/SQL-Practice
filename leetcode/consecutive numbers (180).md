=======================================================
### 180. Consecutive Numbers (https://leetcode.com/problems/consecutive-numbers/description)
=======================================================

### Table Schema

#### Table: Logs

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| num         | varchar |


### Question

Find all numbers that appear at least three times consecutively.

### Solution

```sql
    SELECT DISTINCT l1.Num AS ConsecutiveNums
    FROM Logs l1
    JOIN Logs l2 ON l1.Id = l2.Id - 1
    JOIN Logs l3 ON l1.Id = l3.Id - 2
    WHERE l1.Num = l2.Num 
    AND l2.Num = l3.Num;
```

### Concepts

The query uses concepts of Mutiple `JOINS` on next tables previous record to find 3 consecutive numbers