=======================================================
### 1321. Restaurant Growth (https://leetcode.com/problems/movie-rating/description/)
=======================================================

### Table Schema

#### Table: Customer

| Column Name   | Type    |
|---------------|---------|
| customer_id   | int     |
| name          | varchar |
| visited_on    | date    |
| amount        | int     |

### Question
 
Compute the moving average of how much the customer paid in a seven days window (i.e., current day + 6 days before). average_amount should be rounded to two decimal places.

### Solution

```sql
WITH cte1 AS (
    SELECT 
        visited_on, 
        SUM(amount) AS sum_amount
    FROM 
        Customer
    GROUP BY 
        visited_on
    ORDER BY 
        visited_on
)

SELECT 
    visited_on,
    
    -- 7-day rolling sum ending on current day
    SUM(sum_amount) OVER (
        ORDER BY visited_on 
        ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
    ) AS amount,
    
    -- 7-day rolling average ending on current day (rounded to 2 decimals)
    ROUND(AVG(sum_amount) OVER (
        ORDER BY visited_on 
        ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
    ), 2) AS average_amount

FROM 
    cte1

-- Skip the first 6 days since there isn't a full 7-day window yet
ORDER BY 
    visited_on
OFFSET 6

```

### Concepts

This query uses `ROLLING WINDOW SUM, AVG` to find rolling average amount paid by customer