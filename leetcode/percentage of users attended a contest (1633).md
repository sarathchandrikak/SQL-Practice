=======================================================
### 1633. Percentage of Users attended a contest (https://leetcode.com/problems/percentage-of-users-attended-a-contest/description)
=======================================================

### Table Schema

#### Table: Users

| Column Name | Type    |
|-------------|---------|
| user_id     | int     |
| user_name   | varchar |

#### Table: Register

| Column Name | Type    |
|-------------|---------|
| contest_id  | int     |
| user_id     | int     |

### Question

Write a solution to find the percentage of the users registered in each contest rounded to two decimals.
Return the result table ordered by percentage in descending order. In case of a tie, order it by contest_id in ascending order.

### Solution

```sql
    select 
    r.contest_id, 
    round((count(r.user_id) * 100.0) / (select count(distinct user_id) from users), 2) as percentage
    from register r
    group by r.contest_id
    order by percentage desc, r.contest_id;
```

### Concepts

The query uses concepts of `AGG COUNT FUNCTION` and `PERCENTAGE` to find registered users
