=======================================================
### 602. Friend Requests II: Who Has the Most Friends (https://leetcode.com/problems/friend-requests-ii-who-has-the-most-friends/description/)
=======================================================

### Table Schema

#### Table: RequestAccepted

| Column Name    | Type    |
|----------------|---------|
| requester_id   | int     |
| accepter_id    | int     |
| accept_date    | date    |

### Question

Write a solution to find the people who have the most friends and the most friends number.

### Solution

```sql
        WITH cte1 AS (
    SELECT requester_id AS id FROM RequestAccepted
    UNION ALL
    SELECT accepter_id AS id FROM RequestAccepted
    )

        SELECT 
            id, 
            COUNT(id) AS num
        FROM 
            cte1
        GROUP BY 
            id
        ORDER BY 
            num DESC
        LIMIT 1;

```

### Concepts

This query combines requester_id, accepter_id into id column and perform count on top of the id column