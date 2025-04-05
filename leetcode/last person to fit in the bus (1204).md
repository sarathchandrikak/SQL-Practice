=======================================================
### 1204. Last Person to Fit in the Bus (https://leetcode.com/problems/last-person-to-fit-in-the-bus/description/)
=======================================================

### Table Schema

#### Table: Queue

| Column Name | Type    |
|-------------|---------|
| person_id   | int     |
| person_name | varchar |
| weight      | int     |
| turn        | int     |

### Question

Write a solution to find the person_name of the last person that can fit on the bus without exceeding the weight limit of 1000 kg. 

### Solution

```sql
        with cte1 as (
        select person_id, person_name, weight,  
            SUM(weight) OVER (ORDER BY turn ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS rolling_weight
        FROM 
            Queue)
        select person_name from cte1 where rolling_weight <= 1000 order by rolling_weight desc limit 1
```

### Concepts

The query uses a `WINDOW` function to find sum of weight as rolling_weight and `FILTER` based on given condition