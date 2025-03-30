=======================================================
### 577. Confirmation Rate (https://leetcode.com/problems/confirmation-rate/description/)
=======================================================


### Table Schema

#### Table: Signups


-----------------------------
| Column Name    | Type     |
-----------------------------
| user_id        | int      |
| time_stamp     | datetime |
-----------------------------
 

#### Table: Confirmations

-----------------------------
| Column Name    | Type     |
-----------------------------
| user_id        | int      |
| time_stamp     | datetime |
| action         | ENUM     |
-----------------------------

### Question

Write a solution to find the confirmation rate of each user.

### Solution

```sql
    WITH cte1 AS (
    SELECT 
        s.user_id, 
        COUNT(CASE WHEN c.action = 'confirmed' THEN 1 END) AS conf_count,
        COUNT(CASE WHEN c.action != 'confirmed' OR c.action != "timeout" THEN 1 END) AS not_confirmed_count
    FROM Signups s
    LEFT JOIN Confirmations c ON s.user_id = c.user_id
    GROUP BY s.user_id
    )
    ,
    cte2 as (
        select s.user_id, count(*) as total_count from Signups s left join Confirmations c on s.user_id = c.user_id group by s.user_id  
    )

    select ct1.user_id, round(ct1.conf_count/ct2.total_count, 2)  as confirmation_rate from cte1 ct1 left join cte2 ct2 on ct1.user_id = ct2.user_id order by confirmation_rate
```

### Concepts

The query uses a `MULTIPLE CTEs` to calculate non_confirmed_count, total_count and `JOIN` to calculate confirmation_rate
