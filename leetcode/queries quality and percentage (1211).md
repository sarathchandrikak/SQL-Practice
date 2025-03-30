=======================================================
### 1211. Queries Quality and Percentage (https://leetcode.com/problems/queries-quality-and-percentage/description)
=======================================================

### Table Schema

#### Table: Queries


| Column Name | Type    |
|-------------|---------|
| query_name  | varchar |
| result      | varchar |
| position    | int     |
| rating      | int     |


### Question

We define query quality as:

The average of the ratio between query rating and its position.

We also define poor query percentage as:

The percentage of all queries with rating less than 3.

Write a solution to find each query_name, the quality and poor_query_percentage.


### Solution

```sql
    with cte1 as (
    select query_name, avg(rating/position) as quality, count(query_name) as tc
    from queries group by query_name),

    cte2 as (
        select query_name, 
        COUNT(CASE WHEN rating < 3 THEN 1 END) AS pq
        from Queries
        group by query_name
    )

    select ct1.query_name, round(ct1.quality,2) as quality, round( (ct2.pq/ct1.tc) * 100, 2) as poor_query_percentage from cte1 ct1 inner join cte2 ct2 on ct1.query_name = ct2.query_name group by ct1.query_name order by ct1.query_name
```

### Concepts

The query uses concepts of `MULTIPLE CTEs` and `JOIN` and to find required columns, poor_query_percentage and query_quality
