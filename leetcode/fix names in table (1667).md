=======================================================
### 1667. Fix Names in a Table (https://leetcode.com/problems/fix-names-in-table/description)
=======================================================

### Table Schema

#### Table: Users

| Column Name  | Type    |
|--------------|---------|
| user_id      | int     |
| name         | varchar |

### Question

Write a solution to fix the names so that only the first character is uppercase and the rest are lowercase.

### Solution

```sql
    SELECT
        u.user_id,
        CONCAT(UPPER(LEFT(u.name, 1)), LOWER(RIGHT(u.name,LENGTH(u.name) -1))) AS name
    FROM    
        Users u
    ORDER BY
        u.user_id
```

### Concepts

The query uses `CONCAT`, `LEFT`, `RIGHT`, `LOWER` and `UPPER` functions to concatenate the string as per upper and lower characters specified 