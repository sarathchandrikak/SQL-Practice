=======================================================
### 1193. Monthly Transactions I (https://leetcode.com/problems/monthly-transactions-i/description)
=======================================================

### Table Schema

#### Table: Transactions


| Column Name   | Type    |
|---------------|---------|
| id            | int     |
| country       | varchar |
| state         | enum    |
| amount        | int     |
| trans_date    | date    |

### Question

Write an SQL query to find for each month and country, the number of transactions and their total amount, the number of approved transactions and their total amount.

### Solution

```sql
    SELECT 
    LEFT(trans_date, 7) AS month, 
    country, 
    COUNT(id) AS trans_count, 
    COUNT(CASE WHEN state = 'approved' THEN 1 END) AS approved_count,
    SUM(amount) AS trans_total_amount,
    SUM(CASE WHEN state = 'approved' THEN amount ELSE 0 END) AS approved_total_amount
    FROM Transactions
    GROUP BY LEFT(trans_date, 7), country;
```

### Concepts

The query uses concepts of `CASE STATEMENTS` and `AGG FUNCS` and to total amount of transactions
