=======================================================
### 1978. Exchange Seats (https://leetcode.com/problems/exchange-seats/description/)
=======================================================

### Table Schema

#### Table: Seat

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| student     | varchar |

### Question

Write a solution to swap the seat id of every two consecutive students. If the number of students is odd, the id of the last student is not swapped.

### Solution

```sql
        SELECT(
        CASE WHEN id % 2 = 1 and  id = (select max(id) from Seat) THEN id
        WHEN id % 2 = 1 THEN id + 1
        WHEN id % 2 = 0 THEN id - 1
        END ) AS id, student 
        FROM Seat
        ORDER BY id
```

### Concepts

This query swaps adjacent students by ID in pairs, except the last student if the total number of rows is odd (they stay in place)