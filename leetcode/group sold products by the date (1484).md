=======================================================
### 1484. Group Sold Products By The Date (https://leetcode.com/problems/second-highest-salary/)
=======================================================

### Table Schema

#### Table: Employee

| Column Name | Type    |
|-------------|---------|
| sell_date   | date    |
| product     | varchar |

### Question

Write a solution to find for each date the number of different products sold and their names.

### Solution

```sql
    select sell_date, count(distinct product) as num_sold, GROUP_CONCAT(distinct product ORDER BY product) as products from Activities group by sell_date
```

### Concepts

The query uses `AGG COUNT`, `GROUP_CONCAT` functions to find number of different products sold