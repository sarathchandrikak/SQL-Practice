=======================================================
### 1729. Find followers count (https://leetcode.com/problems/find-followers-count)
=======================================================

### Table Schema

#### Table: Followers

| Column Name | Type |
|-------------|------|
| user_id     | int  |
| follower_id | int  |


### Question

Write a solution that will, for each user, return the number of followers.

### Solution

```sql
    select user_id, count(distinct follower_id) as followers_count from Followers group by user_id
```

### Concepts

The query uses concept of basic `COUNT FUNCTION`
