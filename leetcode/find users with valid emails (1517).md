=======================================================
### 1517. Find users with valid emails (https://leetcode.com/problems/find-users-with-valid-e-mails/description/)
=======================================================

### Table Schema

#### Table: Users

| Column Name   | Type    |
|---------------|---------|
| user_id       | int     |
| name          | varchar |
| mail          | varchar |

### Question

Write a solution to find the users who have valid emails.

A valid e-mail has a prefix name and a domain where:

The prefix name is a string that may contain letters (upper or lower case), digits, underscore '_', period '.', and/or dash '-'. The prefix name must start with a letter.
The domain is '@leetcode.com'.

### Solution

```sql
    SELECT *
    FROM Users
    WHERE mail ~ '^[a-zA-Z]+[a-zA-Z0-9_.-]*@leetcode\.com$'
```

### Concepts

The query is achieved by writing a `REGULAR EXPRESSION` to satisfy the desired conditions of a email id