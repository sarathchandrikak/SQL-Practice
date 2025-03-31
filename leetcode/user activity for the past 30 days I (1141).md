=======================================================
### 1141. User Activity for the Past 30 Days I (https://leetcode.com/problems/user-activity-for-the-past-30-days-i)
=======================================================

### Table Schema

#### Table: Activity

| Column Name   | Type    |
|---------------|---------|
| user_id       | int     |
| session_id    | int     |
| activity_date | date    |
| activity_type | enum    |

### Question

Write a solution to find the daily active user count for a period of 30 days ending 2019-07-27 inclusively. A user was active on someday if they made at least one activity on that day.

### Solution

```sql

    select activity_date as day, 
           count(distinct user_id) as active_users 
           from Activity 
           where activity_date > '2019-06-27' and activity_date <= '2019-07-27' 
           group by activity_date
```

### Concepts

The query uses concept of `COUNT FUNCTION` to find daily active user count based on filter condition
