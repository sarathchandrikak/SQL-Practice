=======================================================
### 197. Rising Temperature (https://leetcode.com/problems/rising-temperature/description/)
=======================================================

### Table Schema

#### Table: Customer

| Column Name   | Type    |
|---------------|---------|
| id            | int     |
| recordDate    | date    |
| temperature   | int     |


### Question

Write a solution to find all dates' id with higher temperatures compared to its previous dates (yesterday).


### Solution

```sql
    with cte1 as (
    select *, LAG(temperature) OVER(order by recordDate) as prev_temp, LAG(recordDate) Over(order by recordDate) as prev_date from Weather)
    select id from cte1 where temperature > prev_temp and Datediff(recordDate, prev_date) = 1
```

### Concepts

The query is constructed using `CTE`, `WIDNOW` functions and `FILTER` operation based on `DATEDIFF` function