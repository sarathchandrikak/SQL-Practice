=======================================================
### 584. Find Customer Referee (https://leetcode.com/problems/find-customer-referee/description/)
=======================================================

### Table Schema

#### Table: Customer


| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| referee_id  | int     |


### Question

Find the names of the customer that are not referred by the customer with id = 2.

### Solution

```sql
    select name from Customer where coalesce(referee_id,'') != 2
```

### Concepts

The query uses a `COALESCE` function on refreree_id column and `FILTER` based on given condition
